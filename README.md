# PAMscore
expFile="uniSigGeneExp.txt"     
setwd("D:\\biowolf\\TME\\37.PCAscore")     

#读取输入文件
data=read.table(expFile, header=T, sep="\t", check.names=F, row.names=1)
data=t(data)

#PCA分析
pca=prcomp(data, scale=TRUE)
value=predict(pca)
PAMscore=value[,1]+value[,2]
PAMscore=as.data.frame(PAMscore)
scoreOut=rbind(id=colnames(PAMscore), PAMscore)
write.table(scoreOut, file="PAMscore.txt", sep="\t", quote=F, col.names=F)

---
permalink: /dataviz/
title: "Data viz"
author_profile: true
header:
  overlay_color: "#000"
  overlay_filter: "0.2"
  overlay_image: /images/microbes.jpeg
---

Check out some fun data visualizations I've made using Plotly's libraries.

```{r message=FALSE, warning=FALSE, echo=FALSE, fig.width=6.5,fig.height=5}
library(plotly)
pca = read.table("/Users/ruthschmidt/Dropbox/Work/INRS/Data/NI_experiment/Files/VOC/pca.df.txt", sep="\t", header=T)
pca$Date = as.factor(pca$Date)
pcoa3d <- plot_ly(pca, x = ~x, y = ~y, z = ~z, color = ~Treatment, colors = "Dark2", text = ~Date, mode = "markers", type = "scatter3d",
               marker = list(symbol = ~as.factor(char), symbols = "Date"))
pcoa3d <- pcoa3d %>% layout(scene = list(xaxis = list(title = 'PC1 (37.1%)'),
                                   yaxis = list(title = 'PC2 (13.3%)'),
                                   zaxis = list(title = 'PC3 (5.7%)')))

pcoa3d

```

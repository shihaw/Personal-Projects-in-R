# First-Project-NBA Shot Chart

---
title: 'Project 1: Shot Chart Data'
author: "Austin Shih"
date: '2022-09-27'
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

```{r}
require(tidyverse)

nba <- read_csv('../data/nba_shotchartdetail_2018-19.csv')
glimpse(nba)
nba %>% 
  filter(PLAYER_NAME == 'Kevin Durant') %>%
  select(LOC_X,LOC_Y,SHOT_MADE_FLAG) %>%
  ggplot(aes(x = LOC_X, y = LOC_Y, color = factor(SHOT_MADE_FLAG))) + 
  geom_point(alpha = 0.5) + 
  labs(title = "Kevin Durant Shot Chart", subtitle = "2018-19 Season") + 
  geom_curve(x = -200, y = 0, xend = 200, yend = 0, curvature = -1.2, color = 'black') +
  scale_color_manual(name = 'Make or Miss', 
                     values = c('red', 'green'), 
                     labels = c('Miss', 'Make'))
                     

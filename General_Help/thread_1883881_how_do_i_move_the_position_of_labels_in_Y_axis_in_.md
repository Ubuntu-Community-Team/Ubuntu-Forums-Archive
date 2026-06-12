---
title: "how do i move the position of labels in Y axis in gnuplot"
date: 2011-11-20
forum: General Help
---

### Post by jayanthan on 2011-11-20
when i plot a graph with labels it appears exactly at the top of the point. but i want to move the label corresponding to the data (not the axis label) by, say 1 unit in the y axis so that the label will appear above the data point. so, how do i move these labels?

ps: i want to actually show the data, as i am plotting kind of a potential energy surface so that labels won't appear on the top of the bars.
[IMG]http://i.stack.imgur.com/a36jO.png[/IMG]
how can i move the labels MP, TS(ROT) etc by one unit in the Y axis?

---

### Post by gmargo on 2011-11-20
The 'set label' command has an offset parameter that may help.

I'd be interested to see the data file(s) and gnuplot command line you used to generate that plot.  Someone might be able to make a suggestion.

---

### Post by jayanthan on 2011-11-20
```
5	-0.027	1	MP
7.5	0.8	0	TS(ROT) = ?
10	-0.027	1	MP
12.5	0.126	0	TS(EXCH)
15	0	1	A
17.5	0.854	0	TS(ROT)
20	0	1	A
22.5	20.1	0	TS
25	18	1	TOP(?)
```

then i used plot 'file.dat' u 1:2:3 w xerrorbars, 'file.dat' u 1:2:4 w labels

---

### Post by gmargo on 2011-11-21
Check this out:
[IMG]http://i.imgur.com/1gIBj.png[/IMG]

Here's the **gnuplot** command I used:
```

plot "file.dat" using 1:2:3 notitle with xerrorbars, "file.dat" using 1:2:4 notitle with labels offset character 0,1

```You could also add a font command to smallen the text.

---

### Post by jayanthan on 2011-11-22
thanks a lot.
exactly what i was looking for.
however i did it with xmgrace. it has a gui interface.

---


---
title: "Software for plotting graphs like bootchart"
date: 2011-03-22
forum: General Help
---

### Post by motumboe on 2011-03-22
In order to profile the performance on a program I'm working on, I would like to analyze the behaviour of the various threads. My software would produce a text file that an external software (e.g. gnuplot?) would take as input for generating a chart, like the ones greated by bootchart (see [http://www.bootchart.org/images/bootchart.png](http://www.bootchart.org/images/bootchart.png) ) for boot.

Have you got any suggestions?
Thanks in advance.

---

### Post by motumboe on 2011-03-24
bump :-)

---

### Post by oldfred on 2011-03-24
Have you looked at the code in pybootchartgui.py?

[http://code.google.com/p/pybootchartgui/](http://code.google.com/p/pybootchartgui/)

---

### Post by motumboe on 2011-03-24
I'll give a look to it for sure!:popcorn:
Thank you!

---

### Post by tgalati4 on 2011-03-24
apt-cache search profile

I don't anything about these, but they may be helpful:

q-tools - quick and easy performance analysis tools (ia64, 2.6 kernel only)

qprof - Profiling utilities for Linux
qtiplot - data analysis and scientific plotting

---

### Post by motumboe on 2011-03-25
thank you! I have to check if they provide an efficient way to see threads.

---


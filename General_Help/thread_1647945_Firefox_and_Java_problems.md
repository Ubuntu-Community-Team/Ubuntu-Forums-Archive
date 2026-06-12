---
title: "Firefox and Java problems"
date: 2010-12-18
forum: General Help
---

### Post by leona on 2010-12-18
Hi there

Can anyone help with a website problem.
It works fine with Windows and Firefox (at work)
but not on my machine at home, Ubuntu and Firefox
No point complaining to the site runner, I am sure its a firefox and java issue, but not sure how to solve it.

The site is [http://www.trafficengland.com]("http://www.trafficengland.com") the map will not load and just says 'applet loading' and in the task bar says 'applet started'
It loads for a short time, then goes blank, it even sometimes crashes firefox completely.

Does anyone have any ideas, I need to see the traffic info for today, thank you.

---

### Post by lmarmisa on 2010-12-18
Try to install Sun (now Oracle) Java 6 plugin package. Please, follow these instructions.

Open System -> Administration -> Synaptic Package Manager

Then select Settings -> Repositories -> Other Software and tick [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner. Close.

Reload (maybe you will need to restart Synaptic).

Finally, install the package sun-java6-plugin (and the other packages automatically selected, of course).

---

### Post by leona on 2010-12-18
Thank you, I have followed your instrutions and installed sun java 6 plugin.
But, I am still seeing the same problem :(
[edit]
Arr, I removed the Open Java package, restarted and that seems to have fixed the problem, thank you.

---


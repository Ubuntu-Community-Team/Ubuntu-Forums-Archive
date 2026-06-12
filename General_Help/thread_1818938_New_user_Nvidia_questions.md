---
title: "New user Nvidia questions"
date: 2011-08-05
forum: General Help
---

### Post by hbaird on 2011-08-05
I am leaving Fedora after several years because of the unending Nvidia problems. The updates break the nvidia driver from time to time. Then you must go back to an earlier Kernel to get an X display. Sometimes it takes a while to get all the parts to work together. Is there any thing like kmod in Ubuntu?

---

### Post by pqwoerituytrueiwoq on 2011-08-05
ubuntu will inform you that there is a propriety driver available installing is quick and easy
if you use 10.04 i suggest adding the xswat ppa to the the latest driver
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get install nvidia-current
```i don't know if you need the ppa on 11.04 or not

---

### Post by realzippy on 2011-08-05
Which nvidia card do you use?
Some are not free of trouble also in ubuntu...

---

### Post by hbaird on 2011-08-05
I have a Geforce 9400 GT. The problem is the updates on the Kernel, the akmod and the drivers are not at all in sync and they all have to be together for it to work.

---

### Post by papibe on 2011-08-05
I have a 9500GT in 10.4, and a 310M on 11.4, and both have been working great. If you use the proprietary Nvidia driver provided by Ubuntu (additional drivers), updates go smoothly.

Before that, I felt like having the latest driver would be better, and I installed the driver from the Nvidia site. I was a mess. Every other kernel update, I was greeted by a black screen.

Nevertheless, note that there are very skillful people that can handle the last situation with a little of work. For example, take a look at this guide: [HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573&highlight=nvidia+kernel").

Regards.

---

### Post by realzippy on 2011-08-05
There is no need to install the driver manually or to care about
a kernel update when driver installed by jockey (Hardware-drivers tool).
Your card you should run fine.

---


---
title: "Stuck with Recovery Console and User Defined Session"
date: 2011-05-27
forum: General Help
---

### Post by Selo on 2011-05-27
So i was messing around and i think i've done something very bad. After installing new nvidia driver, GDM did not start so i uninstalled GDM, re-installed it, re-installed nvidia driver etc. and after all i could get the login screen but it only offers two different sessions; Recovery Console and User Defined Session :( How can i bring all of them back ?

---

### Post by wildmanne39 on 2011-05-27
> **Selo said:**
> So i was messing around and i think i've done something very bad. After installing new nvidia driver, GDM did not start so i uninstalled GDM, re-installed it, re-installed nvidia driver etc. and after all i could get the login screen but it only offers two different sessions; Recovery Console and User Defined Session :( How can i bring all of them back ?
Hi, what version of ubuntu are you using? Did you activate the cube or effects? how did you install the nvidia driver, what are the specs of your system?

---

### Post by Selo on 2011-05-28
> **wildmanne39 said:**
> Hi, what version of ubuntu are you using? Did you activate the cube or effects? how did you install the nvidia driver, what are the specs of your system?


I'm running Ubuntu 10.10. I did not active any compiz affects. As for installing Nvidia driver; i downloaded the lastest one and since i was getting some errors i followed this [guide]("http://ubuntuforums.org/printthread.php?t=1467074") After installing the driver everything went fine. Problem occurred when i removed [Ubuntu Audio Dev Team]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa")'s  packages . (If i recall right they were about PulseAudio)

---

### Post by Selo on 2011-05-28
Something weird happened. From Ctrl+Alt+F1 i run aptitude -u and i saw Gnome Desktop Manager (or something like that ) i thought this could be the problem. So i installed it and now my desktop is back but it looks like this;

[IMG]http://tinypic.com/r/el1zjn/7[/IMG][IMG]http://tinypic.com/r/el1zjn/7[/IMG][IMG]http://i56.tinypic.com/el1zjn.png[/IMG]

[SIZE=4]What tha heck is this ?[/SIZE]

---

### Post by wildmanne39 on 2011-05-28
> **Selo said:**
> Something weird happened. From Ctrl+Alt+F1 i run aptitude -u and i saw Gnome Desktop Manager (or something like that ) i thought this could be the problem. So i installed it and now my desktop is back but it looks like this;

[IMG]http://tinypic.com/r/el1zjn/7[/IMG][IMG]http://tinypic.com/r/el1zjn/7[/IMG][IMG]http://i56.tinypic.com/el1zjn.png[/IMG]

[SIZE=4]What tha heck is this ?[/SIZE]
Hi, I do not know for sure what that is.

---

### Post by wildmanne39 on 2011-05-28
> **Selo said:**
> Something weird happened. From Ctrl+Alt+F1 i run aptitude -u and i saw Gnome Desktop Manager (or something like that ) i thought this could be the problem. So i installed it and now my desktop is back but it looks like this;

[IMG]http://tinypic.com/r/el1zjn/7[/IMG][IMG]http://tinypic.com/r/el1zjn/7[/IMG][IMG]http://i56.tinypic.com/el1zjn.png[/IMG]

[SIZE=4]What tha heck is this ?[/SIZE]
Hi, I do not know for sure what that is. If you right click on the panel you can remove it then select to add panel back maybe that will fix it but I do not know for sure.

---

### Post by Selo on 2011-05-29
Things went pretty messy so i just reinstalled Ubunutu 10.10. But thanks for your time wildmanne39 !

---

### Post by eugenevdm on 2012-03-09
I had a very similar problem to this and doing:

> sudo apt-get install gnome-session-fallback sorted me out. Thanks goodness, I have just recovered a couple of hours of my life.

---


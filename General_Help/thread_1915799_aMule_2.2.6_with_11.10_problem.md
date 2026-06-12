---
title: "aMule 2.2.6 with 11.10 problem"
date: 2012-01-26
forum: General Help
---

### Post by ubu492 on 2012-01-26
I am running amule 2.2.6 with 11.10 the computer become amule becomes unresponsive every 30 secs or so. The display screen dims and I am unable to do anything in aMule until the screen comes out of the dimmed mode. almost immediately the dimming starts again. I have checked using the System Monitor and the CPU util is low during these times. I installed amule using the system pkg manager. I suspect that this might be related to my video card which is a Nvidia GeForce 8500gt. I have installed the proprietary drivers but this did not help.
Can anyone offer a solution!

---

### Post by csmth on 2012-02-24
You can type "amule" in your terminal to get error message. The error description can provide a specific cause to your problem.

I think it is unlikely that amule has any problem with your display card. It draws its GUI using wxwidget instead.

I have another problem on amule. My amule crashes intermittently. Users of amule 2.2.6 should get wxwidget of 2.8.12, because it is the required library.

Because wxwidget did not maintained a build for 11.10, I tried distribution for 11.04 and it is fine for me. That is to add these sources:

```
deb http://apt.wxwidgets.org/ natty-wx main
deb-src http://apt.wxwidgets.org/ natty-wx main
```

And also get the key using the command below:

```
curl http://apt.wxwidgets.org/key.asc | sudo apt-key add -
``` 

Download site:
[http://www.wxwidgets.org/downloads/](http://www.wxwidgets.org/downloads/)

Download for ubuntu: instructions:
[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

---


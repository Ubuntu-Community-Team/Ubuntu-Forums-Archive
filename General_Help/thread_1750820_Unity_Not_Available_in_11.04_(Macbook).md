---
title: "Unity Not Available in 11.04 (Macbook)"
date: 2011-05-05
forum: General Help
---

### Post by maestropaolo on 2011-05-05
Hi all,

I am new to using Ubuntu as an OS so please pardon in advance my ignorance.

I installed 11.04 64-bit as a partition on my Macbook Pro. This macbook is only a year old, so I think the hardware is okay for Unity. For some reason though, I have Gnome 2.32.1 as my desktop. Upon login, Unity is not one of the options at the bottom of the screen.

I don't see Unity as an option in System Settings/Login Screen either. So I'm wondering -- is Unity not made for running on a macbook? I did a google search and didn't find much information. If it is possible to run on a macbook, how do I enable it as an option? 

I have 64-bit Ubuntu 11.04 installed, but I am not sure if this has any bearing on my problem.

Also, I went to synaptic to look for unity, and apparently it is already installed. So my question is -- how do I make Unity work in my Ubuntu installation?

Thank you,

Paul

---

### Post by spikoley on 2011-05-06
Do you know what type of video card you are using?

If not, post the results of:
```
lspci
```

This might be related to a [bug in jockey]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  Check under System> Administration> Additional Drivers for an error at the bottom.

---

### Post by maestropaolo on 2011-05-07
> **spikoley said:**
> Do you know what type of video card you are using?

If not, post the results of:
```
lspci
```

This might be related to a [bug in jockey]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  Check under System> Administration> Additional Drivers for an error at the bottom.

Hey I installed the drivers and now Unity is my default -- I will test it out and see how it goes. Thanks very much!!

edited to add: the solution was to install the nvidia drivers as spikoley suggested above (Check under System> Administration> Additional Drivers). I then restarted and Unity is my default.

---


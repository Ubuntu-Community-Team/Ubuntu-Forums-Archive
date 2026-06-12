---
title: "Startup applications and usb wireless adaptor problems"
date: 2011-01-04
forum: General Help
---

### Post by josh_kwl on 2011-01-04
Hi, im new to ubuntu and linux, i got reccomended it by a friend of mine as it was my first time building a pc and didnt want to be tied down to microsofts way of things. Anyway, its been going great and im loving ubuntu, except there are a few problems.

Firstly I added skype to my startup applications (usr/bin/skype) and now everytime i boot a get 3 or 4 of them pop up aswell as my music folder.

My second problem is my usb wireless adaptor ( Netgear Wn111v2 ) keeps dropping out frequently.

Im running ubuntu 10.10 64bbit if this helps.

Help would be appreciated guys :)

---

### Post by Bucky Ball on 2011-01-04
Skype third party, little unpredictable. There could be a cure though. Someone else may chirp in with a fix for that.

Odd with the wireless card. Have you plugged an ethernet cable? Gone for all updates? Checked System->Administration->Additional Drivers?

I would perhaps unplug the Netgear USB adapter, get online with an ethernet cable, plug it back in and see what gives. You could open a terminal (Applications-Accessories->Terminal) and type this:

```
lspci
```

Near the bottom somewhere (generally) look for the line that says 'Network Controller' and just post that line here.

For your first taste, you may have been better off trying 10.04 LTS (long term support). Has a year more support than 10.10 and a little more stable. ;)

---

### Post by josh_kwl on 2011-01-04
Terminal comes back with this :

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

---

### Post by Bucky Ball on 2011-01-04
Should work out of the box. Plug in an ethernet cable if you can.

There is a problem with the latest 10.10 kernel on some machines. Could you confirm if you are using this kernel? It will be on the list when you boot your machine:

2.6.35-24

If so there is currently a bug report. I will try and find you the link if this is the case.

As mentioned, 10.04 might be the better option. But if you are looking to dive straight in and spend some time learning in the deep end and tweaking, 10.10 it is!

If not, try 10.04 before you get too involved. Easy to upgrade but not so easy to downgrade without a full install if you can't get things working . ;)

---

### Post by josh_kwl on 2011-01-04
Thanks, and i dont think i can get an ethernet cable in, as my computer is upstairs and the hub is downstairs :/ will post back to you what kernal i am on

---

### Post by josh_kwl on 2011-01-04
yes i am on kernel 2.6.35-24 as it says it on system monitor then the system tab, although i have no idea what a kernel is.

---

### Post by Dans564 on 2011-01-04
the kernel is the base of the os that points the os to different parts of hardware in your computer, at least that is my understanding of it.  Anyways if you are having the wireless problem for -24 here is a thread claiming to have a fix [http://ubuntuforums.org/showthread.php?p=10283175#post10283175](http://ubuntuforums.org/showthread.php?p=10283175#post10283175)

---

### Post by Bucky Ball on 2011-01-04
> **Dans564 said:**
> the kernel is the base of the os that points the os to different parts of hardware in your computer, at least that is my understanding of it.  Anyways if you are having the wireless problem for -24 here is a thread claiming to have a fix [http://ubuntuforums.org/showthread.php?p=10283175#post10283175](http://ubuntuforums.org/showthread.php?p=10283175#post10283175)

A workaround at best and does not solve the problem with the kernel. Worth a shot but might be left with the inferior driver/firmware for your card.

---


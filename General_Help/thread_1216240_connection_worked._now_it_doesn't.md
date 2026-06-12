---
title: "connection worked. now it doesn't"
date: 2009-07-18
forum: General Help
---

### Post by horseradish on 2009-07-18
Hi

I installed ubuntu on a windowsXP machine and the router 'just worked' with ubuntu (through an ethernet connection)

My windows xp then became corrupted but the connection still worked with ubuntu

Now my router transformer broke and when I replaced it, my connection no longer worked.

Do you think the connection was still dependent on windows xp settings in some way ?

There is so little for me to go on in ubuntu network settings. Ubuntu still thinks there is no connection. The connection and router definitely work (currently using a laptop and XP)

---

### Post by DeMus on 2009-07-18
> **horseradish said:**
> Hi

I installed ubuntu on a windowsXP machine and the router 'just worked' with ubuntu (through an ethernet connection)

My windows xp then became corrupted but the connection still worked with ubuntu

Now my router transformer broke and when I replaced it, my connection no longer worked.

Do you think the connection was still dependent on windows xp settings in some way ?

There is so little for me to go on in ubuntu network settings. Ubuntu still thinks there is no connection. The connection and router definitely work (currently using a laptop and XP)

This router, does it have multiple connections for an ethernet cable? If so, are you using another one with your Windows XP machine? Try switching the cables and see what happens then. Could be, one port of your router is damaged.

---

### Post by horseradish on 2009-07-18
Thanks for the reply. It works from the same port with my xp laptop, so that seems ok.

I also meant to say my ubuntu boots from wubi (?), but I can no longer access windows (corrupted).  

The router needs no username/password etc. Should work straight away (on ubuntu via ethernet)

---

### Post by DeMus on 2009-07-18
> **horseradish said:**
> Thanks for the reply. It works from the same port with my xp laptop, so that seems ok.

I also meant to say my ubuntu boots from wubi (?), but I can no longer access windows (corrupted).  

The router needs no username/password etc. Should work straight away (on ubuntu via ethernet)

Sorry, I have no experience with Wubi. I do think it is a bad way of installing Ubuntu, since you depend on the Windows system. Now this has crashed (what else is new?) and you stuck with a non working Ubuntu.
Since you need to re-install Windows anyway do this:

Install Windows from the CD and during install delete all partitions. Then make a partition (C:\) with a size of 20GB.
Then boot into Windows and make a second partition (D:\). Depend the size on the size of your harddisk, but make sure you let so much free space to hold Ubuntu.
Then boot from the Ubuntu CD and install it using the free space on your harddisk.
When you boot your computer you have two OS's next to each other and in a menu (GRUB) you can choose which one to start. This way Ubuntu is independent from Windows.

---

### Post by horseradish on 2009-07-18
the ubuntu is still working. just the connection that isn't.

Im not sure the difference bewteen wubi and a full ubuntu install but I get to choose from a OS menu at boot up

---


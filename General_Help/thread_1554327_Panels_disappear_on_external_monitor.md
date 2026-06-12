---
title: "Panels disappear on external monitor"
date: 2010-08-16
forum: General Help
---

### Post by ryu kun on 2010-08-16
Hi!

I have Asus eee PC 1000HE with Ubuntu 10.04. Almost always I use my eee PC with 19" LG external monitor.

When external monitor is connected, top and bottom panels disappear every time Ubuntu starts. To bring panels back I open my eee PC's lid, press Fn+F8 for 4 times, then panels appear again.

This also happens every time I log out or every time screen saver blanks the screen. So it is very annoying. :mad:

I had the same issue with netbook remix version, thus I've tried desktop edition but it did not help.

I'd really appreciate any help or idea to solve this issue.

Thanks a lot in advance.

---

### Post by ryu kun on 2010-08-17
If somehow I could make "crt only" setting survive Ubuntu restarts or screen savers perhaps I could solve this annoying issue. But I don't know how to do it.

---

### Post by coffee001 on 2010-08-17
> **ryu kun said:**
> Hi!

I have Asus eee PC 1000HE with Ubuntu 10.04. Almost always I use my eee PC with 19" LG external monitor.

When external monitor is connected, top and bottom panels disappear every time Ubuntu starts. To bring panels back I open my eee PC's lid, press Fn+F8 for 4 times, then panels appear again.

This also happens every time I log out or every time screen saver blanks the screen. So it is very annoying. :mad:

I had the same issue with netbook remix version, thus I've tried desktop edition but it did not help.

I'd really appreciate any help or idea to solve this issue.

Thanks a lot in advance.

I've been having the exact same issues ever since moving from Karmic to Lucid (also have an ASUS EEEPC 1000HE hooked up to an LG screen). Another bug that goes along with the one described is that visual effects cannot be switched on. The only solution I have found is to revert to kernel 2.6.31-20, where both these things work as expected (panels are visible, external screen remains primary after sleep, visual effects can be switched on). The 2.6.32 kernel generally doesn't seem to work. :-(

---

### Post by Vela2 on 2010-08-21
Hi,
I don't have a solution, just the same problem. I have an Acer-TravelMate 8371 runnig Ubuntu 10.04 with Kernel 2.6.32-24-generic. Plugged in is a 19''TFT monitor (Hanns).
I'll try switching to the other kernel.

I hope they'll fix it soon.

---

### Post by Vela2 on 2010-08-22
Hi again,
I found this [http://ubuntuforums.org/showthread.php?t=1352688](http://ubuntuforums.org/showthread.php?t=1352688) in the Ubuntu-Netbook-Reemix Section. It's the same problem, not really a solution there.
Until now I couldn't boot with the older kernel.

And then I found this: [https://bugs.launchpad.net/gnome-control-center/+bug/351427](https://bugs.launchpad.net/gnome-control-center/+bug/351427)
So the problem is the resolution, the panels are there, but not visible. 
 Running "xrandr -s 0" brings the panels back. Seems that you have to run it at least at the beginning of each session. Since in my case at the beginning of the session the panels are there, but disappear after a while (so far I dont't know when) I might have to run it more often.

Hope that helps someone, without beeing a really nice solution.

---

### Post by ryu kun on 2010-08-26
Thank you for your replies, they are helpful. 

I don't know how to revert to an older kernel. I have made some research but I could not find it. 

"xrandr -s 0" command really brings the panels back, but I wish we could solve this issue permanently as panels can disappear again from time to time and also applet icons on the panel are mixed up each time, which make this issue more annoying.

I think many people uses external monitor. So this bug of Gnome should have high priority.

Upon this problem I have tried some other Linux distributions recently which uses KDE desktop. They do not have any problem with external monitor at all.

I will try Xubuntu as soon as its download completes.

Any of you tried Ubuntu 10.10 beta? If yes, does it have this problem?

> **Vela2 said:**
> Hi again,
I found this [http://ubuntuforums.org/showthread.php?t=1352688](http://ubuntuforums.org/showthread.php?t=1352688) in the Ubuntu-Netbook-Reemix Section. It's the same problem, not really a solution there.
Until now I couldn't boot with the older kernel.

And then I found this: [https://bugs.launchpad.net/gnome-control-center/+bug/351427](https://bugs.launchpad.net/gnome-control-center/+bug/351427)
So the problem is the resolution, the panels are there, but not visible. 
 Running "xrandr -s 0" brings the panels back. Seems that you have to run it at least at the beginning of each session. Since in my case at the beginning of the session the panels are there, but disappear after a while (so far I dont't know when) I might have to run it more often.

Hope that helps someone, without beeing a really nice solution.

---

### Post by coffee001 on 2010-09-23
Just to reiterate: the problem goes along with the inability to switch on desktop effects. So while using the command as described above will bring back the panel, that still won't resolve the effects issue. My guess is it's somehow related to the eeepc's graphics card and compiz...

---

### Post by ryu kun on 2010-09-24
> **coffee001 said:**
> Just to reiterate: the problem goes along with the inability to switch on desktop effects. So while using the command as described above will bring back the panel, that still won't resolve the effects issue. My guess is it's somehow related to the eeepc's graphics card and compiz...

I disagree because I had this problem while compiz was disabled and Intel graphic chipset is compatible with Linux in most cases. I would guess that problem's cause lies on somewhere else. My hopes are now for 10.10.

---


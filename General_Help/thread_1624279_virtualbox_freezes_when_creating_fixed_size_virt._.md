---
title: "virtualbox freezes when creating fixed size virt. disk"
date: 2010-11-17
forum: General Help
---

### Post by oospill on 2010-11-17
when I try to make a 100MB fixed-size virtual disk, it werks.  when I try to make one that is 5+GB, it shows the completion bar, but it stays at 0% and freezes.  hitting 'cancel' doesn't even work.

anyone have any ideas? much thanx!!

---

### Post by dcstar on 2010-11-17
> **oospill said:**
> when I try to make a 100MB fixed-size virtual disk, it werks.  when I try to make one that is 5+GB, it shows the completion bar, but it stays at 0% and freezes.  hitting 'cancel' doesn't even work.

anyone have any ideas? much thanx!!

What do they say in the Virtualization forum?

---

### Post by junkboxy on 2011-01-03
> **oospill said:**
> when I try to make a 100MB fixed-size virtual disk, it werks. when I try to make one that is 5+GB, it shows the completion bar, but it stays at 0% and freezes. hitting 'cancel' doesn't even work.
 
anyone have any ideas? much thanx!!
 
No, but Yeah I get the same on a new (today) Lucid Server install on a PowerEdge 2900 box. The VirtualBox (4.0 current) virt disk creation freezes VirtualBox and eventually cripples the OS itself. Hard shutdown time!
 
i'm only making a 15GB fixed disk. Didn't try a lower size. 
 
I was so stoked at how flawless the server install went and the subsequent ubuntu-desktop minimal install went. :mad:
 
 
 
 
[I Forgot my original login hence 1 post, Welcome back me, meet the real me.]

---

### Post by junkboxy on 2011-01-04
For posterity, 
Traced this back to a bad DKMS install. I dunno what happened to the original, but reinstalling the DKMS package and rerunning "sudo /etc/init.d/vboxdrv setup"  fixed the issue. 
I had obviously done that on the original install, and didn't get errors from vboxdrv setup. Who knows. Now VB creates the disks in it's usual slow pace but doesn't freeze the app or the OS.

---

### Post by Habitual on 2011-01-04
Well, glad you [SOLVED] it!

Please edit post subject to reflect [SOLVED] if it is [SOLVED].

Get it? :)

---

### Post by junkboxy on 2011-01-04
> **Habitual said:**
> Get it? :)
 
Yeah, Yeah...I know the rap. I'm not OP   :P

---


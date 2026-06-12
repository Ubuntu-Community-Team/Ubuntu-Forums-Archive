---
title: "ubuntu 10.04 inside windows ?"
date: 2010-07-01
forum: General Help
---

### Post by oly on 2010-07-01
Can anyone direct me at any version of linux that lets me run 10.04 inside linux, some thing using colinux i have found andlinux but the version of ubuntu is a lot older, can i apt upgrade to the latest one using a system like this ??

Are there any alternatives, i am aware of virtualisation but prefer a much more integrated experience.

Any suggestions ?

---

### Post by Tumex on 2010-07-01
Wubi -
```
http://wubi-installer.org/index.php
```

---

### Post by laithbsoul on 2010-07-01
I could be wrong but isn't wubi visualization correct me if i'm wrong i would say just use virtual box

---

### Post by Admiral Yi on 2010-07-01
Wubis not virtualisation. And as far as I know, the disks come with wubi on them (or at least they did up to 9.04, not sure about later). Just pop the disk in the drive on windows and a message should pop up asking if you want to install with wubi.

---

### Post by laithbsoul on 2010-07-01
ya but isn't it a visualization like the installation is of a proprietary visualizer custom built for it again i'm not entirely sure

---

### Post by celldweller1591 on 2010-07-01
>  				 				**ubuntu 10.04 inside windows ?** 			
 			 			 		   		 		 		Can anyone  direct me at any version of linux that lets me run** 10.04 inside linux** Confusing !!!  What you want to ask ?? 
If you are looking for integrated linux in windows, go for para virtualisation in KVM/Virtual box or use Unity feature of VMware. Else install it dedicated using Wubi.

---

### Post by celldweller1591 on 2010-07-01
>  				 				**ubuntu 10.04 inside windows ?** 			
 			 			 		   		 		 		Can anyone  direct me at any version of linux that lets me run** 10.04 inside linux** Confusing !!!  What you want to ask ?? 
If you are looking for integrated linux in windows, go for para virtualisation in KVM/Virtual box or use Unity feature of VMware. Else install it dedicated using Wubi.

---

### Post by Mark Phelps on 2010-07-01
A Wubi install does NOT end up with a setup that runs Ubuntu INSIDE MS Windows.  When you boot to Ubuntu, you're still running it in native form.  You're just using a filesystem that is installed on an NTFS-formatted partition.  It's not virtualization.

---

### Post by bodhi.zazen on 2010-07-01
You really can not run two operating systems at the same time, the closest you can come is Virtualization.

Colinux is probably the closest to what you want. It takes some time to set up, and is not seamless.

An alternate would be Cygwin. Cygwin allows you to run bash and some LInux applications in windows (I had KDE running in Windows on Cygwin at one point several years ago).

You can go the other way, install Ubuntu and run Windows in Virtualbox:

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by steveneddy on 2010-07-01
Wubi is bad. Forget wubi.

You really want to look at VirtualBox.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Some YouTube videos:

[http://www.youtube.com/results?search_query=virtualbox+ubuntu&aq=1sx](http://www.youtube.com/results?search_query=virtualbox+ubuntu&aq=1sx)

---

### Post by oly on 2010-07-05
I did mean windows, wubi as far as i am aware lets you run linux inside windows but seperately ie you have to reboot between the two.

colinux does seem like my best option but all i can find is portable ubuntu and it seems a bit dead / does not work at all on this xp machine.

perhaps i can use colinux and roll my own is there any information on this ?

my goal is basically to have applications i am used to available in windows, virtualbox is an option i know but its not as integrated as portable ubuntu used to be.

Are there any other projects other than portable ubuntu ?

---

### Post by bodhi.zazen on 2010-07-05
colinux is probably your best bet. You certainly can "roll your own" distro in colinux, it takes some effort.

If colinux is too much work, you can get the same effect with Virtualbox. SSH into your guest, forward X apps, and run xming on Windows (which is basically what colinux is doing).

Colinux uses less resources but takes more work.

Alternates would be VMWare.

---


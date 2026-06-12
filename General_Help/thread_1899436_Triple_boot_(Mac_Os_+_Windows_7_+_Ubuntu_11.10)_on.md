---
title: "Triple boot (Mac Os + Windows 7 + Ubuntu 11.10) on MacBook"
date: 2011-12-23
forum: General Help
---

### Post by altropianeta on 2011-12-23
Hello everyone! After watching some videos on the web I decided to install three operating systems on my MacBook.

So I divided the hard disk into two partitions, installed Mac OS in partition no 1, and Windows 7 in partition no 2. Then I installed rEFIt on MacOS ([http://refit.sourceforge.net/](http://refit.sourceforge.net/)), a boot menu that gives the opportunity to choose which operating system to use when you turn on the computer. And so far, so good. Windows 7 works perfectly, thanks to the drivers provided by Boot Camp.

Then I installed Linux in Windows 7 partition, which has been splitted into three parts: one part is dedicated to Windows 7, one to Ubuntu 11.10, and one to swap.

The three operating systems'  installation seemed to be successful, but after a while I noticed some problems.

Now... When I turn on my computer I get this screen:

[IMG]http://refit.sourceforge.net/img/screen2.png[/IMG]

However, once I installed Ubuntu I lost the opportunity to access the Windows partition through rEFIt. In fact, if I choose Windows, I get the Ubuntu Grub with its minimal menu where you can choose which operating system to run. And here, if I choose Windows 7 option, it does start and work.

Apparently, all this happened because Ubuntu has installed its boot manager and has kind of messed up somethig in Windows boot.

On the Internet I found several ways to solve this problem but really incomplete and badly explained. So I need the proper procedure to restore normal access to Windows via rEFIt after installing Ubuntu. Can anyone give me any suggestion, please?

Thanks to anyone who tries to help me, and please remember that I'm not an expert.

;)

---

### Post by altropianeta on 2011-12-24
Up

---

### Post by West201 on 2011-12-26
Can you post your gurb.config file ? 

It's located in /boot/grub/grub.config

You use an Ubuntu live cd to boot.

---

### Post by 2F4U on 2011-12-26
Did you follow the instruction here

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

and sync the partitions with the rEFit partitioning tool?

---


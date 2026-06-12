---
title: "Selecting Win7 In GRUB forces restart"
date: 2009-11-19
forum: General Help
---

### Post by sqeeeksLongboards on 2009-11-19
I've tried everything now...
Here's what i've tried so far:
-Installing Ubuntu first, then Win7 on another drive, then editing grub. Selecting windows = instant reset. 
-Installed Win7 first, then Ubuntu, selecting windows = instant reset
-Installed Win7 on one drive, Ubutnu on the other, boot to PLoP, selecting win7=yaay, selecting GRUB=instant reset
I've tried some other stuff too, but you get the idea... how the heck do i make grub correctly boot windows 7?
Sorry to bother... I'd just use Ubuntu but half my stuff for school only works in windows, and WINE won't work with them either.

I should clarify, this is with _any_ hard drive, not just the two that are in here, which are:
sda: 200gb maxtor
sdb: 40gb WD sata
(crappy drives i know, but heck, i got them for free...)

---

### Post by oldfred on 2009-11-20
Do you have anything installed now. It is hard to tell you what your problem is without knowing your exact configuration. It is always better to install windows first then Ubuntu. What version of Ubuntu?

Have you followed these guides?
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by drseuk on 2009-11-20
> **oldfred said:**
> Do you have anything installed now. It is hard to tell you what your problem is without knowing your exact configuration. It is always better to install windows first then Ubuntu. What version of Ubuntu?

Have you followed these guides?
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/]("http://members.iinet.net/%7Eherman546/")
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Agree totally (since MS Windows tends to ignore the presence of any other OS and simply wipes it - unlike Ubuntu which gives you a choice as to what you wish to do - i.e., keep any existing OS or overwrite it).

---

### Post by sqeeeksLongboards on 2009-11-20
I've followed those guides, yes. And yup, i've tried installing Win7 first, I agree that it's easier. I'm thinking it's hardware related, because dual booting works fine on my laptop. Also, PLoP doesn't work either - I installed each operating system separately, unplugging the windows drive when i installed ubuntu, etc... PLoP can boot Win7, but won't boot Ubuntu. However, when I set the BIOS to boot to the Ubuntu drive, it loads grub fine. 
So I finally got it to dual boot, sort of-
-I set the BIOS to boot to the floppy first, then Ubuntu
-Then I told PLoP to automatically boot the Win7 Partition
So now, when the floppy's in, it boots windows, when the floppy's out, it boots Ubuntu.

I think half the problem I was having was that if Ubuntu is on a different drive, GRUB's 30_os-prober script isn't finding Win7 for some reason... I'll figure it out later, or hope that when it gets out of Beta, it works a bit better... 

Thanks for your help.

FYI:
My exact configuration right now:
-Maxtor 200gb IDE
 Partition one, 193000mb, WIN7
 Free Space 1001mb
-WD 40gb SATA
 Partition one, Ubuntu
 Partition two, 2gb swap

I blame my motherboard's HDD controllers, it's a 4 year old Intel board with 5 SATA ports and one IDE, it's always had compatibility issues. Lol dual booting RedHat and Win2k a couple of years ago was... interesting... XD

---


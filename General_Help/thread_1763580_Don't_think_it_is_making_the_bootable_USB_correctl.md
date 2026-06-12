---
title: "Don't think it is making the bootable USB correctly"
date: 2011-05-20
forum: General Help
---

### Post by thoenix on 2011-05-20
My friend showed up on my doorstep last night with a system 32 file missing from his windows-based netbook.  It's an Acer Aspire One 522.  I tried, of course, fixing windows on it, but this is just getting frustrating even with a legit key for windows 7 starter (finding an unaltered iso to use, since Windows doesn't give you a disk... urgh...) and I personally loathe working with windows.  I'm currently torrenting windows just in case nothing else works.  

So now I am attempting to install Ubuntu.

I have followed the instructions for creating a bootable USB, using my partner's Windows7 computer, as found on the [download page.]("http://www.ubuntu.com/download/ubuntu/download")  I do not, however, think that it is creating it properly.  I cannot get the bootable USB to work on any of our computers, or at least, I don't think I can.  The boot order is correct, as verified using a windows repair USB, but it will not load.

Am I missing a step somewhere?  Is there something that I should be doing extra?  Is there an alternate installer that might work better to create the bootable USB?  I'm a bit new at this, but have successfully installed Ubuntu on my partner's laptop awhile back by following the instructions on the download page, so I don't know what I'm doing wrong.

At present, the computers at my disposal to try and do this are: a desktop running Windows 7 64bit, a Macbook Pro running Snow Leopard 10.6.4 and the netbook with no OS.  I also have an Ubuntu laptop running Karmic Koala.

Anyone have any ideas to help?  Please?

---

### Post by linuxinstalledfromhdd on 2011-05-20
Try  burning it to a disc.

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Use that walkthrough.

---

### Post by thoenix on 2011-05-20
The netbook in question doesn't have a disk drive.  It has to be USB.  I don't have a USB CD-Rom drive, either.  If it were that simple, I'd have it on the computer already lol.

---

### Post by bdoe on 2011-05-20
What exactly happens when you try to boot from your USB drive?

If you made your bootable USB with Ubuntu 10.10 or 11.04, and you get some sort of weird error along with a boot> prompt when you try to boot with it, then try typing "live" (without the quotes) at that boot prompt. I had to do this to get my thumbdrive to boot the Linux install ISO I had put on it.

---

### Post by jerrrys on 2011-05-20
may want to give [unetbootin]("http://unetbootin.sourceforge.net/") a try.  if you already have the iso downloaded you need not download again. use manual setting to copy to usb.

---

### Post by thoenix on 2011-05-21
There is no error message.  It just is acting as though it isn't finding a bootable USB--not booting to it, I mean.  Tried unetbootin.  Have tried multiple USBs.  It is simply refusing to create a bootable.  And I don't know why.  I'm following all instructions to a T.  When I create a Windows repair disk, it is booting up correctly as a bootable, so I know that the boot order is correct.

---

### Post by cariboo on 2011-05-21
If you are running a recent version of Ubuntu, anything after 10.04, use the Startup Disk Creator utility

---

### Post by thoenix on 2011-05-22
> **cariboo907 said:**
> If you are running a recent version of Ubuntu, anything after 10.04, use the Startup Disk Creator utility
Sadly, the Ubuntu laptop is running Karmic Koala which was, I think, 9.something.  (the screen is broken so I have to borrow the monitor from the desktop to run it, so I'm not overly into checking)

---

### Post by halibaitor on 2011-05-22
I had the same thing happen to me on a friend's computer that I was trying to install Ubuntu 10.10 on.  What I finally did that made it work was to disable boot entirely from the hard drive.  Then it finally worked.

---


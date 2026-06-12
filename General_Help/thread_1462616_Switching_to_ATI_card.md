---
title: "Switching to ATI card"
date: 2010-04-25
forum: General Help
---

### Post by dpCalbee on 2010-04-25
Hi, I'm having trouble getting X to work after switching from onboard intel video to a 5000 series ATI card. Apparently I need to switch to a MESA or fglrx driver. I did a sudo apt-get install fglrx-driver and it installed but still no X. I'm currently using Karmic. 

I've tried to boot with a live CD which works fine and changed the xorg file manual but that was a mess. 

When I start I get a checking battery state ... done and it stays there forever sometimes and sometimes I can login but without x. Typing startx gives me a long list that says check the xorg website.

I've been looking around for a way to fix this and haven't been able to get it working. Any help would be appreciated as I'm still new to the whole linux thing.

---

### Post by dcstar on 2010-04-26
> **dpCalbee said:**
> Hi, I'm having trouble getting X to work after switching from onboard intel video to a 5000 series ATI card. Apparently I need to switch to a MESA or fglrx driver. I did a sudo apt-get install fglrx-driver and it installed but still no X. I'm currently using Karmic. 

I've tried to boot with a live CD which works fine and changed the xorg file manual but that was a mess. 

When I start I get a checking battery state ... done and it stays there forever sometimes and sometimes I can login but without x. Typing startx gives me a long list that says check the xorg website.

I've been looking around for a way to fix this and haven't been able to get it working. Any help would be appreciated as I'm still new to the whole linux thing.

Boot off the Live CD, mount the drive with Ubuntu on it and see if there is an xorg default/failsafe file.

If there is, rename the existing xorg.conf file and copy this to xorg.conf.

Reboot and reinstall the ATI driver.

---

### Post by dpCalbee on 2010-04-26
I renamed xorg.conf.failsafe to xorg.conf and now after checking battery state done...it says nmdb running and stays there. No longer brings me to a login prompt.

Could it be that the old intel driver is conflicting with it? Would I have to uninstall it and how would I find out what the driver is to uninstall it if I can get to a login screen? I have a feeling it's not using the xorg.conf file in /etc/X11/ if that's possible.

---

### Post by quadproc on 2010-04-26
> **dpCalbee said:**
> Hi, I'm having trouble getting X to work after switching from onboard intel video to a 5000 series ATI card. Apparently I need to switch to a MESA or fglrx driver. I did a sudo apt-get install fglrx-driver and it installed but still no X. I'm currently using Karmic. 

It would help to know the exact model of your ATI card.  The reason for this is that ATI uses the same numbers with differing qualifiers to identify several different cards.

I am running HD4870x2 and have learned the hard way about some of the quirks involved with X windows, the kernel, and the fglrx driver.

It sounds like you have driver trouble.  I don't know which version you obtained from the repository so here is what I suggest: uninstall the existing driver, do something to the name of the xorg.conf file so that X windows can't find it, download an ATI driver file from ATI's web site making sure that the version you get is correct for your Ubuntu version and for the graphics card that you have and put this is a directory of its own, and then manually install the downloaded ATI file.  Do not use the Hardware Drivers utility in Ubuntu as it does not give you control over what it is doing and you could easily get something that doesn't work right.

In the latest versions of Ubuntu, the X windows server will attempt to use the xorg.conf file to set up the graphics system but if it can't find the file then it will look at the hardware and make its best guess for setting things up.  I am not sure what it will do about the fact that you have two graphics systems in the machine; you may have to use an xorg.conf file that has a BusID on the entry for the graphics card that you wish to be the primary card.

When doing the driver install, I suggest this:
```
cd <where_the_downloaded_file_is>
sudo sh <name_of_downloaded_file> --keep --install
```This will leave behind all of the directories and files that the ATI software used so that you can inspect them if you so desire.

It is very important that you remove the old driver before you install the new one.  If vestiges of the old one remain then weird and bizarre problems can occur.

quadproc

---

### Post by dpCalbee on 2010-04-26
Thank you.

It is an HD 5770 and I haven't ever gotten my Karmic to display X since I got the card. So the only Ati driver I got was from sudo apt-get install fglrx-driver when I was able to login.

I will try what you say but manually install the driver. How do I do this from within a DOS-like environment?

btw I am on Windows 7 right now and able to boot to a jaunty live cd

oops you gave me direct instructions on teh install sorry! I'll try it now

---

### Post by dpCalbee on 2010-04-26
Thank you! It works! Haven't seen this screen in awhile.

I wasn't sure I'd ever get ubuntu running with an Ati card. Now sound doesn't work. That's for another day.

If I'm supposed to mark this as solve I'm trying to figure out how to do that now so bear with em.

---

### Post by quadproc on 2010-04-26
> **dpCalbee said:**
> Thank you! It works! Haven't seen this screen in awhile.
Congratulations!> 
I wasn't sure I'd ever get ubuntu running with an Ati card. Now sound doesn't work. That's for another day.Yes, I have seen a lot of comments regarding sound problems in 9.10.  There is a sticky thread at the top of the forum regarding sound issues; if you haven't seen that then it is probably worth a read.> 
If I'm supposed to mark this as solve I'm trying to figure out how to do that now so bear with em.Take a look near the top under Thread Tools.

quadproc

---


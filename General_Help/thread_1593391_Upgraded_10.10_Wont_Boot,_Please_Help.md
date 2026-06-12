---
title: "Upgraded 10.10 Wont Boot, Please Help"
date: 2010-10-11
forum: General Help
---

### Post by ndstate on 2010-10-11
Hello,

I upgraded from 10.04 64bit to 10.10 64bit.  I have a Toshiba Satellite A305-xxxx.  I have ati graphics.

I disabled the fglrx driver for troubleshooting (because 10.10 was ungodly slow).  Upon reboot Ubuntu will not load.  It sits at a black screen right after the Ubuntu loading logo.  I have tried multiple kernels and recovery mode... they all freeze at that black screen.  Also, I tried ctrl-alt-f1 and that also freezes. :confused:

Can someone please help me figure out how I can get Ubuntu back?

Thank you!

---

### Post by ndstate on 2010-10-11
Well I finally figured this out on my own. I will outline the steps I took in case someone else has this issue.

I was finally able to get to the terminal.  To do this at grub I edited the command for startup and added nomodeset to the beginning.  This allowed me to boot into the terminal via recovery mode.

Once there I was able to figure out fglrx was causing all the problems.  I couldnt remove it all with   sudo apt-get remove --purge xorg-driver-fglrx fglrx* ... because some folders had files in the still.  I just renamed them with the mv command.

I re ran purge and cleared out dpkg.

I then renamed /etc/X11/xorg.conf since it was messed up.  I subsequently ran   sudo dpkg-reconfigure xserver-xorg

After this I was able to do the command startx which started the x server without issue... so that fixed that problem.  I was able to get to the gui, but it was messed up.

I removed all fglrx files I could find, including renaming folders that contained files of fglrx (I determined these files by the errors I was getting trying to modify fglrx).  I reinstalled fglrx and apparently this time I got an updated copy.  I installed it and restarted.  Upon restart I used the command sudo aticonfig --initial -f .. rebooted again.

That appears to have fixed all of the graphics issues.  If you need any help with fglrx or anything related to this let me know.

See [https://wiki.ubuntu.com/X/TroubleshootingFglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/TroubleshootingFglrxInteferesWithRadeonDriver) for more info.

---


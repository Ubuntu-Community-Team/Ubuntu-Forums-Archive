---
title: "Triple booted XP, 7, and Ubuntu 9.10. Grub only see's XP and 9.10"
date: 2010-02-12
forum: General Help
---

### Post by gymophett on 2010-02-12
I installed them in this order.
Windows 7
Windows XP
Ubuntu 9.10

When I boot, grub see's XP and Ubuntu 9.10, not 7, although it is there.
I've done some searching on google, and can't really find anything on it. If there is one, will someone point me to it?
Can anyone help?

Thank you.

---

### Post by eriktheblu on 2010-02-12
What happens when you boot to XP?

My understanding is that GRUB chain loads the MS boot loader, from there you should be able to select your Windows distro.

It seems to be common practice with booting multiple versions of Windows to install the older distro first.

---

### Post by gymophett on 2010-02-12
I already had 7 installed before I thought about triple booting. But I'm not able to choose anything after choosing Windows.

---

### Post by Mark Phelps on 2010-02-12
Did you try booting into Win7 after you installed XP? My guess is that, if you had done that, you would have noticed that you couldn't boot into Win7 anymore.  You most probably overwrote the Win7 MBR with the XP MBR -- which is why MS Windows boot defaults to XP now.

And then, you probably overwrote the XP MBR with an Ubuntu MBR (GRUB).

When you were in Win7, did you take the time to create and burn a Win7 Repair CD?  If you had done that, you could now boot using that to repair the Win7 boot loader -- and it would automatically create a menu including both XP and Win7.

But, if you didn't create that CD, don't know how you can boot into Win7 to repair it.

---

### Post by oldfred on 2010-02-12
Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by 0nullun0 on 2010-02-12
If ubuntu 9.10 was a clean install (not an upgrade), you're running grub2. You don't mention whether you've run 'update-grub' under your ubuntu 9.10 install. Among many other things, 'update-grub' detects all installed OSs. My own multiboot install (same as yours, on a netbook) didn't show up properly in the bootloader until I did this. 

Hope this helps ...

0nullun0

---


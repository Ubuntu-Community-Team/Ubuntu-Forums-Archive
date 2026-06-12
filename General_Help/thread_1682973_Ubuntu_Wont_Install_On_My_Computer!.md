---
title: "Ubuntu Wont Install On My Computer!"
date: 2011-02-06
forum: General Help
---

### Post by Josh Workman on 2011-02-06
Ok I recently download Ubuntu 10.10 from there officail website and burned it to a blank disc useing infra recorder like there website suggested. I put the disk in the tray closed in and restarted my computer. Every thing went fine untill the purple ubuntu screen with the loading dots under it. Abount 50 seconds later, a very old school mediveal prompt came up that read;
 
"BusyBox v1.15.3 (Ubuntu 1:1.15.3-1Ubuntu5) built in shell (ash) 
 
Enter 'Help' for a list of built in commands.
 
(initramfs) unable to find a medium containing a live file system."
 
I ran Ubuntu 10.10 on a Sun Virtual Box and everything came up fine asking me if I wanted to Try it out or Install it. But I dont want to install it on the virtual box, I want to install it on my computer. What am I doing wrong? I want to start using Ubuntu ASAP becuse im sick of windows crashing all the time. Please Email me at [EMAIL="joshworkman4@gmail.com"]joshworkman4@gmail.com[/EMAIL] if you have a solution to this!
Ps I know I burned it right because I was successfully able to install it on my unlcles computer.
):P

---

### Post by RJ12 on 2011-02-06
Did you burn the ISO at a slow speed?

---

### Post by Josh Workman on 2011-02-06
I think I burned it on fast speed. Would re burning it on a slow speed fix the problem?

---

### Post by marshag63 on 2011-02-06
If you have a 2 gig flash drive, you can make a bootable USB drive and byass any CD/DVD burning issues.  Unetbootin is the easiest method.

MarshaG.

---

### Post by wandalalakers on 2011-02-08
Try 10.10 and:
Navigate to the GRUB prompt, when starting boot.
Add 'splash all_generic_ide' at the end of line quiet ==>quiet splash all_generic_ide
Ctrl+X to boot edit
or
Try installing the alternative version.
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by Forgotten Path on 2011-02-08
I had a similar problem with an older Ubuntu installer on my wifes old PC - I believe its a video card driver issue, or the LiveCD doesn't have enough RAM to run.  How much RAM does the PC have?
Either way, using the alternative installer would take care of that.

---

### Post by Quackers on 2011-02-08
When booting from the cd, as the first purple screen appears (the one with the little man graphic at the bottom) press any key. Choose language then on the next screen choose the option to check the cd for errors. If it finds an error try burning the image at a slower speed, or check the md5sum of the Ubuntu .iso file that you downloaded.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---


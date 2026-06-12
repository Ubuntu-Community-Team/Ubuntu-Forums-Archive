---
title: "How to modify GRUB to boot into Vista?"
date: 2010-08-24
forum: General Help
---

### Post by cAlpha on 2010-08-24
I've previously had a dual boot Vista/Ubuntu machine that was working fine.  Fast forward, I'm not able to boot into Vista at all and decide to reformat, return to factory settings after which I'll simply reinstall Ubuntu to get my functioning dual-boot back.

I reformat the drive, everything seems to work fine and when I reboot I'm met by the GRUB screen rather then the Vista bootloader screen I expected.  I select the Vista option and rather than starting to boot, seeing the Windows splash and THEN breaking (as it's been doing for a few weeks leading up to my decision to reformat), I'm promptly given a message that it can't find the disk 5252-ACFA... (that Vista was previously on).  

After further inspection, my Ubuntu partition is still in tact and untouched, so I think the 'reformat' simply reformatted the Vista partition not the entire HD as I'd wanted.  

How do I modify GRUB to point to the new correct Vista boot?

---

### Post by JKyleOKC on 2010-08-24
Log into Ubuntu, open a terminal window, and type "sudo update-grub" into it. It will ask for a password; type your login password but don't expect to see any response on the screen. You should see, then, several lines reporting what the program is doing, winding up with a line that says it found Vista (there might be two such lines; my now-gone Vista system showed its loader and also a factory-recovery partition).

When it gets back to the terminal prompt, you can type "sudo reboot now" and it should come up (when you hit left shift during the boot process) with Vista showing on the grub menu...

---

### Post by cAlpha on 2010-08-24
> **JKyleOKC said:**
> Log into Ubuntu, open a terminal window, and type "sudo update-grub" into it. It will ask for a password; type your login password but don't expect to see any response on the screen. You should see, then, several lines reporting what the program is doing, winding up with a line that says it found Vista (there might be two such lines; my now-gone Vista system showed its loader and also a factory-recovery partition).

When it gets back to the terminal prompt, you can type "sudo reboot now" and it should come up (when you hit left shift during the boot process) with Vista showing on the grub menu...

Thanks...it does, indeed, show the Vista loader ("Found Windows Vista (loader) on /dev/sda3") and within GRUB as well--Vista is listed as an option within GRUB, just after selecting it, it doesn't go anywhere.  

I just checked *blkid* and noticed that the UUID for my Vista boot partition is different than when it worked previously--how can I modify GRUB to point to the new UUID/disk?

---

### Post by wilee-nilee on 2010-08-24
At some point it will be helpful to have you post the bootscript in my signature in code tags as described.

It would be nice to see if the the Vista boot setup is correct. If you are using grub2 theoretically it should see Vista, the boot flag may be on a wrong partition as well.

What were looking for is something like this.
sd??: __________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   **/bootmgr /Boot/BCD /Windows/System32/winload.exe**

---

### Post by cAlpha on 2010-08-24
> **JKyleOKC said:**
> Log into Ubuntu, open a terminal window, and type "sudo update-grub" into it. It will ask for a password; type your login password but don't expect to see any response on the screen. You should see, then, several lines reporting what the program is doing, winding up with a line that says it found Vista (there might be two such lines; my now-gone Vista system showed its loader and also a factory-recovery partition).

When it gets back to the terminal prompt, you can type "sudo reboot now" and it should come up (when you hit left shift during the boot process) with Vista showing on the grub menu...

UPDATE:  I updated GRUB this way and after rebooting I was again able to get into Vista, newly reformatted.  Thanks for the help!

---


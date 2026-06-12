---
title: "Grub got messed up on triple-boot system, can't boot anything"
date: 2011-05-10
forum: General Help
---

### Post by rage_311 on 2011-05-10
Hi all,

I'm currently on a work trip with my Asus G72GX laptop for non-work use (I'm posting from my work laptop).  Yesterday, I accidentally booted into my laptop's recovery partition (from the Grub2 bootloader).  Before I realized that that's what was happening, it booted into some kind of recovery program which ended up in an error.  I restarted the laptop and couldn't get into the bootloader anymore.  Now, the only thing that comes up is an error -- "error: unknown filesystem."  Below that, it gives me the "grub rescue>" prompt.  Most of the commands that sites list for grub rescue only return "Unknown command".  ls works and lists all of my partitions: (hd0), (hd0,msdos8), (hd0,msdos7), etc. down to msdos1.  When I "ls (hd0,msdos8)" (etc, etc) it says "error: unknown filesystem."

I then started looking into booting from a Live Ubuntu USB drive.  I've tried 11.04 and 10.04 now and they both do the same thing.  I put them on an 8GB flash drive (only 1 at any given time) using Universal USB Installer and was able to get to the Ubuntu menu (Run Ubuntu from this USB, Install Ubuntu on a Hard Disk, etc.)  If I try either "Run Ubuntu" or "Install Ubuntu", the screen flickers and comes right back to that menu.

BTW, my 3 operating systems are: Windows 7 HP 64-bit, Mythbuntu 10.10 64-bit, and Windows XP 32-bit.  Laptop hardware: Core 2 Duo P8700 2.53GHz, 6GB RAM, Nvidia 8800 GTX video card.  Maybe that helps.

Any help and/or direction?  Thanks in advance...

---

### Post by ManualSparrow on 2011-05-11
Not an expert but had a similar problem here a while ago - [http://ubuntuforums.org/showthread.php?t=1736692](http://ubuntuforums.org/showthread.php?t=1736692)

(Might give you a better idea of what's going on, but probably won't get you all the way unfortunately).

The hard drive diagnostics in the BIOS may also be helpful, if something is wrong there.

---

### Post by wilee-nilee on 2011-05-11
> **ManualSparrow said:**
> Not an expert but had a similar problem here a while ago - [http://ubuntuforums.org/showthread.php?t=1736692](http://ubuntuforums.org/showthread.php?t=1736692)

(Might give you a better idea of what's going on, but probably won't get you all the way unfortunately).

The hard drive diagnostics in the BIOS may also be helpful, if something is wrong there.

No problems like this are ever the same see the #2 post in your own thread, lease be careful.

Thread starter do this, so from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by rage_311 on 2011-05-24
Not necessarily solved, but I did get a workaround.  My issue was that my laptop just wouldn't start Ubuntu from a USB drive, for some reason.  It booted to the menu just fine, but wouldn't boot into the installer or actual OS.  I was finally able to get a hold of some CD-Rs and I was able to burn Ubuntu to a CD from the other laptop and boot from that just fine.  Just thought I'd let you all know how it went.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Was it a live bootable version 11.04 or 10.10 (stable)?

---


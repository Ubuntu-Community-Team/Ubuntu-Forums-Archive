---
title: "Strange problem with computer or Bios"
date: 2012-04-07
forum: General Help
---

### Post by tetri on 2012-04-07
Hello

 Recently I got an old NEC kompyutarche with the following parameters - 2200 processor, 512 MB &#8203;&#8203;RAM, integrated graphics, DVD Rom does not work, floppy drive is broken. Is 20 GB hard drive.
 But I could not install OS in any way.
 In the bios has the option of charging devices, gullies, but can not leave.
 Via [http://live.learnfree.eu/](http://live.learnfree.eu/) trying to install some of its Linux distribution, but nothing happens. I tried to lubuntu, ubuntu and gently, but do not leave. There is an option to boot from flash drive.


 Writes me something like run a boot flash.
 [B]SYSlinux 4.04 CS Copyright 1994-2011 H.Peter
ERROR No configuratipon file found[/B] [B]
No DEfault or UI configuratio directive found![/B] [B]
boot:

[/B][http://picbg.net/img.php?file=8735ad500896337b.JPG](http://picbg.net/img.php?file=8735ad500896337b.JPG)

It can be seen long in the tooth box and monitor the IBM
 DVD Rom constantly lit like rotten receive signals from the bottom.
 Cause I removed the floppy drive and it creates problems.

 there is another option to install the OS then. a USB optical drive. But now I have this available.

 What do I do now. Do it in my shop ... you'll probably want my 60 lev for repair costs as the entire computer ...:confused:

*PS. Sorry for the spelling, but I'm from Bulgaria and write a translation program*

---

### Post by Cheesemill on 2012-04-07
The only methods I can think of installation are:

CD - But your CD drive doesn't work.
USB - Your machine is most likely to old to boot from USB.
Floppy - Use a boot floppy such as PLOP to initiate booting from USB - But your floppy doesn't work.

This leaves you with:
External CD - If you can get hold of an external CD drive then you might be able to boot from this (if your BIOS supports it).
Network - If your laptop supports network boot then you can set up a PXE / TFTP server on another machine and boot over the network.

---

### Post by Cheesehead on 2012-04-07
> **tetri said:**
> 
 Writes me something like run a boot flash.
 [B]SYSlinux 4.04 CS Copyright 1994-2011 H.Peter
ERROR No configuratipon file found[/B] [B]
No DEfault or UI configuratio directive found![/B] [B]


The bootloader is telling you that it is misconfigured. That can be very easy to fix.

See the syslinux documentation at [http://www.syslinux.org/wiki/index.php/SYSLINUX#How_do_I_Configure_SYSLINUX.3F](http://www.syslinux.org/wiki/index.php/SYSLINUX#How_do_I_Configure_SYSLINUX.3F)
Or, just post the text of your syslinux.cfg file here.

---

### Post by tetri on 2012-04-07
ok This file is taken from my flash drive
[U][B]syslinux.cfg
[/B][/U]
 > 
MENU TITLE Lubuntu USB BOOT MENU
DEFAULT vesamenu.c32
PROMPT 0
LABEL live
    menu label ^Start Lubuntu
    kernel /casper/vmlinuz
    append file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash locale=bg_BG --

#PERSISTENCE:LABEL live-persist
#PERSISTENCE:    menu label ^Start Lubuntu (persistent)
#PERSISTENCE:    kernel /casper/vmlinuz
#PERSISTENCE:    append file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash locale=bg_BG --


LABEL live-acpifix
    menu label ^Start Lubuntu (safe mode)
    kernel /casper/vmlinuz
    append file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa nomce nosmp noapic locale=bg_BG --
    
LABEL live-noacpi
    menu label ^Start Lubuntu (disable ACPI)
    kernel /casper/vmlinuz
    append file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet acpi=off splash locale=bg_BG --
    
LABEL live-install
    menu label ^Install Lubuntu
    kernel /casper/vmlinuz
    append file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash locale=bg_BG --
    
LABEL check
    menu label ^Check filesystem for defects
    kernel /casper/vmlinuz
    append boot=casper integrity-check initrd=/casper/initrd.lz quiet splash --
    
LABEL memtest
    menu label ^Test memory
    kernel /install/mt86plus
    
LABEL hd
    menu label ^Boot from first hard disk
    localboot 0xffff
    append -

MENU BACKGROUND backg.png
ALLOWOPTIONS 1
timeout 150
menu color title    1;31;49        #eeff1010 #cc553333 std
menu color sel        7;37;40        #ffffffff #99660000 all
menu color border    30;44        #ffffffff #00000000 std
menu color pwdheader    31;47        #eeff1010 #20ffffff std 


---


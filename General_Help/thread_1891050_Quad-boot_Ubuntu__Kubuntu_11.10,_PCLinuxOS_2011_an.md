---
title: "Quad-boot Ubuntu / Kubuntu 11.10, PCLinuxOS 2011 and Fedora 16... -- GRUB2 Help"
date: 2011-12-04
forum: General Help
---

### Post by ryanwolf74 on 2011-12-04
Ello.. I'm making a quad boot system with 6 partitions (1 is swap, 4 is main os'es and 5th is a testing part for the trying of other os).

I knew something like this would happen because since PCLOS uses GRUB Legacy it'd cause some commotion, but how do I get it to boot in this condition?

Some things that may be to your interest:

 > jkeys0@jkeys0:~$ sudo os-prober
[sudo] password for jkeys0: 
/dev/sda6: PCLinuxOS: PCLinuxOS:linux (spaces added because colon and P makes some smiley -_-)
/dev/sda7:Fedora release 16 (Verne):Fedora:linux
/dev/sda8:Ubuntu 11.10 (11.10):Ubuntu:linux> jkeys0@jkeys0:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007c468

   Device         Boot      Start            End               Blocks           Id         System
/dev/sda1                            4094           312580095    156288001    5          Extended
/dev/sda5                            4096            17022975      8509440       82         Linux swap / Solaris
/dev/sda6                        17025024      86775807         34875392     83         Linux
/dev/sda7         *         86777856  145938431     29580288    83        Linux
/dev/sda8                       145940480   230926335      42492928    83         Linux
/dev/sda9                      230928384   281716735       25394176    83         Linux
/dev/sda10                    281718784   312580095       15430656    83         Linux
sudo nano /etc/grub.d/40_custom

> #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "PCLinuxOS 2011.6" {

set root=(hd0,msdos6)

chainloader +1

}

Hopefully that stuff will help out.. I added the custom entry myself but trying to boot bring up an error about no signature or something..

Thanks! :D

---

### Post by jjex22 on 2011-12-04
Hi there!

Just to confirm, do you mean you've installed PClinuxOS last and now it's bootloader is in charge and can't hand over to the grub2 bootloaders?

if this is the case, load up PCLOS, go to /Boot/grub/menu.lst and make sure you've got an entry for ubuntu in the menu.lst that looks like this

title Ubuntu (dev/sda8 )  - no space between 8&)
root (hd0,7)
kernel /boot/grub/core.img
boot

This should enable you to get into ubuntu (which has the newest bootloader) and then run

sudo update-grup

Which will hopefully make Ubuntu's grub 1.99 default and set up entries for the others. 

Hope it helps! let me know If this wasn't the problem!

p.s. for fututre reference when adding distro's it's best to make them install their bootloaders to their own partitions rather than the MBR - that way, you just have to run update-grub to add them, and a again once you've removed them :)

---

### Post by ryanwolf74 on 2011-12-04
Hi, thanks for the quick reply!

I installed PCLinuxOS first, followed by Fedora 16, Kubuntu and Ubuntu 11.10 being the last 2.

---

### Post by jjex22 on 2011-12-04
Sorry, I got a bit confused - what exsactly is the problem? which OS(s) cant you get into, and which bootloader are you using?

---

### Post by ryanwolf74 on 2011-12-04
Ubuntu 11.10's GRUB bootloader is in use, and really I just cannot boot into PCLinuxOS.. :/

---

### Post by oldtimer7777 on 2011-12-04
> **ryanwolf74 said:**
> Ubuntu 11.10's GRUB bootloader is in use, and really I just cannot boot into PCLinuxOS.. :/

Doesn't PCLinuxOS have a rescue disc that you can boot from to load their version of Grub to repair it?

If you need to run multiple servers, why don't you just use Fusion VMWare instead? And just visualize everything?

---

### Post by oldfred on 2011-12-05
Post boot script, it will be long, so be sure to use code tags. Did you install PCLinix's grub legacy to its PBR partition boot sector? But grub2 from Ubuntu should directly boot it anyway.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

### Post by ryanwolf74 on 2011-12-06
> **oldtimer7777 said:**
> Doesn't PCLinuxOS have a rescue disc that you can boot from to load their version of Grub to repair it?

If you need to run multiple servers, why don't you just use Fusion VMWare instead? And just visualize everything?
I don't know.. Do you mean the LiveCD? I've only heard of that option for Mandriva Powerpack or Ubuntu Boot-Repair. 

Im not running a server either.. and VMWare isn't exactly a good thing for a netbook :/

> **oldfred said:**
> Post boot script, it will be long, so be sure to  use code tags. Did you install PCLinix's grub legacy to its PBR  partition boot sector? But grub2 from Ubuntu should directly boot it  anyway.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file  and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New  Reply Edit toolbar and then paste the contents between the generated [  code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible.  New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

I don't know what is the PBR.. But I know booting it gives about 3 errors, 

1. File doesn't exist
2. vga=860 or something is deprecated. Please use vga=(other options) instead.
3. No such partition (Fake.. it obviously is there)

I will check out the link you gave me.. thanks so far everyone

---

### Post by oldfred on 2011-12-06
PBR is partition boot sector. Like MBR is first sector of hard drive, PBR is first sector of partition. Used by Windows for boot code. Grub legacy can be installed to PBR, grub2 does not like to be installed to PBR.

vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

Need script to see if inconsistency in UUIDs or sdaX's are causing other errors. Sometimes partition issues.

---

### Post by ryanwolf74 on 2011-12-06
Thanks for the info. All of their GRUB's was selected to be installed on the MBR.

About vga, won't the 1024x768 be too big for a netbook? I believe mines is 1024x600, will it support it?

---

### Post by oldfred on 2011-12-07
You have to use the correct setting or something smaller that is compatible. Then it seems like 1024x600 would be correct.

You can see what vga= setting you had and find the mode that matches:

VGA conversions:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

---

### Post by ryanwolf74 on 2011-12-07
Hello all! As of right now I am marking this thread as solved. Last night I have been tinkering around with the 40_custom file. Basically the GRUB got the vmlinux and intrid boot file thing wrong.. so now I can freely boot into all my OS'es perfectly, although it still has that invalid signature error...

Thank you all SO much for your help. :D And one day I hope this thread helps someone else too. To make that possible, here is my 40_custom file.

> #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "PCLinuxOS release 2011.6 (on /dev/sda6)" --class gnu-linux --class g$
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos6)'
        search --no-floppy --fs-uuid --set=root 86282f93-7a70-4be1-aba2-e4bb019$
        linux   /boot/vmlinuz-2.6.38.8-pclos3.bfs root=/dev/sda6
        initrd  /boot/initrd-2.6.38.8-pclos3.bfs.img

chainloader +1

}Basically, I copied some parts of the Ubuntu entry and compared the PCLOS entry to make that. 

Now If I can only find out how to mark this solved..

**EDIT:** Found out how.. under thread tools. Wasn't really all that hard :P

---


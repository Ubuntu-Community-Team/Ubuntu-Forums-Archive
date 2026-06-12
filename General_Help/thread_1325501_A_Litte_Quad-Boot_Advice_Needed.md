---
title: "A Litte Quad-Boot Advice Needed"
date: 2009-11-13
forum: General Help
---

### Post by TrevT93 on 2009-11-13
(I know, how many people actually have the desire to do this?)

Hi.  I'm looking for a little advice.  My hard disk is split into five partitions right now:

Windows Vista Recovery (unknown filesystem type, but I'd bet it's NTFS)
Windows Vista (NTFS)
Windows 7 RC 1 (NTFS)
Kubuntu 9.10 (EXT4)
Linux Swap Space (SWAP)

And, crazy as it may sound, I'm looking to make it six, with the fourth OS being openSUSE w/ GNOME (and eventually I'll use it to try out a bunch of other Linux distros when I get spare time).  I have a 13 GB space to install it on.

Here's my problem: I researched a little on tri- and dual-booting and found out that there are times that installing a separate Linux OS when another is present causes the other to disappear off the radar screen when the new one is installed.

But I have also heard that you should just allow the OS to go about its own business when installing and your computer will be okay.  Conflicting advice...it's no good.

I figured that, before I go and rush headfirst into action, I may as well ask around.  And here would be my first choice; my experiences on this forum have been quite positive so far, and it's better than asking around a forum where you've had no experience so far.

So...what will happen if I install openSUSE with Kubuntu already installed?  Will everything be okay because they both use GRUB?  Will one partition be left behind?  What should I do to avoid this or fix it after it happens, if it comes to that?

Thanks in advance, I know you guys will be helpful :) .

-TrevT93

EDITED: in a little problem now, because prior advice caused a total wipeout of my ability to boot into an OS...still working on a solution to that, any advice would help.  Thanks.

EDIT 2: the aforementioned problem and in fact all problems have been resolved.  Thanks to everyone for the help.

---

### Post by ranch hand on 2009-11-13
Yes, I think you are nuts.  What is all that space being wasted on MS products for?

I only have 10 OS' on my box right now.

I always let the installer do its thing.  I want each OS to be set up to boot everything else.  The last installed will be boot/root unless you change it.

You probably know how to set the boot/root with the live CD.  Here is how to do it with grub2;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I would want grub2 fore the job in the long run as it is the easiest to update, just run "sudo update-grub".

---

### Post by TrevT93 on 2009-11-13
> **ranch hand said:**
> Yes, I think you are nuts.  What is all that space being wasted on MS products for?

I get that a lot.  Know in advance that I'm a high school student.  Not sure if I'll be able to get Windows 7 (the real deal), but when I can, Vista is out the door.  Its recovery sector (factory-installed) too.  I need at least one kind of Windows because my high school's wireless network is run by Windows and a tech guy that I would swear hates everything non-Windows.  I can get around his security scanners with a static IP (something he warned us about in the past but never fixed...), and then access the internet, but I don't think that will last forever.

Here's the thing with my school's tech guy: he set up the school's networks on purely Windows systems.  Everything is slow and unreliable, prone to failure every few weeks.  And he's afraid of being done in by a Kubuntu-running laptop (that he can't scan; his security scanner only works on Windows) carrying a virus onto his system!  Kind of absurd...but if you knew the guy, you would think he's just a little bit unreasonable.  And paranoid.

Anyway, thank you, I'll see how it goes.

---

### Post by ranch hand on 2009-11-13
Wow, he must be supplied by MS too.  Most IT guys know better.

Have FUN.

---

### Post by TrevT93 on 2009-11-13
Here's what the openSUSE installer says about my system (if openSUSE was to be installed):

Under the Booting section:

-Boot loader type: GRUB
-Status location: /dev/sda4 (extended)
-Change location:
   -Boot from MBR is disabled
   -Boot from "/" partition is disabled
-Sections:
+openSUSE 11.2 (default)
+windows 1
+windows 2
+windows 3
+Failsafe -- openSUSE 11.2

That doesn't sound right.  Why is there no "Ubuntu 9.10" in the "Sections" list?

Just making sure before I go ahead with this.

---

### Post by ranch hand on 2009-11-13
It is not there because SUSE does not play well with other OS'.  Loves MS but screws with every thing else.

---

### Post by TrevT93 on 2009-11-13
Following the instructions in the link, I'm at a section that says "Now you need to edit the **/etc/default/grub** file to fit your system."  But I don't know what to edit...

What do I need to do with the file?

---

### Post by ranch hand on 2009-11-13
Skip the bugger.  There is nothing wrong with your grub2 so no need to edit anything.  You need to mainly
```

sudo grub-install /dev.sda

```
Everything else can be handled when you get back in to your OS.

---

### Post by TrevT93 on 2009-11-13
You meant "/dev/sda", right?  Giving it a shot now...

EDIT: the command line returned:

```
Installation finished.  No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not.  If any of the lines is incorrect,
fix it and re-run the script 'grub-install'.

(hd0)    /dev/sda
```

---

### Post by ranch hand on 2009-11-13
Yes.  I really need to learn to type.

---

### Post by TrevT93 on 2009-11-13
Problem: I'm only getting a GRUB command line now.  I'm guessing that's because only /dev/sda showed up showed up when I installed GRUB into the MBR in the last step.

What do I need to change this time to get all my OSes back?

---

### Post by ranch hand on 2009-11-13
You only have one grub2 OS, right?

You have no trouble seeing that it is all there from the LiveCD?

---

### Post by TrevT93 on 2009-11-13
Both right.  Or at least, I think openSUSE 11.2 still uses the original GRUB.

---

### Post by ranch hand on 2009-11-13
Well if you have a terminal try running "update-grub".  Let us see what happens.

We may have to look at your grub files.

---

### Post by TrevT93 on 2009-11-13
Ran that in the Ubuntu Live terminal.  It returned:

```
grub-probe: error: cannot find a device for /.
```Seems like there's something wrong with device.map.  It only reads:

```
(hd0)   /dev/sda
(hd1)   /dev/sdb
```I don't have a second hard disk...

Again, not that I would know, because I'm still a little bit of a beginner.

---

### Post by oldfred on 2009-11-13
Whenever we are not sure of system configuration it is best to run this script as it documents the entire boot process. You can download and run from a liveCD.

Boot Info Script 0.32 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions 
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) 
cd to directory saved to: 
chmod 755 boot_info_script032.sh 
sudo ./boot_info_script032.sh 
or as example if on desktop 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by TrevT93 on 2009-11-13
Thanks for chiming in.  I really appreciate it.

Here's what I get back:

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks at sector 
    2218690918 on boot drive #4 for core.img, but core.img can not be found at 
    this location.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda4 and 
                       looks at sector 282698790 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5cb4fa98

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    21,478,904    21,478,842   7 HPFS/NTFS
/dev/sda2          21,478,905   167,027,800   145,548,896   7 HPFS/NTFS
/dev/sda3         167,027,805   261,378,740    94,350,936   7 HPFS/NTFS
/dev/sda4    *    261,393,615   312,576,704    51,183,090   5 Extended
/dev/sda5         310,199,148   312,576,704     2,377,557  82 Linux swap / Solaris
/dev/sda6         261,393,741   282,358,564    20,964,824  83 Linux
/dev/sda7         282,358,566   310,199,084    27,840,519  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="FE7E736B7E731B99" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda2: UUID="74A695FBA695BE54" TYPE="ntfs" 
/dev/sda3: UUID="30B81F9DB81F60A0" TYPE="ntfs" 
/dev/sda5: UUID="acf97f4c-7d2b-4f93-a051-2cbd79184997" TYPE="swap" 
/dev/sda6: UUID="01302bda-0a9e-4a61-a3c4-8f5aa7e6c150" TYPE="ext4" 
/dev/sda7: UUID="f7439938-ebd1-49f8-b847-03f8b880710e" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/disk-2 type ext4 (rw,nosuid,nodev,uhelper=hal)
/dev/sda7 on /media/disk-3 type ext4 (rw,nosuid,nodev,uhelper=hal)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 01302bda-0a9e-4a61-a3c4-8f5aa7e6c150
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 01302bda-0a9e-4a61-a3c4-8f5aa7e6c150
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=01302bda-0a9e-4a61-a3c4-8f5aa7e6c150 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 01302bda-0a9e-4a61-a3c4-8f5aa7e6c150
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=01302bda-0a9e-4a61-a3c4-8f5aa7e6c150 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set fe7e736b7e731b99
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 74a695fba695be54
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=01302bda-0a9e-4a61-a3c4-8f5aa7e6c150 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=acf97f4c-7d2b-4f93-a051-2cbd79184997 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 133.8GB: boot/grub/grub.cfg
 133.8GB: boot/initrd.img-2.6.31-14-generic
 133.8GB: boot/vmlinuz-2.6.31-14-generic
 133.8GB: initrd.img
 133.8GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Fri Nov 13 15:56:33 EST 2009
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,6)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.2
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.31.5-0.1-default root=/dev/disk/by-id/ata-WDC_WD1600BEVS-22RST0_WD-WXC607621985-part7 resume=/dev/disk/by-id/ata-WDC_WD1600BEVS-22RST0_WD-WXC607621985-part5 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-default

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,1)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 3###
title windows 3
    rootnoverify (hd0,2)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.31.5-0.1-default root=/dev/disk/by-id/ata-WDC_WD1600BEVS-22RST0_WD-WXC607621985-part7 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-default

============================= sda7/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

/dev/disk/by-id/ata-WDC_WD1600BEVS-22RST0_WD-WXC607621985-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD1600BEVS-22RST0_WD-WXC607621985-part7 /                    ext4       acl,user_xattr        1 1
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda7: Location of files loaded by Grub: ===================


 144.5GB: boot/grub/menu.lst
 144.5GB: boot/grub/stage2
 144.5GB: boot/initrd
 144.5GB: boot/initrd-2.6.31.5-0.1-default
 144.5GB: boot/vmlinuz
 144.5GB: boot/vmlinuz-2.6.31.5-0.1-default
 144.5GB: grub/grub.cfg
```

I don't know about you, but it seems as though the first part is a bit significant.  GRUB2 is looking for a file that isn't there.

---

### Post by ranch hand on 2009-11-13
I am afraid that openSUSE ate the sucker.  You have to watch it like a hawk or it will wipe out several linux OS' with its installer.  The only thing that anyone would ever, apearantlly, want to dual boot with is MS.

---

### Post by TrevT93 on 2009-11-13
Great, but what do I do?  I can't boot into anything now...I just get an empty GRUB screen.  With a prompt.

Does this mean I have to use my Windows disk to restore the MBR and work from there?

---

### Post by ranch hand on 2009-11-13
That is one thing you could do and maybe the best, I do not know much about the durability of the MS boot loader.

An other thing is to reinstall 9.10.

There is nothing stopping you from doing that after you repair the MS boot loader.

I hope you use R-W CDs, there are better uses for them than SUSE.

---

### Post by audiomick on 2009-11-13
Try running the Ubuntu installer again. If I understood that log that you posted correctly, all your OSes are still there. Let it run at least far enough for it to get to the screen that tells you what it has found on the computer. You can always bail out at that point and think it over again.
I have also seen a number of posts suggesting that you can re-install grub using the Ubuntu live CD. You'll have to do a bit of searching for that though.
In short, don't do anything too hasty

---

### Post by TrevT93 on 2009-11-13
I'm thinking I will just reinstall Kubuntu.  The one document on there that's of importance I can throw onto my USB during a live session.

Next question: if I'm going to reinstall Kubuntu, is there anything I'll need to do to get GRUB to re-recognize openSUSE?

---

### Post by oldfred on 2009-11-14
I would reinstall grub2 to the MBR to boot your Kubuntu. Then I would see if the osprober finds your openSuse. If not I would copy the grub entry from openSuse to /etc/grub.d/40_custom.

It almost looks like your openSuse renumbered partitions which messed up everything. You seem to have new grub still in the MBR and it points to the extended partition which is really just a container for the logical partitions. Also old grub is in the extended partition and the boot flag is in the extended partition. So is that how openSuse boots?

to reinstall grub2:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

### Post by TrevT93 on 2009-11-14
@oldfred: thank you, the instructions got me back to GRUB2 the way it used to be, with the multiple options for booting into Kubuntu and Windows!

Okay, next challenge.  As I had expected, openSUSE is still not on the GRUB2 list.  I'm guessing that there's a missing entry somewhere.  What do I have to do to get this working?

---

### Post by ranch hand on 2009-11-14
With grub2 the first thing to always do is run;
```

sudo update-grub

```
The next thing to do is create a custom menu file.   See the link it my sig for that.  The first 2 links deal with it too (in depth).

An entry similar to the one I use for Mandriva should work, I think.

---

### Post by oldfred on 2009-11-14
ranch hand has some good examples out there. You can copy your old grub entry for openSuse and modify it to grub2 style for pasting into 40_custom.

The main deferences beweeen old grub and new are the adding of { } at the beginning & end and The red bits, note the reason the partition number is red is because it is one higher as grub2 count from 1 not 0 as  old grub.
[COLOR=Red]set[/COLOR] root[COLOR=Red]=[/COLOR](hd0,[COLOR=Red]2[/COLOR])
[COLOR=Red]linux [/COLOR] /boot/vmlinuz-2.6.18-6-686 root=/dev/sda11  
initrd   /boot/initrd.img-2.6.18-6-686
boot

---

### Post by oldfred on 2009-11-14
Another choice since I chainboot just about everything. It seems that your openSuse installed grub to the extended partition whicyh is just a container but is still a primary. So maybe it needs a primary to boot from.
If direct booting as ranch hands examples are, does not work perhaps chainbooting to the grub that openSuse installed will? I tried to adjust to your partition:

menuentry “openSUSE 11.2 to grub on sda4, by chainloader”  {
set root=(hd0,4)
chainloader +1
}

other examples from:
[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0)

menuentry “Kubuntu 9.10 on sdb7, by chainloader”  {
set root=(hd1,7)
chainloader +1
}

"chainloader +1" says to go to sector 1 (of (hd1,7)) and turn control over to the bootloader found there.

For this example to work, a bootloader (e.g., GRUB 2) must be installed to the partition (hd1,7).
To install GRUB 2 to the boot sector of partition sdb7 (=(hd1,7)):
sudo grub-install /dev/sdb7

This is another way to write the same boot entry:
menuentry “Kubuntu 9.10 on sdb7, by chainloader”  {
chainloader  (hd1,7)+1
}

Another Linux example

menuentry “Drive sdc = hd2 by chainloader”  {
chainloader  (hd2)+1
}

---

### Post by TrevT93 on 2009-11-14
Actually...update-grub took care of the whole mess.  It managed to somehow place openSUSE on the menu.

And here I was thinking that things would be more complicated than this!

Okay, thanks everyone for the invaluable help.  I've learned a lot from this experience.

Before I take off, can I customize the GRUB2 menu with that 40_custom file (just looking to make the names a little more user-friendly in case anyone else boots up my laptop)?

Thanks again!

---

### Post by ranch hand on 2009-11-14
The generated menu entry for SUSE works?

If so this is great.  Please let us know.

---

### Post by oldfred on 2009-11-14
Glad it worked. I agree with ranch hand and would like to know what entry it generated. 

You can either modify to logic in the grub config or turn off the osprober and manually put in entries into 40_custom or any number of ##_custom files.

Grub 2 Title Tweaks Thread
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

---


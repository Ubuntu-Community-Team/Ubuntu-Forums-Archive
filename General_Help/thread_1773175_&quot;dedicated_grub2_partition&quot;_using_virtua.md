---
title: "&quot;dedicated grub2 partition&quot; using virtual machine +live CD"
date: 2011-06-01
forum: General Help
---

### Post by 29much on 2011-06-01
After trying for several day, with help from google, I give up. I am pessimistic there will be a response for my problem, but here it is:

I'm trying to build perfect partition for Ubuntu/Linux in general. It start from MS-OS because the idea is to migrate from it to Linux. In my idea, perfect partition sequence in the hd is something like this:

[LIST=1]
[*]GRUB2 partition (primary partition,ext4).
[*]SWAP partition (primary partition)
[*]Extended partition contain:
[/LIST]
[INDENT][LIST]
[*]Ubuntu or other Linux distro as main OS (logical partition1).
[*]Other Linux distro or any other OS (logical partition2).
[*]Data partition (either ext3, ext4, fat, ntfs, or hfs).
[*]Installation partition, all the ISO for installation purpose is is placed here.
[/LIST][/INDENT]

The hd is unplugged from the box and mounted as external hd through USB port to other machine. Ubuntu Live CD run from VMWare/virtualbox is used to create the partition and to install GRUB2. 

Using Gparted, I succeed to create the partition mention above. But I have problem when came to the task installing GRUB2. From lot of source i install GRUB2 using this command:

```
sudorub-install --root-directory=/media/Grub /dev/sda
```

It's produce an error (I forget what the error, I'll try again and put it here latter)

Then I follow this code:

```
sudo mount /dev/sda1 /mnt
sudo mkdir /mnt/dev
sudo mount --bind /dev /mnt/dev
sudo mkdir /mnt/proc
sudo mount --bind /proc /mnt/proc
sudo mkdir /mnt/sys
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

[LIST]
[*]It's also produce error
[/LIST] 

```
chroot: cannot execute the command `/ bin / bash ': No such file or directory type 
```

I try /usr/sbin/chroot with no luck either.

I'll try again to find out why the method is fail. All the solution that I found in internet isn't about boot to live CD using virtual machine. I'll try also from Live USB (boot the machine) to see any different.

---

### Post by oldfred on 2011-06-01
You cannot chroot into an install until you have an install. So what do you want to do. If you just want to boot the ISO in you ISO partition manually create a grub.cfg file in your sda to loopmount any ISO you copy into your install partition. I have done essentially the same thing in setting up my flash drives. I have one with grub & all the ISO in one partition. I have one with a windows repair install converted to boot with grub and then loading other repair ISOs from another partition.

Hard drive:
Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by 29much on 2011-06-01
Thank you for the link, it's a comprehensive threads, but I still not manage to pinpoint what I do wrong 

This is my problem: can not Install Grub2.

I'm running Ubuntu Live CD in VMware. After create partition using Gparted in external hard drive ( 2.5 inch laptop-hard drive, connected via ATA to USB converter) I open terminal and run this command (also said in the link from post above)```
sudo grub-install --root-directory=/media/grub2 /dev/sda
```The error is```
/usr/sbin/grub-probe: error cannot stat 'aufs'.
```

Is it because I'm trying to install grub2 from 32-bit Ubuntu Live CD running from VMware in 64 OS try to install grub2 from  or I'm wrongly understand all the tutorial above?

Well I can test it with run Ubuntu Live from USB by restarting my desktop, but that's not the idea.

Latter on I will install Ubuntu to my laptop from hd (old one and the only one I have, broken optical drive, can not boot to USB), so the link is very usefull. But before I move to the next step, I need to install grub2 in the hard drive, right?

It said in [here]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")
```
Choose an existing partition or create a new one and format it with a file system, you will need at least about 60 MiB of space in the partition for grub 2 files, but a little more room than that might be advisable.
Format the partition with a file system and optionally give the file system a FILE SYSTEM LABEL. 
Mount the partition by clicking on its icon in the 'Places' menu.
Run a grub-install command similar to the one shown below,[CODE]sudo grub-install --root-directory=/media/grub2 /dev/sda
```Where: '/media/grub2' is the mount point for the file system I want to have GRUB files created in
Where:  I want to make a new /boot/grub directory and fill it with GRUB files.
Where: '/dev/sda' is the hard disk in which I want to write the stage1 code to MBR in[/CODE]

I think I need to modify the command to meet my condition, but I still not get it, what command should I use.

---

### Post by 29much on 2011-06-01
from [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1288604")

```
&#8220;/media/USBFolderName&#8221; for the mounted directory name which must be replaced with the proper names of your plugged in USB flash drive. 
If you don't know them you can look under the File System tab from the System Monitor or execute the &#8220;mount&#8221; command in a terminal.

```

that i think is my mistake.

---

### Post by 29much on 2011-06-01
Got it.

"--root-directory=/media/grub2" is the partition that grub2 want to be placed.

The problem: The partition is mounted with ridiculously automatically long name. Did not mastering how to mounting manually to human friendly mounted directory name.

Solution: Read the tutorial much more carefully.

Conclusion: Installing grub2 from virtual machine using live cd is no different than booting the host pc physically.

Next steep, Installing from hard-drive.

Side note, installing red-hat like distro (using Anaconda) perhaps require fat32 or ext3 partition because last time I use Anaconda, it can not detect ntfs or ext4, perhaps because I do not know the appropriate module to be loaded. Reading tutorial how to load ISO from non Linux partition.

---

### Post by 29much on 2011-06-01
Side note again:

Using [plpbt.iso]("http://www.plop.at/") the grub2 in USB/External hard drive can be tested. Because version VMware that I use can not boot to real USB. I do not know about virtualbox.

The idea is to create a perfect Ubuntu/Linux installation system, using any kind of OS, without necessity to turn-on/off the real machine that we use to work.

---

### Post by oldfred on 2011-06-01
I know nothing about vitualbox. 

Have not installed Redhat since the about 7-10 year ago versions 5.1 and 7.1. Do the new versions require a separate boot partition and use old grub? If grub legacy install grub's boot loader to the Partition boot sector PBR not the MBR. then you can easily chainload it from grub2.

This was with grub legacy and now grub2 does not like to be installed to a partition and will not be totally reliable if installed to a PBR. But if booting with old grub you can still easily set the grub2 partition to chainload to old grub installed in a partition like this:
chainboot 145 systems - saikee
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by oldfred on 2011-06-01
This is one of my manually configured grub.cfg for my flash with ISO. Booting a hard drive ISO requires specific HdX,Y info also - see link above to drs305's how to:

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 11.10 Oneiric 64bit" {
    set isofile="/boot/iso/oneiric-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

menuentry "Ubuntu 11.04 Natty 64bit" {
    set isofile="/boot/iso/ubuntu-11.04-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/iso/ubuntu-10.10-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}


menuentry " " {
set root= 
}


# iso_filename=$isofile boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
menuentry "Parted Magic" {
    set isofile="/boot/iso/pmagic-6.1.iso"
    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw loglevel=0 max_loop=256
    initrd (loop)/pmagic/initramfs
}

menuentry "Gparted live" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/iso/gparted-live-0.8.0-5.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile nomodeset
  initrd (loop)/live/initrd.img
}

# boot=live config  noswap noprompt  toram=filesystem.squashfs ip=frommedia  nosplash
menuentry "Gparted Live ISO" {
set isofile="/boot/iso/gparted-live-0.8.0-5.iso"
loopback loop $isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs nomodeset
initrd (loop)/live/initrd.img
}
menuentry "SystemRescueCd 1.6.3" {
 set isofile="/boot/iso/systemrescuecd-x86-1.6.3.iso"
 loopback loop $isofile 
 linux (loop)/isolinux/rescuecd isoloop=$isofile  
 initrd (loop)/isolinux/initram.igz
}

menuentry "Puppy 511" {
set root=(hd0,1)
linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=usbflash loglevel=7 pkeys=us 
initrd /boot/lupu511/initrd.gz
}

menuentry "slitaz " {
  set isofile="/boot/iso/slitaz-3.0.iso"
  loopback loop $isofile 
  linux (loop)/boot/bzImage rw root=/dev/null lang=C kmap=us screen=1024x768x16 autologin noprompt noeject
  initrd (loop)/boot/rootfs.gz
#  linux (loop)/boot/bzImage isofrom=$isofile boot=live quiet vga=791 noeject noprompt
}

menuentry "archlinux-2010.05" {
    set isofile="/boot/iso/archlinux-2010.05-core-x86_64.iso"
    loopback loop $isofile 
    linux (loop)/boot/vmlinuz26 findiso=$isofile archisolabel=MC4GB tmpfs_size=75% locale=en_US.UTF-8
    initrd (loop)/boot/archiso.img
}

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

menuentry "Memory test (memtest86+)" {
 linux /boot/memtest86+.bin
}

menuentry "Custom Menu"{
        configfile (hd2,5)/boot/grub/grub.cfg
        }

menuentry "boot to first mbr"{
set root=(hd0)
chainloader +1
}

Boot most up2date Maverick kernel on sdb2
menuentry "Lucid on sdb2 - hd1?" {
    set root=(hd1,2)
        linux /vmlinuz root=/dev/sdb2 ro quiet splash
        initrd /initrd.img
}

Boot most up2date Lucid kernel on sdc7
menuentry "Lucid on sdc7 - hd2?" {
    set root=(hd2,7)
        linux /vmlinuz root=/dev/sdc7 ro quiet splash
        initrd /initrd.img
}


```

---

### Post by 29much on 2011-06-02
This is what my menu.cfg looks like```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu" {
    set isofile="(hd0,6)/isos/ubuntu-11.04-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "Slax" {
    set isofile="(hd0,6)/isos/slax-6.1.2.iso"

    loopback loop $isofile 
    linux (loop)/boot/vmlinuz from=$isofile ramdisk_size=6666 root=/dev/ram0 rw
    initrd (loop)/boot/initrd.gz
}

```
I used this command to install grub```
sudo grub-install --root-directory=/media/mounted_directory_name /dev/sda
```the grub menu tell me that my grub version is 1.99, even though I just edited grub.cfg file.

Anyway, I understand the method to put the ISO file in the same partition with grub. But my idea is to put the ISO file either in separated ntfs or ext4 partition. I can go to Anaconda method anytime, like last time I installed CentOS, by loading Anaconda and ISO installer from ext3 partition, but I want to know Ubuntu better.

For start, what is Ubuntu ISO Installer (similar with Anaconda) or how to load that Installer or ISO file when they are placed in ext4 or ntfs partition.

Now by writing ```
set isofile="(hd0,6)/isos/ubuntu-11.04-desktop-i386.iso"
``` am I telling grub to load an ISO file located in the six partition of the 0 hard drive? the respond is
```
error: there is no such file
``` if I tell it right, should I load some kernel first (from grub partition) to read ext4 or ntfs partition?

my hard drive configuration is

GRUB2 partition (primary partition,ext4, sda1).
SWAP partition (primary partition, sda2)
Extended partition (sda3) contain:
[INDENT][LIST]
[*]ext4 partition(logical partition, sda5).
[*]ntfs (logical partition, sda6).
[*]ntsf (logical partition, sda7)
[/LIST][/INDENT].


I put Ubuntu Live CD ISO at sda7 under folder ISO. Here the fdisk -l result```
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x37bb37ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      102400   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13         144     1048576   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sdb3             144        9730    76998656    5  Extended
/dev/sdb5             144        2326    17526784   83  Linux
/dev/sdb6            2326        4508    17525760    7  HPFS/NTFS
/dev/sdb7            4508        9730    41943040    7  HPFS/NTFS

```

---

### Post by 29much on 2011-06-02
Well, i take out the hard drive from machine that I use to set it, mounting it on my laptop, boot it and it goes to grub menu.

hit "c" button and enter grub command line. type ls and there it is the list of the partition. type "ls (hd0,7)/" grub list all the folder in hd0,7. there it is the Ubuntu ISO folder shown up. Turn out if the partition is sd#Y, even if the Y value is not sequence (i.e random) hdX,Y formula still need to be used, with #=a, then X=0, #=b X=1.

so I change the grub.cfg file to```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu" {
    set isofile="(hd0,[COLOR="Red"]7[/COLOR])/isos/ubuntu-11.04-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
```reboot the laptop, enter the grub menu, select ubuntu, and the error prompt does not come out, but for some reason it goes blank.

Either i need to load lighter kernel or i still do it wrong.

Comment? Pls?

---

### Post by 29much on 2011-06-02
My method can load slax.iso but then goes to error. so i think it's display related.

How to load Ubuntu ISO file from Hard drive with minimum configuration, display, processing memory and etc?

Is adding code vga=788 will do the trick? or "gfxpayload 800x600x16, 800x600" will do the trick.

so far in my conclusion that grub2 dedicated partition method can read ntfs/ext4 partition and load ISO installation. but in order the ISO can run properly, some set must be used.

So it's down to all to set the grub.cfg file and load the correct file.

---

### Post by oldfred on 2011-06-02
this was my entry to boot Ubuntu on a hard drive. This was in the same partition as my install. The drive, partition has to be on the loopback loop line.

menuentry "Ubuntu 10.10 Maverick ISO 64bit" {
    set isofile="/boot/ISO/maverick-desktop-amd64.iso"
 
    loopback loop (hd0,5)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

---

### Post by 29much on 2011-06-02
> **oldfred said:**
> this was my entry to boot Ubuntu on a hard drive. This was in the same partition as my install. The drive, partition has to be on the loopback loop line.To be honest I still can not grasp the meaning of loopback loop line.

This```
set isofile="/boot/ISO/maverick-desktop-amd64.iso"
``` will load maverick-desktop-amd64.iso located in the grub partition in folder /boot/ISO.

While this code```
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
initrd (loop)/casper/initrd.lz

```tell the location of initramfs (&#8220;an initial ramdisk, a temporary file system used in the boot process of the Linux kernel. initrd and initramfs refer to slightly different schemes for loading this file system into memory. Both are commonly used to make preparations before the real rootfile system can be mounted.&#8221;) and vmlinuz ("statically linked executable file that contains the Linux kernel in one of the executable file formats supported by Linux") inside maverick-desktop-amd64.iso.

now what "loopback loop (hd0,5)$isofile " do?

What I understand is after the linux kernel is loaded (vmlinuz), thing start to fall apart because not all linux ISO is design to be extracted from hard drive. Is loopback loop tell the location to extract and configure the ISO file to run live CD?

Anyway, currently I'm using dedicated grub partition to load plop linux in order to boot to USB in my old laptop. But latter on, I also want to create a hard drive that contain a lot of Linux variant, ready to be installed.

---

### Post by oldfred on 2011-06-02
As I understand the loopback loop is that if the ISO is correctly configured then the loop back command can look into the ISO and find the kernel & initrd files to boot from. When an ISO does not have the loop back feature you have to have the kernal & initrd files to load first. With Puppy I had to extract the boot files and boot them then from that load the Puppy ISO.

I just made this work from my USB flash drive. I booted gparted ISO on my sdc6 partition with this entry. I had to make drive 3 even though it is sdc as the flash drive became drive 0 in grub, sda then was drive 1 an sdc was drive 3.

menuentry "Gparted Live ISO in sdc6 " {
set isofile="/ISO/gparted-live-0.8.0-5.iso"
loopback loop (hd3,6)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs nomodeset
initrd (loop)/live/initrd.img
}

I was not able to quickly get it to work from my standard boot. But I boot a gpt partition now and sdc6 is msdos and I have to get it to know that. With 10.10 I had to add a parameter to even get it to chainload from gpt to XP in a MBR partitioned drive.

Grub's definition:

> loopback Mount a file as a device. `loopback loop (hd0,2)/iso/my.iso


---

### Post by 29much on 2011-06-02
little bit understand now, "/ISO/gparted-live-0.8.0-5.iso" is mounting file for "(hd3,6)/gparted-live-0.8.0-5.iso"

I think I have to look out more grub.cfg from other people. None of ISO file that I try to boot is working out.

I'm trying to work with Live Ubuntu, Slax Live Debian, mini Ubuntu, and Puppy (Plop is working fine).

I think I saw Puppy grub.cfg somewhere before.

Thanks for the help, btw.

---

### Post by 29much on 2011-06-10
How about this.

1. Create grub2 dedicated, swap, linux, and ntfs partition.
2. Extract the ISO to ntfs
3. Donwload grub4dos, extract to ntfs
4. Create grub.cfg in grub2 partition, add entry```
menuentry "Grub4dos kernel format" {
        set root=(hd0,Y)
        linux16 /grub.exe
}
```Y=ntfs partition

5. Edit menu.lst in ntfs partition add ```
title Install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz vga=788  -- quiet
initrd /kernel&initrd_folder/initrd.gz
boot

title Graphical install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz video=vesa:ywrap,mtrr vga=788  -- quiet
initrd /kernel&initrd_folder/gtk/initrd.gz
boot

title Expert install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz priority=low vga=788  --
initrd /kernel&initrd_folder/initrd.gz
boot

title Automated install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz auto=true priority=critical vga=788  -- quiet
initrd /kernel&initrd_folder/initrd.gz
boot

title Graphical expert install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz priority=low video=vesa:ywrap,mtrr vga=788  --
initrd /kernel&initrd_folder/gtk/initrd.gz
boot

title Graphical automated install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz auto=true priority=critical video=vesa:ywrap,mtrr vga=788  -- quiet
initrd /kernel&initrd_folder/gtk/initrd.gz
boottitle Install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz vga=788  -- quiet
initrd /kernel&initrd_folder/initrd.gz
boot

title Graphical install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz video=vesa:ywrap,mtrr vga=788  -- quiet
initrd /kernel&initrd_folder/gtk/initrd.gz
boot

title Expert install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz priority=low vga=788  --
initrd /kernel&initrd_folder/initrd.gz
boot

title Automated install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz auto=true priority=critical vga=788  -- quiet
initrd /kernel&initrd_folder/initrd.gz
boot

title Graphical expert install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz priority=low video=vesa:ywrap,mtrr vga=788  --
initrd /kernel&initrd_folder/gtk/initrd.gz
boot

title Graphical automated install
find --set-root /kernel&initrd_folder/vmlinuz
kernel /kernel&initrd_folder/vmlinuz auto=true priority=critical video=vesa:ywrap,mtrr vga=788  -- quiet
initrd /kernel&initrd_folder/gtk/initrd.gz
boot
```

6. Unplug the hard disk, mount it on the old laptop, boot and install Ubuntu, easily without difficult explanation.

I'm testing it in real laptop.

---

### Post by 29much on 2011-06-10
Testing it Using Debian (menu.lst is for debian actually)

The method is not work for debian. Trying to do it to Ubuntu, now.

Anyway, if anyone have ever try this method, please post the menu.lst for ubuntu, since the key of this method is menu.lst.

I'll close this thread, if I finally finish install any linux to my old laptop.

---

### Post by 29much on 2011-06-10
my menu.lst

```
default 0
timeout 60

title Install Ubuntu
find --set-root /casper/vmlinuz
kernel /casper/vmlinuz vga=788  -- quiet
initrd /casper/initrd.lz
boot

title ubuntu.iso
map (hd0,4)/isos/ubuntu-11.04-desktop-i386.iso (hd32)
map --hook
chainloader (hd32)
boot

title debian.live.iso
map --heads=256 --sectors-per-track=0 (hd0,4)/isos/debian-live-6.0.1-i386-gnome-desktop.iso (hd32)
map --hook
chainloader (hd32)
boot

title mini.ubuntu.iso
map (hd0,4)/isos/mini.iso (hd32)
map --hook
chainloader (hd32)
boot

title CommandLine
commandline

title Reboot
reboot

title Halt
halt
```

The first menu "Install Ubuntu" is not working. It said that it can not initiate the initrd. Second menu "ubuntu.iso" is working on virtual machine, but not in my old laptop, perhaps Ubuntu to advance for old machine. "debian ISO, debian live, is loading the menu screen successfully. Have not test the "mini.ubuntu.iso" yet.

---

### Post by 29much on 2011-06-11
Final method:

The partition:```
1. Dedicated Grub2 partition, primary, flag as bootable, ext2, (hd0,1).
2. SWAP partition, (hd0,2).
3. ext4 partition, primary partition, (hd0,3).
4. ntfs partition, extended partition-logical, (hd0,5).
5. ntfs partition, extended partition-logical, (hd0,6).

```

grub.cfg```
menuentry "plpbt.iso" {
    set isofile="/boot/isos/plpbt.iso"
    loopback loop $isofile
linux16 (loop)/plpbt.bin iso-scan/filename=$isofile quiet splash noprompt
}

menuentry "ntfs chainload boot" {
insmod ntfs
set root=(hd0,5)
drivemap -s (hd0) ${root}
chainloader +1
}

menuentry "grob4dos" {
set root=(hd0,6)
linux16 /grub.exe
}

menuentry "Ubuntu" {
    set isofile="(hd0,6)/isos/ubuntu-11.04-desktop-i386.iso"
     loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt gfxpayload=800x600x16--
    initrd (loop)/casper/initrd.lz
}

menuentry "DebianLive" {
    set isofile="(hd0,6)/isos/debian-live-6.0.1-i386-gnome-desktop.iso"

    loopback loop $isofile 
    linux (loop)/live/vmlinuz boot=live iso-scan/filename=$isofile quiet splash noprompt gfxpayload=800x600x16--
    initrd (loop)/live/initrd.lz
}
```

grub4dos menu.lst```
title Install Ubuntu
find --set-root /casper/vmlinuz
kernel /casper/vmlinuz vga=788  -- quiet
initrd /casper/initrd.lz
boot

title ubuntu.iso
map (hd0,6)/isos/ubuntu-11.04-desktop-i386.iso (hd32)
map --hook
chainloader (hd32)
boot

title debian.live.iso
map --heads=256 --sectors-per-track=0 (hd0,6)/isos/debian-live-6.0.1-i386-gnome-desktop.iso (hd32)
map --hook
chainloader (hd32)
boot

title CommandLine
commandline

title Reboot
reboot

title Halt
halt
```

Result:

All the Ubuntu method above is working in virtual machine, but not in my old laptop. Loading Ubuntu kernel and initial ramdisk using grub4dos is fail to load initrd.

All the Debian method mention above is fail.

---

### Post by oldfred on 2011-06-11
I am surprised this works in a virtual machine.

```
menuentry "Ubuntu" {
    set isofile="(hd0,6)/isos/ubuntu-11.04-desktop-i386.iso"
     loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt gfxpayload=800x600x16--
    initrd (loop)/casper/initrd.lz
}

```

My entry is like this with the drive not in the quotes:
```
menuentry "Ubuntu 10.10 Maverick ISO 64bit" {
set isofile="/boot/iso/maverick-desktop-amd64.iso"

loopback loop (hd0,2)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt noeject
initrd (loop)/casper/initrd.lz
}

```

And I save this in my notes which uses a set root:
```
With install of vmlinux & initrd.gz into iso folder
menuentry "Ubuntu 10.10 Server 32-bit CD" {
set root=(hd0,5)
set isofile="/iso/ubuntu-10.10-server-i386.iso"
loopback loop $isofile
linux /iso/vmlinuz iso-scan/filename=$isofile noprompt noeject
initrd /iso/initrd.lz
} 
server CD uses initrd.lz rather than initrd.gz and that is why it failed.

```

---

### Post by 29much on 2011-06-12
I use new hard drive, plug it to IDE to USB, format it to 2 partition.
1. ext3, bootable partition (hd0,1)
2. ntfs, primary partition, not bootable off course (hd0,2)

I install grub2 to (hd0,1) using command```
sudo grub-install --root-directory=/media/mounted_directory_name /dev/sda
```then create grub.cfg

This is working with slax.iso in the sense it load the ISO file. Latter on it produce an error, but at least it prove that ISO file can be loaded.
```
menuentry "Slax" {
    set isofile="(hd0,2)/isos/slax-6.1.2.iso"

    loopback loop $isofile 
    linux (loop)/boot/vmlinuz from=$isofile ramdisk_size=6666 root=/dev/ram0 rw
    initrd (loop)/boot/initrd.gz
}

```
I edit it using your entry (I put slax iso both of in isos folder and in the (hd0,2) root partition.
```
menuentry "Slax" {
    set isofile="/boot/isos/slax-6.1.2.iso"

    loopback loop (hd0,2)$isofile 
    linux (loop)/boot/vmlinuz from=$isofile ramdisk_size=6666 root=/dev/ram0 rw
    initrd (loop)/boot/initrd.gz
}

```

it's said that the file can not be found or something like that.

Anyway, by using this logic I create two grub entry```
menuentry "Ubuntu1" {
    set isofile="(hd0,2)/isos/ubuntu-11.04-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu2" {
    set isofile="/boot/isos/ubuntu-11.04-desktop-i386.iso"
 
    loopback loop (hd0,6)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

```

The first entry goes to forever cursor blink, do not know why, the second one report that file could not be find.

So what do you think? Why is this happen? Anyway, I solve my problem by using grub4dos to load ISO file (since I insist to separate the isos folder in ntfs partition).

The solution for using grub2 dedicated partition only, i think, is mount the iso file in ntfs partition to /boot/isos/ folder first. but i can not figure it out the command to do this.

btw, change the command to```
loopback loop (hd0,2)isos/$isofile
```

the error produced is " invalid file name 'isos/boot/isos/ubuntu-11.04-desktop-i386.iso' "

so where should I put the iso in (hd0,2)? inside folder /boot/isos/ in (hd0,2)?

---

### Post by oldfred on 2011-06-12
Maybe I am confusing you as my two examples are booting different drives. The hd0,6 is from my sdc drive which really is hd0 when I boot sdc from BIOS. In partition sdc6 which is a data partition only I have folder /ISO where I store all my ISO files. Grub will look in hd0.6 for a folder /ISO and the iso file to loopmount. This partition is ext3.

My example for hd0,2 is for my flash drive. When I use BIOS to boot it then it also is hd0. And the ISO files are in a folder in /boot/iso as I also boot from sdd2.

I have another flash where this works without the specification of a hdX,Y. I think it works only because the folder is in the boot partition.

```
menuentry "Ubuntu 11.04 Natty 64bit" {
    set isofile="/boot/iso/ubuntu-11.04-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

```

Drive & partition have to match drive & partition that files are in. Especially if different than boot drive. Sometimes the numbering is off one since the boot drive is hd0. When I boot my sdb drive I have to change the hd0,6 entry to hd2,6 so it sees the third drive. sdb is hd0 sda is hd1 and sdc is hd2. But if in BIOS I boot sdc the sdc6 is hd0,6.

Path/folder structure has to match. I had some confusion initially as I mount my data partition in /mnt/data, so I see my ISO folder as /mnt/data/ISO, but in the partition it is just /ISO which is all grub can see as it is not mounted yet.

I have only used FAT32 & ext3 perhaps you need the extra parameter:
insmod ntfs 
My data partition sdc6 is a MBR/msdos partition but when booting from sdb which is gpt I have to add this paramater. 
insmod part_msdos

---

### Post by 29much on 2011-06-15
ok, thanks for the info. i'm able now to load ISO file from different media, flash drive, internal or external hd, using several method. i figure it our several correct set-up for boot loading configuration. some still puzzle me though.

the problem that i face is not how to load the ISO anymore, but the ISO installer it self. I had to familiar with the distro in order able to load them from hd.

my friend asked me why we need to load installer from hd. well my answer is this, when building a box, we need physically attach the hard drive to the machine. why not just skip all the hustle by make the installation available in the hard drive. other reason is lot of laptop nowadays have hidden partition with installer, back-up or rescue system proprietary OS in it.

i think it's about time install from internal hd is in the front page how to install linux. install from network is cool too, but that's maybe next step.

---

### Post by 29much on 2011-06-22
I think I'm already write every thing that did. I play around several time installing linux, and every time I forgot about some code or step, I refer to this page back.

I do not have anything else to add regarding "Installing Ubuntu from hard drive with dedicated grub2 partition". The method is work for me. I'm pretty sure, I put the working code and step that I used in the recent post.

---


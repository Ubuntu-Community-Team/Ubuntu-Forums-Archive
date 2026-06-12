---
title: "Vista/Maverick dual boot screen pls help!!"
date: 2010-11-10
forum: General Help
---

### Post by samrat94 on 2010-11-10
I just recently reinstalled Ubuntu 10.10 through USB disk(without using wubi) after I realized that ubuntu was booting too slowly. However, after installing I noticed that there is no screen prompting the user to select between Vista and Ubuntu. How can I restore that?? Please help me!!

---

### Post by Rubi1200 on 2010-11-10
Hi and welcome to the forums :-)
Go to Applications > Accessories > Terminal and run the following command:
```
sudo update-grub
```If it picks up the all the operating systems, good.

If not, post the results of the boot-script linked at the bottom of my post please.

Thanks.

---

### Post by samrat94 on 2010-11-10
Hello Rubi,
Just did what you told and it does pick all the operating systems, but the prompt still doesn't show up when I restart the computer.

---

### Post by samrat94 on 2010-11-10
Sorry for double posting, but I also noticed another error. When Ubuntu boots, an error message show up for some time. The error message was 

```
udevd-work[370]  ....... -No such file or directory                      
```

I had some problems with my previous installation of Maverick which is why I reinstalled without using wubi. But the boot still seems to be very slow. Why is that?

---

### Post by Rubi1200 on 2010-11-10
When you are in Ubuntu can you please post the output of this file:

> /etc/default/grub

Just copy/paste the contents here and I will take a look.

Thanks

---

### Post by samrat94 on 2010-11-10
Here it is-

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by Rubi1200 on 2010-11-10
Hmm, the file looks fairly normal.

Clearly, something is causing the problem you are experiencing.

Click on the link at the bottom of my post and follow the instructions there for the boot info script.

post the results back here please.

Thanks for your patience.

---

### Post by samrat94 on 2010-11-10
Here it is

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,980,889    20,980,827  27 Hidden HPFS/NTFS
/dev/sda2    *     20,981,760   166,782,975   145,801,216   7 HPFS/NTFS
/dev/sda3         166,782,976   290,894,644   124,111,669   7 HPFS/NTFS
/dev/sda4         290,895,870   312,580,095    21,684,226   5 Extended
/dev/sda5         290,895,872   311,562,239    20,666,368  83 Linux
/dev/sda6         311,564,288   312,580,095     1,015,808  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4864ADF264ADE2C4                       ntfs       PQSERVICE                     
/dev/sda2        B200DE3100DDFBF3                       ntfs       ACER                          
/dev/sda3        58421DDE421DC224                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        880971a7-90b1-4716-896a-596e2d2cb6cc   ext4                                     
/dev/sda6        56270758-644c-4cd8-a334-0a7e420632db   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 880971a7-90b1-4716-896a-596e2d2cb6cc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 880971a7-90b1-4716-896a-596e2d2cb6cc
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 880971a7-90b1-4716-896a-596e2d2cb6cc
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=880971a7-90b1-4716-896a-596e2d2cb6cc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 880971a7-90b1-4716-896a-596e2d2cb6cc
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=880971a7-90b1-4716-896a-596e2d2cb6cc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 880971a7-90b1-4716-896a-596e2d2cb6cc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 880971a7-90b1-4716-896a-596e2d2cb6cc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4864adf264ade2c4
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set b200de3100ddfbf3
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=880971a7-90b1-4716-896a-596e2d2cb6cc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=56270758-644c-4cd8-a334-0a7e420632db none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 151.3GB: boot/grub/core.img
 158.0GB: boot/grub/grub.cfg
 156.3GB: boot/initrd.img-2.6.35-22-generic
 149.5GB: boot/vmlinuz-2.6.35-22-generic
 156.3GB: initrd.img
 149.5GB: vmlinuz

```

---

### Post by oldfred on 2010-11-10
Windows or grub do not correctly identify the recovery & Vista partitons, titles are reversed. If you boot recovery you should get into your Vista install.

The system seems to have an issue with something & it then resolves it.

I have had issues with gparted not mounting my sda drive. After I ran chkdsk on the NTFS partition in sda then it worked. You can try that on all your NTFS partitions, but I think it still is another boot issue. If you look in the logs do you see more info on issues? System, administration, log file viewer. I look in messages first but you can look in all of them. I look for repeated attempts at something or very long times between entries.

---

### Post by samrat94 on 2010-11-10
> **oldfred said:**
> Windows or grub do not correctly identify the recovery & Vista partitons, titles are reversed. If you boot recovery you should get into your Vista install.

The system seems to have an issue with something & it then resolves it.

I have had issues with gparted not mounting my sda drive. After I ran chkdsk on the NTFS partition in sda then it worked. You can try that on all your NTFS partitions, but I think it still is another boot issue. If you look in the logs do you see more info on issues? System, administration, log file viewer. I look in messages first but you can look in all of them. I look for repeated attempts at something or very long times between entries.

How do I do that? Could you elaborate please.

---

### Post by Rubi1200 on 2010-11-10
As the computer is booting hold down "Shift" to bring up the GRUB menu (if you do not see it already) and then try booting sda2 instead of sda1.

What result do you get?

---

### Post by oldfred on 2010-11-10
Just like Ubuntu runs a filecheck every 30 boots you should regularly run a chkdsk on your NTFS partitions:

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by samrat94 on 2010-11-10
> **Rubi1200 said:**
> As the computer is booting hold down "Shift" to bring up the GRUB menu (if you do not see it already) and then try booting sda2 instead of sda1.

What result do you get?

I tried booting into sda2 which is listed as Windows Recovery mode and it works fine; but isn't there a way to get the actual dual boot screen. sda1 doesn't even work, it opens up a prompt to restore the backup and just freezes. 

> Just like Ubuntu runs a filecheck every 30 boots you should regularly run a chkdsk on your NTFS partitions:

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/d....mspx?mfr=true]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true")

I also tried this. It took more than an hour,I think. But its of no use. 

Should I rather try uninstalling Ubuntu 10.10 and install 10.04? 10.04 was running so smoothly, now I think I shouldn't have upgraded at all.

---

### Post by oldfred on 2010-11-11
Did chkdsk report any errors? If so you have to rerun it until no errors are reported as it does not fix everything on one pass.

What other errors are you still having?

I typically do not upgrade anymore but have 3 20GB root partitions. I keep my old install, the current install and the next beta install. I only then switch when the new install fully works & is configured the way I want it. Most of my data is in a /data partition I mount in all three & some but not neccessarily all of /home hidden settings I copy from one to the next.

---

### Post by samrat94 on 2010-11-11
Hi oldfred,
No chkdsk showed no errors. Just to let you know, I am back on my wubi install now. However, the boot is still slow and it shows an error for some time which displays "no wubildr". Do you know how to fix it?? Thanks for your help.

---

### Post by oldfred on 2010-11-12
I am not familiar with wubi.

Do it show the no wubildr and then eventually boot into Ubuntu?

Have you checked the logs in system, administration log file viewer. I usually look at messages first, but check most of the logs just to see what is reported. Repeat entries where it tries and then gives up or long times between entries are things to review.

---

### Post by samrat94 on 2010-11-12
Yes, it boots after showing the error message. 

I haven't checked any log files; I've no idea why the error showed up in the first place.

---

### Post by bcbc on 2010-11-12
Generally you get the 'no wubildr' message if the wubildr file isn't on the windows boot partition. This can happen if you have a special boot partition (like win7 does these days). I don't see that setup in your bootinfoscript results, but you can check and see where the wubildr file is and copy it to the boot partition if required.

---


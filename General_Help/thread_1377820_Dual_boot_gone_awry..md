---
title: "Dual boot gone awry."
date: 2010-01-10
forum: General Help
---

### Post by venividibitchy on 2010-01-10
I installed Ubuntu as a dual-boot system with Windows XP very carefully. Unfortunately, though given the option to boot Windows at the grub menu, when I select it, I get an error. Booting Ubuntu on my other partition works just fine, no issues.

I also attempted to access files from the first partition in Ubuntu using gparted, but once I mounted it, all of my files were not present. I only saw manufacturer files, and many files and folders I didn't recognize.

What could've happened? Is all hope lost?

Also, as an aside, my laptop monitor is suffering from occasional black-outs during use. Ubuntu gave me a little toolbar flag, telling me to go to a website and use the patches given to fix it, but I'm not quite so sure where to input the given patch text. Do I really need to go through the trouble of finding the source code, etc., or is it more simple?

Your patience is appreciated.

---

### Post by Leppie on 2010-01-10
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by warfacegod on 2010-01-10
Ah! Leppie you beat me to it.

---

### Post by Leppie on 2010-01-10
> **warfacegod said:**
> Ah! Leppie you beat me to it.
trying to steal my beans? you addict... :P

---

### Post by warfacegod on 2010-01-10
Hi, my name is warfacegod, and I am a beanaholic.

---

### Post by Leppie on 2010-01-10
welcome warfacegod, my name is leppie and i am a beanaholic too :P

---

### Post by warfacegod on 2010-01-10
I started getting beans when I was young. I was okay with it for a while, you know, I could handle it. But then it ...(abject sobbing) it took on a life of it's own....

---

### Post by vinnywright on 2010-01-10
sound's like NTFS file system coruption.

if you have the xp cd boot it to recovery console and run chkdsk on it with the fix switch maby f maby p cant remember

or install ntfsprogs and run ntfsfix on it 

VINNY

---

### Post by warfacegod on 2010-01-10
> **vinnywright said:**
> sound's like NTFS file system coruption.

if you have the xp cd boot it to recovery console and run chkdsk on it with the fix switch maby f maby p cant remember

or install ntfsprogs and run ntfsfix on it 

VINNY

Pretty sure it's f

---

### Post by venividibitchy on 2010-01-12
> **Leppie said:**
> could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

I downloaded it, but am having troubles running the script.

I tried "sudo bash boot_info_script048.sh" to no avail. It says there's no file with that name.

Do I have to place the file somewhere special? It's on my desktop now.

Forgive the ignorance -- still learning.

---

### Post by michy99 on 2010-01-12
You need to make it executable.```
sudo chmod +x boot_info_script048.sh
```

---

### Post by venividibitchy on 2010-01-12
> **michy99 said:**
> You need to make it executable.```
sudo chmod +x boot_info_script048.sh
```

chmod: cannot access `boot_info_script048.sh': No such file or directory

---

### Post by Leppie on 2010-01-12
this should work:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by venividibitchy on 2010-01-13
> **Leppie said:**
> this should work:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

Perfect, thanks.

Here's the results (I included only what I thought was pertinent):

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x308ebecd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    10,506,509    10,506,447  12 Compaq diagnostics
/dev/sda2          10,506,510   156,296,384   145,789,875   5 Extended
/dev/sda5          10,506,573   156,007,214   145,500,642  83 Linux
/dev/sda6         156,007,278   156,296,384       289,107  82 Linux swap / Solaris

---

### Post by Leppie on 2010-01-13
> **venividibitchy said:**
> Here's the results (I included only what I thought was pertinent)
<snip>
post the complete output

---

### Post by venividibitchy on 2010-01-13
> **Leppie said:**
> <snip>
post the complete output

<snip>


============================= Boot Info Summary: ==============================

 ```
=> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x308ebecd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    10,506,509    10,506,447  12 Compaq diagnostics
/dev/sda2          10,506,510   156,296,384   145,789,875   5 Extended
/dev/sda5          10,506,573   156,007,214   145,500,642  83 Linux
/dev/sda6         156,007,278   156,296,384       289,107  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="220CFF700CFF3D7B" TYPE="ntfs" 
/dev/sda5: UUID="171f1c5f-3649-44d2-b227-b9efe08deef5" TYPE="ext4" 
/dev/sda6: UUID="ebb7fe83-481f-4e80-9fd2-ffb5f78cfd4e" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/paiboddum/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paiboddum)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 171f1c5f-3649-44d2-b227-b9efe08deef5
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 171f1c5f-3649-44d2-b227-b9efe08deef5
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=171f1c5f-3649-44d2-b227-b9efe08deef5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 171f1c5f-3649-44d2-b227-b9efe08deef5
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=171f1c5f-3649-44d2-b227-b9efe08deef5 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 171f1c5f-3649-44d2-b227-b9efe08deef5
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=171f1c5f-3649-44d2-b227-b9efe08deef5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 171f1c5f-3649-44d2-b227-b9efe08deef5
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=171f1c5f-3649-44d2-b227-b9efe08deef5 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 171f1c5f-3649-44d2-b227-b9efe08deef5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=171f1c5f-3649-44d2-b227-b9efe08deef5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 171f1c5f-3649-44d2-b227-b9efe08deef5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=171f1c5f-3649-44d2-b227-b9efe08deef5 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 220cff700cff3d7b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=171f1c5f-3649-44d2-b227-b9efe08deef5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ebb7fe83-481f-4e80-9fd2-ffb5f78cfd4e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   5.3GB: boot/grub/core.img
   5.3GB: boot/grub/grub.cfg
   5.3GB: boot/initrd.img-2.6.31-14-generic
   5.3GB: boot/initrd.img-2.6.31-16-generic
   5.3GB: boot/initrd.img-2.6.31-17-generic
   5.3GB: boot/vmlinuz-2.6.31-14-generic
   5.3GB: boot/vmlinuz-2.6.31-16-generic
   5.3GB: boot/vmlinuz-2.6.31-17-generic
   5.3GB: initrd.img
   5.3GB: initrd.img.old
   5.3GB: vmlinuz
   5.3GB: vmlinuz.old
```

---

### Post by Leppie on 2010-01-13
> **venividibitchy said:**
> Copping an attitude doesn't help anybody.
being a wise-a... when asking for help does???
if i wanted reduced output, i would've asked for it...
you do not seem to know what to do with a script, but you know which parts of the output file will help diagnose your issue?

---

### Post by Leppie on 2010-01-13
After analysing the results, it appears the entry you have in the grub menu is the compaq diagnostic tools.
It looks like you deleted your windows partition and put the ubuntu partions in the space freed up by removing the windows partition.

---

### Post by venividibitchy on 2010-01-13
> **Leppie said:**
> After analysing the results, it appears the entry you have in the grub menu is the compaq diagnostic tools.
It looks like you deleted your windows partition and put the ubuntu partions in the space freed up by removing the windows partition.

How could that have happened, when I was not given any remove-partition/reformat partition, etc. warnings or flash screens? Why would the actual grub menu that's visible still say "Windows XP"? And how could Compaq Diagnostics take up so much space? I don't even have a Compaq.

---

### Post by Leppie on 2010-01-13
> **venividibitchy said:**
> How could that have happened, when I was not given any remove-partition/reformat partition, etc.
i don't know how this could've happened.

> **venividibitchy said:**
> warnings or flash screens? Why would the actual grub menu that's visible still say "Windows XP"?
the actual menu entry is: Windows NT/2000/XP (on /dev/sda1)
windows xp in the results generated by the script only refers to the boot loader type.

> **venividibitchy said:**
> And how could Compaq Diagnostics take up so much space? I don't even have a Compaq.
it's not a very large partition, around 5gb. also the fact that you stated that there's only a bunch of manufacturer's files, would be an indication that it's not a normal operating system but something like a restore/recovery partition.

---


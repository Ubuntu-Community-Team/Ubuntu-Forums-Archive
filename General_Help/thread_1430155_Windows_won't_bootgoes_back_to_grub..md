---
title: "Windows won't boot/goes back to grub."
date: 2010-03-15
forum: General Help
---

### Post by BrinnieSmith on 2010-03-15
Hello, 
I have an Acer Aspire 5810T which came with Windows Vista. I prefer Ubuntu but I need some windows applications so I dual-booted Vista and 9.10.

There was a few minor problems with the Vista side but I didn't use it enough to care. A few weeks ago Vista would not open some programs and others would shut down automaticly and some would open but not connect to the internet like they should. This happened on my previous laptop and when I used the system recovery discs to restore the computer all those issues were gone. 

I used the recover discs to restore everything to its original factory settings, it said everything was successful so I restarted. My computer got to the grub menu but when I chose Windows Vista as my operating system it goes black for half a second then returns to the grub menu. 

I can get into Ubuntu fine, and I can see the Vista files when I mount the drive to Ubuntu. When I look at the files everything is the way it should be if I had restored it but I can't boot it... 

I would appreciate any help anyone can give me on how to get the windows portion to load again. I was also thinking of just getting rid of Vista altogether, but would I be able to install Windows 7 if I need to?(which I probably do)

Thanks! (sorry for the long post ;D)

---

### Post by l4zy on 2010-03-15
Use live cd and reinstall / make shure that grub points to right place.

---

### Post by coffeecat on 2010-03-15
> **l4zy said:**
> Use live cd and reinstall / make shure that grub points to right place.

@BrinnieSmith, I'm sure you don't want to do that. I'm sure we can repair whatever has gone wrong.

Some thoughts:

Possibly the Vista recovery wasn't successful, or there's a corruption somewhere despite the successful recovery message. Or possibly the Vista recovery changed the UUID of the Vista C: partition, although if that was the case I would expect a grub error rather than a blak screen. Whatever, let's get some basic information.

Download the boot info script from:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Once downloaded, move it to your desktop and run it (from a terminal) with:

```
sudo bash ~/Desktop/boot_info_script*.sh
```That will give you a RESULTS.TXT file on the desktop. Post the contents of the file. When you post it, please enclose it in [noparse]```

```[/noparse] tags or highlight the text and click on the # sign on the toolbar.

The other thing to do to see if Vista is actually bootable (to exclude a problem in the Vista restore) is to download SuperGrubDisk from here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Burn a CD and boot up with it. There is an option in its menu to boot into Windows. Be careful - there are two Windows options. One of them boots into Windows but repairs the Windows MBR as well. If you choose this, you'll overwrite grub stage 1 and have a machine which can only boot into Windows - or not boot into anything at all if Vista is broken. It wouldn't be a disaster, just an inconvenience, because grub is easily repaired, but best avoided.

---

### Post by BrinnieSmith on 2010-03-15
Thanks coffeecat, here is what the file said:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 507395178 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

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

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x47dbc8a1

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  27 Hidden HPFS/NTFS
/dev/sda2    *     20,482,048   476,076,023   455,593,976   7 HPFS/NTFS
/dev/sda3         476,086,275   625,137,344   149,051,070   5 Extended
/dev/sda5         476,086,338   618,968,384   142,882,047  83 Linux
/dev/sda6         618,968,448   625,137,344     6,168,897  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        EAEE-EB49                              vfat       PQSERVICE                     
/dev/sda2        4836770D3676FAF0                       ntfs       ACER                          
/dev/sda5        7bf7523a-c1c2-4a0c-b22d-9de5c53c1219   ext4                                     
/dev/sda6        a9129a6f-8077-454a-9442-c5a269835412   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 7bf7523a-c1c2-4a0c-b22d-9de5c53c1219
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 7bf7523a-c1c2-4a0c-b22d-9de5c53c1219
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=7bf7523a-c1c2-4a0c-b22d-9de5c53c1219 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 7bf7523a-c1c2-4a0c-b22d-9de5c53c1219
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=7bf7523a-c1c2-4a0c-b22d-9de5c53c1219 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 7bf7523a-c1c2-4a0c-b22d-9de5c53c1219
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=7bf7523a-c1c2-4a0c-b22d-9de5c53c1219 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 7bf7523a-c1c2-4a0c-b22d-9de5c53c1219
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=7bf7523a-c1c2-4a0c-b22d-9de5c53c1219 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 7bf7523a-c1c2-4a0c-b22d-9de5c53c1219
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7bf7523a-c1c2-4a0c-b22d-9de5c53c1219 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 7bf7523a-c1c2-4a0c-b22d-9de5c53c1219
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7bf7523a-c1c2-4a0c-b22d-9de5c53c1219 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set eaee-eb49
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 4836770d3676faf0
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
UUID=7bf7523a-c1c2-4a0c-b22d-9de5c53c1219 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a9129a6f-8077-454a-9442-c5a269835412 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 247.8GB: boot/grub/core.img
 245.3GB: boot/grub/grub.cfg
 244.1GB: boot/initrd.img-2.6.31-14-generic
 244.2GB: boot/initrd.img-2.6.31-17-generic
 245.3GB: boot/initrd.img-2.6.31-19-generic
 244.1GB: boot/vmlinuz-2.6.31-14-generic
 244.1GB: boot/vmlinuz-2.6.31-17-generic
 244.4GB: boot/vmlinuz-2.6.31-19-generic
 245.3GB: initrd.img
 244.2GB: initrd.img.old
 244.4GB: vmlinuz
 244.1GB: vmlinuz.old
```

---

### Post by coffeecat on 2010-03-15
To be honest, I'm puzzled. This bit seems wrong:

> **BrinnieSmith said:**
> 

```

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 507395178 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
```

You've got bits of grub in the boot sector of the Vista partition. Compare this with my Vista partition:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
```Questions: 

Is sda1 a recovery partition or a boot partition for Vista?

According to your grub.cfg, you will have Vista entries for both sda1 and sda2. Which are you trying to boot from? What happens when you try to boot from the other?

After you ran the restore from the recovery discs, did you do anything before you tried to boot into Vista from the grub menu? Such as a terminal grub command?

As far as I can see those bits of grub have no place in the Vista partition and are replacing the Vista boot sector. Which would explain why Vista is not booting, but I am at a loss to understand how they got there.

I'm afraid it's late now and I have to log off. I'll think about this and come back to this thread tomorrow. Hopefully, someone else may come in and see what I may have missed.

---

### Post by BrinnieSmith on 2010-03-15
> Is sda1 a recovery partition or a boot partition for Vista?

According to your grub.cfg, you will have Vista entries for both sda1 and sda2. Which are you trying to boot from? What happens when you try to boot from the other?

After you ran the restore from the recovery discs, did you do anything before you tried to boot into Vista from the grub menu? Such as a terminal grub command?

As far as I can see those bits of grub have no place in the Vista partition and are replacing the Vista boot sector. Which would explain why Vista is not booting, but I am at a loss to understand how they got there.


sda1 is a recovery partition, when it was working I always booted from sda2. 
If I try sda1 it will say "searching for files" or something like that then go back to the grub menu. 

After I ran the restore I tried to boot Vista. 
I did do a few grub commands, one to find out which version of grub I had and some others but they all said "command not found" so I assumed they didn't do anything and nothing changed after I did them. 

Is there a way to get the bits of grub out of the Vista partition? 

And thank you for all your help! I appreciate it. :)

---

### Post by coffeecat on 2010-03-16
I've had some thinking time now, so..

First thing. Don't bother with SuperGrubDisk (my first post). This won't help in this situation. 

It may be that one of the grub commands you tried after you found Vista to be unbootable installed grub to the boot sector of the Vista partition, but that's all a bit theoretical now. If so, it would mean that there was another problem making Vista unbootable apart from the overwritten boot sector. Which would suggest that the recovery DVD is faulty.

The limited experience I have of Windows OEM recovery partitions is that they will boot from grub, but this one might be different. One option might be to boot into the recovery partition using whatever magic key Acer uses and try another Vista partition restore from that.

The second option is to use a Vista recovery CD to try to repair Vista. I know you don't have one, unless you can borrow a "proper" Microsoft Vista install DVD from someone. If you boot from a Microsoft DVD, you can get into a repair console which the OEM image discs don't have. If you can't borrow a DVD, you can download a recovery disc CD ISO from here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

That contains just the recovery console part of the installation DVD, which is why you can fit it on a CD.

Alternatively, if you're feeling adventurous and you have a friend you doesn't mind you doing a bit of (benign) hacking of their Vista, you can create a recovery disc from Vista using this method:

[http://www.istartedsomething.com/20080324/recover-create-a-recovery-disc-vista-sp1-rtm/](http://www.istartedsomething.com/20080324/recover-create-a-recovery-disc-vista-sp1-rtm/)

I've done this successfully. It's not difficult. It's strange that MS chose to disable this feature in the final SP1 because this facility is available in Windows 7. (Ours is not to reason why. :rolleyes:)

When you boot up from the recovery disc, at the first menu choose the recovery/repair option (clearly the installation choice won't work). Then you are presented with the menu shown in the fourth screenshot here:

[http://www.istartedsomething.com/20070929/vista-sp1-recovery-disc/](http://www.istartedsomething.com/20070929/vista-sp1-recovery-disc/)

If you choose the first option - Startup Repair - I'm hoping (but can't be sure) that that will repair the borked boot sector and will repair any other problems it finds. It's worth a shot anyway. Problem is, it will probably rewrite the Windows MBR to the MBR of the hard disc, overwriting grub stage 1 in the process. Which mean that you'll either get a system that will only boot into Windows or, if it doesn't manage to repair Vista properly, that won't boot at all.

If that happens, boot into your Karmic live CD, open a terminal and:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```Then try a reboot. You shouldn't need to refresh the grub menu, but if anything is awry, open a terminal (in your hard drive installed Ubuntu) and:

```
sudo update-grub
```Good luck. Do post back if anything is not clear. And the final, final option if the Vista repair disc doesn't work and booting into the recovery partition doesn't work is to approach Acer. They (probably) will sell you a recovery DVD but they will charge you for it.

---

### Post by coffeecat on 2010-03-16
Just to add what I've posted.

If you get yourself the Vista recovery disc and the "Startup Repair" doesn't do the job, you can use various commands from the command prompt.

Here's a link which explains all:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I should imagine that 'fixboot' is the one to go for. Don't do 'fixmbr'. That's the one that overwrites grub stage 1 in the mbr so that you won't be able to boot into Ubuntu.

---

### Post by BrinnieSmith on 2010-03-24
Thank you so very very much coffeecat! The /fixboot worked perfectly and I can boot into Windows and Ubuntu just fine :) 

Thanks again!!:p

---

### Post by coffeecat on 2010-03-24
I'm glad to hear it. Congratulations!

Interestingly, I came across a thread a couple of days ago where someone couldn't boot into XP after upgrading Ubuntu to 10.04. Their boot script showed...

```

Boot sector type:  Grub 2
Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                   looks at sector 1881763251 of the same hard drive for 
                   core.img, but core.img can not be found at this 
                   location. No errors found in the Boot Parameter Block.
```... in their Windows C:\ partition, and I thought, "Hmmm. Looks familiar...." :-k

You are not alone! :p

FIXBOOT fixed their boot as well.

---


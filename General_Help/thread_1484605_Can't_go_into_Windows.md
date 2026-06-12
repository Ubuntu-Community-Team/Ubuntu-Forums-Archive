---
title: "Can't go into Windows"
date: 2010-05-15
forum: General Help
---

### Post by NTHQ on 2010-05-15
My computer is dual-booting Windows 7 and Ubuntu. I just upgraded to 10.04 through the Update Manager and now I can't go into Windows anymore. When GRUB loads, I have the option to choose which OS I want to load but when I choose Windows, GRUB just keeps reloading. Can someone help me fix this?

---

### Post by demosthenese on 2010-05-15
Do you have os-prober installed? This helps grub2 find other operating systems.

---

### Post by NTHQ on 2010-05-15
Yup. According to Synaptic it's there.

---

### Post by wilee-nilee on 2010-05-15
> **NTHQ said:**
> My computer is dual-booting Windows 7 and Ubuntu. I just upgraded to 10.04 through the Update Manager and now I can't go into Windows anymore. When GRUB loads, I have the option to choose which OS I want to load but when I choose Windows, GRUB just keeps reloading. Can someone help me fix this?

When you say I can't go into windows do you mean boot or access via the home bookmarks. If it is can't boot then, post this boot script, in code tags; which means in the reply highlight the text and click on the # in the reply panel.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by NTHQ on 2010-05-15
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 314865532 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 314865532 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 314865532 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 314865532 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 314865532 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,712,509   209,712,447   7 HPFS/NTFS
/dev/sda2         209,712,510   314,568,764   104,856,255  83 Linux
/dev/sda3         314,568,765   339,742,619    25,173,855   5 Extended
/dev/sda5         314,568,828   335,533,589    20,964,762  83 Linux
/dev/sda6         335,533,653   339,742,619     4,208,967  82 Linux swap / Solaris
/dev/sda4         339,742,620   625,137,344   285,394,725   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,948,282,874 1,948,282,812   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1DEAABA075FBBE51                       ntfs       Windows                       
/dev/sda2        75b23c41-3f8f-4c24-9646-1bc164ded7dc   ext4       /home                         
/dev/sda3: PTTYPE="dos" 
/dev/sda4        213D0AD31E81BE62                       ntfs                                     
/dev/sda5        7ee7a3dd-4a81-42b6-8920-78ff027ef4ba   ext4                                     
/dev/sda6        57687a19-39d9-4da9-8c78-d481c9be15b8   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6056E06456E03D02                       ntfs       My Book                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home                    ext4       (rw)
/dev/sda4        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/My Book_          fuseblk    (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7ee7a3dd-4a81-42b6-8920-78ff027ef4ba
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7ee7a3dd-4a81-42b6-8920-78ff027ef4ba
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ee7a3dd-4a81-42b6-8920-78ff027ef4ba
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7ee7a3dd-4a81-42b6-8920-78ff027ef4ba ro vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ee7a3dd-4a81-42b6-8920-78ff027ef4ba
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7ee7a3dd-4a81-42b6-8920-78ff027ef4ba ro single vga=792
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ee7a3dd-4a81-42b6-8920-78ff027ef4ba
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=7ee7a3dd-4a81-42b6-8920-78ff027ef4ba ro vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ee7a3dd-4a81-42b6-8920-78ff027ef4ba
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=7ee7a3dd-4a81-42b6-8920-78ff027ef4ba ro single vga=792
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ee7a3dd-4a81-42b6-8920-78ff027ef4ba
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ee7a3dd-4a81-42b6-8920-78ff027ef4ba
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1deaaba075fbbe51
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
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=7ee7a3dd-4a81-42b6-8920-78ff027ef4ba / ext4 errors=remount-ro 0 1
# Entry for /dev/sda2 :
UUID=75b23c41-3f8f-4c24-9646-1bc164ded7dc /home ext4 defaults 0 2
# Entry for /dev/sda6 :
UUID=57687a19-39d9-4da9-8c78-d481c9be15b8 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda4 /media/Data ntfs-3g defaults,locale=en_CA.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 161.2GB: boot/grub/core.img
 162.0GB: boot/grub/grub.cfg
 167.4GB: boot/initrd.img-2.6.31-21-generic
 168.0GB: boot/initrd.img-2.6.32-22-generic
 166.6GB: boot/vmlinuz-2.6.31-21-generic
 168.9GB: boot/vmlinuz-2.6.32-22-generic
 168.0GB: initrd.img
 167.4GB: initrd.img.old
 168.9GB: vmlinuz
 166.6GB: vmlinuz.old

```

---

### Post by wilee-nilee on 2010-05-16
So what I see if you look at the script is grub installed in windows basically. Grub only basically should be in the master boot record. So I will let the experts advise you on this there are a handful of other users who are very good at this. So for the mean time, this can be fixed, but do not do it without a definitive answer, don't try to fix this your self.

So other posters don't post a answer unless your absolutely sure of it's validity.

---

### Post by NTHQ on 2010-05-16
> **wilee-nilee said:**
> So what I see if you look at the script is grub installed in windows basically. Grub only basically should be in the master boot record. So I will let the experts advise you on this there are a handful of other users who are very good at this. So for the mean time, this can be fixed, but do not do it without a definitive answer, don't try to fix this your self.

So other posters don't post a answer unless your absolutely sure of it's validity.

Thank you.

---

### Post by wilee-nilee on 2010-05-16
bump

---

### Post by NTHQ on 2010-05-17
*BUMP*
Really need help here. :(

---

### Post by moon_raker on 2010-05-17
Could be that this thread will be of help : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Or: [http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

---

### Post by NTHQ on 2010-05-17
> **moon_raker said:**
> Could be that this thread will be of help : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Or: [http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)
Thanks. I'll look into it.

---

### Post by wilee-nilee on 2010-05-17
> **moon_raker said:**
> Could be that this thread will be of help : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Or: [http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

That thread will do no good, please do not post help your not sure of.

---

### Post by ranch hand on 2010-05-17
I am, by no means, an expert on MS boot problems.

wilee-nilee has it right when he points out that your MS boot is pretty much screwed due to grub being there where it has no business at all.

You, I hope, have an install disc for MS.  If you do, I know you can repair the boot sector from there.

This will, of coarse, put the MS boot loader back in the boot sector and on the MBR.  This will mean that you must fix Grub using these directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

One thing that you might do before that is;
```

sudo grub-install /dev/sda

```
I am sure it will not do any good but it won't hurt any thing either.

---

### Post by NTHQ on 2010-05-17
> **ranch hand said:**
> I am, by no means, an expert on MS boot problems.

wilee-nilee has it right when he points out that your MS boot is pretty much screwed due to grub being there where it has no business at all.

You, I hope, have an install disc for MS.  If you do, I know you can repair the boot sector from there.

This will, of coarse, put the MS boot loader back in the boot sector and on the MBR.  This will mean that you must fix Grub using these directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

One thing that you might do before that is;
```

sudo grub-install /dev/sda

```I am sure it will not do any good but it won't hurt any thing either.
If I understand correctly, the Windows 7 install disk will be able to repair the Windows boot.
I am then to run the above command in a terminal prior to following the instructions from the link that you gave.
And this should put GRUB back to where it belongs, right?

---

### Post by ranch hand on 2010-05-17
No, I just stuck that in in case you want to run it first, before doing anything else.

I believe that all MS install disks are capable of that job.  I have not used one since W98.

The directions for repairing grub will have all the commands you need.  You can ignore the part about editing files as I think yours are all right.  All you really need is the grub-install command once you get to that stage.

You probably had an option during the upgrade that wanted to know where to install grub.  I am not sure but the default may be to just install it everywhere.  This is easy.  It is wrong.  It is a bug.

Having it installed on sda an sdb is alright.  Do not worry about it as you have nothing to boot there.

I am sure that if you run a search on these forums you will find info on MS boot sector repair.  I know you are not the only one that this has happened to.  Hopefully the install disk has some clue as to the commands to use.  I think the MS site should have something on it too.

---

### Post by todak on 2010-05-17
Try [this]("http://www.ehow.com/how_4836283_repair-mbr-windows.html") to get windows booting again then do [this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") to install grub2 and dual boot again.

---

### Post by NTHQ on 2010-05-17
> **ranch hand said:**
> No, I just stuck that in in case you want to run it first, before doing anything else.

I believe that all MS install disks are capable of that job.  I have not used one since W98.

The directions for repairing grub will have all the commands you need.  You can ignore the part about editing files as I think yours are all right.  All you really need is the grub-install command once you get to that stage.

You probably had an option during the upgrade that wanted to know where to install grub.  I am not sure but the default may be to just install it everywhere.  This is easy.  It is wrong.  It is a bug.

Having it installed on sda an sdb is alright.  Do not worry about it as you have nothing to boot there.

I am sure that if you run a search on these forums you will find info on MS boot sector repair.  I know you are not the only one that this has happened to.  Hopefully the install disk has some clue as to the commands to use.  I think the MS site should have something on it too.
As a matter of fact, it did ask me where to install GRUB. When I clicked on the help button, it told that if I didn't know where, then I should just select all the drives... I knew that was a bad idea... :(

---

### Post by ranch hand on 2010-05-17
> **todak said:**
> Try [this]("http://www.ehow.com/how_4836283_repair-mbr-windows.html") to get windows booting again then do [this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") to install grub2 and dual boot again.
If you look at the boot script the problem is not in his grub files or the MBR.

The problem is that when grub was installed on the MBR  of sda, it was also installed on the MS boot sector which is not the MBR.  That is where the files that need fixed are.

The link I gave for recovering grub is what he needs to use.  There is nothing wrong with the grub on his Ubuntu install.  You can see that on the boot script.

That is why the boot script is needed ANY time there is a boot problem.  Guessing is great fun but the results of it is not.

---

### Post by todak on 2010-05-17
> **ranch hand said:**
> If you look at the boot script the problem is not in his grub files or the MBR.

The problem is that when grub was installed on the MBR  of sda, it was also installed on the MS boot sector which is not the MBR.  That is where the files that need fixed are.

The link I gave for recovering grub is what he needs to use.  There is nothing wrong with the grub on his Ubuntu install.  You can see that on the boot script.

That is why the boot script is needed ANY time there is a boot problem.  Guessing is great fun but the results of it is not.
 The *bootsect /nt60 C:\* command from my first link modifies the **Boot Sector** in Win7 NOT the MBR.

---

### Post by wilee-nilee on 2010-05-18
> **ranch hand said:**
> 
That is why the boot script is needed ANY time there is a boot problem.  Guessing is great fun but the results of it is not.

This is the truth, we all want to help, but we have to consider whether our help is going to make things worse, and have the thread starter lose the whole kit and kaboodle. There is a reason why in ethics that you learn to **_do no harm_**.

---

### Post by wilee-nilee on 2010-05-18
> **todak said:**
> The *bootsect /nt60 C:\* command from my first link modifies the **Boot Sector** in Win7 NOT the MBR.

I have yet to see the auto repair mode dislodge grub, and you didn't specify the use of that page. If a specific command needs to be run then post it, don't come back later and try and defend yourself.

And by the way ranch hand has helped 100's of people with boot problems, and is well respected.

---

### Post by todak on 2010-05-18
> **wilee-nilee said:**
> I have yet to see the auto repair mode dislodge grub, and you didn't specify the use of that page. If a specific command needs to be run then post it, don't come back later and try and defend yourself.

And by the way ranch hand has helped 100's of people with boot problems, and is well respected.

 Yes I DID specify the use of the page. Perhaps you did not see the link contained in my first post in this thread, or if you did, then you did not read the page at all. I am not defending myself, I am clarifying for those who DO NOT or REFUSE to understand. Why on earth, if you do not understand the process, do you tell me I am wrong? I have used the process I have described, many times for my friends who dual-boot, so that is why I post the information, because it works for me. Perhaps you can enlighten us with your knowledge and explain why I am wrong, so that others may learn from my mistake.

---

### Post by ranch hand on 2010-05-18
I do not want this to become uncivil here.  We are here to help.

I have no argument with anything anyone says about repairing MS.  I just do not know, nor frankly wish to know.

I do have a problem with the link for then fixing grub.  Grub does not need fixed.  It needs reinstalled on the MBR once MS is repaired.

The boot sector needs fixed in MS.  however this is done will install it on the MBR.

Thus, grub will need reinstalling there.  That is all grub needs.

Now, that said, someone with knowledge of what the W7 menu entry should look like might want to take a look at that and check to see if it is right.  I do think it is but, as I say, I do not know.

---

### Post by NTHQ on 2010-05-19
The Windows 7 disk can't repair it... It doesn't even detect anything wrong with it...
It return 0 errors... :(

---

### Post by ryan858 on 2010-05-19
Is there a way to force it to reinstall the boot sector?

---

### Post by ranch hand on 2010-05-19
> **NTHQ said:**
> The Windows 7 disk can't repair it... It doesn't even detect anything wrong with it...
It return 0 errors... :(
This, I hope is a good thing.

However, there is a command (I am sure) to repair boot or some such thing that will not need to fix anything in in your boot sector but will install MS bootloader on the MBR.  I would do that and then see if it will boot (Ubuntu won't).

If MS will not boot, try to repair the boot sector again.

If it does boot then you need to go by these instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

ignoring the edit files part, yours are great.  In fact I would save a copy of your /boot/grub/grub.cfg file just in case you need a copy of that menu entry for MS.

Good luck with the MS bootloader.  Their command line is not a powerful tool and I do not believe it is that reliable.  I really do not know though so maybe someone can jump in here and correct me and maybe head you in the right direction for fixing it.

---

### Post by john newbuntu on 2010-05-20
Look into this last post by wee to fix the MBR/PBR if auto repair does not work.  I have tried this on Vista but haven't tried on win7.  
[http://www.sevenforums.com/installation-setup/81425-need-help-starting-windows-7-boot-up-6.html](http://www.sevenforums.com/installation-setup/81425-need-help-starting-windows-7-boot-up-6.html)
You can skip running "bootrec.exe /fixmbr" initially and see if it retains grub in MBR.

---

### Post by ranch hand on 2010-05-20
Well, I do not know about the OP but I am glad you dropped in with that little tid bit.

Looks good to me.  Thanks a bunch.

---

### Post by Elie-M on 2010-05-20
sorry I didn't read all the thread answers (i'm at work) but have you tried sudo update-grub?

cz many users suffered that after update to 10.04 and update-grub fixed it.

---

### Post by dez93_2000 on 2010-05-20
Hi all, apologies for asking almost the same question but i'd like to be sure before i begin:

i've got the same problem with XP; drives & partitions are:
drive 1 partition 1 winXP
drive 2 partition 1 ubuntu
drive 3 partition 1 winXP (another old safe install)
drive 4 partition 1 ntfs files.

My boot info script reads thus:

"sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 272191 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 272191 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 272191 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM"



Oddly it spits the same error message for the ubuntu install as the winXPs, but ubuntu boots (thank Aetheismo!).

As i understand it from the (sometimes disagreeing) posts, i should follow section 3 of the page posted by moon raker: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) to restore XPs bootloader. This will affect the MBR? And i then need to reinstall grub2? Which i do via ranch hand's link : [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")
This will reinstall grub to the MBR, which will then recognise ubuntu again (after the windows restore killed it?) AND the XP installs...?

Help/clarification very much appreciated. It surprises me that this is this hard! I figured that if i've accidentally (as per bug explained by Ranch Hand) installed grub to the partitions rather than the MBRs of the drive, that there isn't a way to just put it right. Ubuntu seems to know where the partitions and boot loaders are on each drive...
[edit: something like this: [http://forums.techguy.org/7369116-post6.html](http://forums.techguy.org/7369116-post6.html)]

cheers all.

---

### Post by ranch hand on 2010-05-20
It would be best if we have the whole boot inf script report.

Please type [] with code between the brackets on the line before you paste the report.

Please type [] with /code between the brackets on the line after your pasted report.

---

### Post by dez93_2000 on 2010-05-20
gladly, sir.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 272191 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 272191 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 272191 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 272191 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,719,869   976,719,807   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   964,703,249   964,703,187  83 Linux
/dev/sdb2         964,703,250   976,768,064    12,064,815   5 Extended
/dev/sdb5         964,703,313   976,768,064    12,064,752  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   156,344,579   156,344,517   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   241,248,104   241,248,042   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8E3CDEC53CDEA80B                       ntfs       SamsungA                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9dcff44a-8d21-42c6-978c-a3685b520855   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        79c91a3a-979a-411f-a192-d1e44c7d37f6   swap                                     
/dev/sdb                                                jmicron_raid_member                               
/dev/sdc1        82A47E73A47E6A15                       ntfs       80gb OldC                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        F0F02DA2F02D6FD0                       ntfs       120gb AltBoot                 
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/SamsungA          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1        /media/120gb AltBoot     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/80gb OldC         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=simon)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 9dcff44a-8d21-42c6-978c-a3685b520855
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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 9dcff44a-8d21-42c6-978c-a3685b520855
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9dcff44a-8d21-42c6-978c-a3685b520855
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=9dcff44a-8d21-42c6-978c-a3685b520855 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9dcff44a-8d21-42c6-978c-a3685b520855
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=9dcff44a-8d21-42c6-978c-a3685b520855 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9dcff44a-8d21-42c6-978c-a3685b520855
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=9dcff44a-8d21-42c6-978c-a3685b520855 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9dcff44a-8d21-42c6-978c-a3685b520855
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=9dcff44a-8d21-42c6-978c-a3685b520855 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9dcff44a-8d21-42c6-978c-a3685b520855
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9dcff44a-8d21-42c6-978c-a3685b520855
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8e3cdec53cdea80b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 82a47e73a47e6a15
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=9dcff44a-8d21-42c6-978c-a3685b520855 / ext4 errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=79c91a3a-979a-411f-a192-d1e44c7d37f6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdd1 /media/120gb\040AltBoot ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdc1 /media/80gb\040OldC ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda1 /media/SamsungA ntfs-3g defaults,locale=en_GB.UTF-8 0 0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
 125.0GB: boot/grub/grub.cfg
   3.3GB: boot/initrd.img-2.6.31-21-generic
   3.2GB: boot/initrd.img-2.6.32-22-generic
   2.0GB: boot/vmlinuz-2.6.31-21-generic
   2.0GB: boot/vmlinuz-2.6.32-22-generic
   3.2GB: initrd.img
   3.3GB: initrd.img.old
   2.0GB: vmlinuz
   2.0GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

gracias.

---

### Post by ranch hand on 2010-05-20
That is what we needed.

The good news is that we can see what the problem is.

The bad news is that grub has been installed on your MS boot sector.  I truly hope you have an install disk.

I suspect when you installed Ubuntu there was a question about where to install grub.  It probably had the message "if you are not sure choose all".  This is bad.  It is a bug.

Grub should have been installed on all the drives MBRs (sda, sdb and so forth) it should not have been installed anywhere else.

Your MS boot sector is where the MS boot loader is supposed to be to boot MS.

What you need to do is repair that boot sector using your MS install disk.  This should also install MS boot on the MBR.

You will then need to restore grub to the boot sectors of the drives.  This is the instructions to follow for that;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

As I do not allow MS stuff in the house I am not much help fixing that.  I know the tools are on the install disk.  There are directions on the MS site for that I am sure.

If you have the choice of auto repair or a CLI (command line) repair, use the CLI as it is more robust.

---

### Post by Darkness Des on 2010-05-20
That is all well and good, but you are honestly making it MUCH harder than it needs to be. Install testdisk (it's in the Repositories) and then follow the instructions in the attached .txt file. I had the EXACT, and I mean EXACT, same problem less than 24 hours ago. This fixed it. It was ridiculously easy and fixed me up immediately. What it does is restore the old boot sector back to where Grub is currently installed on /dev/sda. You may have to reinstall Grub to where you have Ubuntu installed, but this was not the case for me. Simple as that.

---

### Post by ranch hand on 2010-05-20
Now that is neat.  I used to have MS and had to repair the boot a couple of times when it was the only thing on the drive.

I was never impressed with the app on the disk.

I have used test disk.  It is a great tool.  Never realized it would do windows too.

Thanks for that.  I will keep and treasure the attachment, by the way, for future reference.

---

### Post by dez93_2000 on 2010-05-21
Des & Ranch - many thanks indeed. Assuming that this doesn't wipe my system / set my PC on fire / kick me in the nuts, then i'm indebted to you.

Cheers!

---

### Post by NTHQ on 2010-05-22
> **john newbuntu said:**
> Look into this last post by wee to fix the MBR/PBR if auto repair does not work.  I have tried this on Vista but haven't tried on win7.  
[http://www.sevenforums.com/installation-setup/81425-need-help-starting-windows-7-boot-up-6.html](http://www.sevenforums.com/installation-setup/81425-need-help-starting-windows-7-boot-up-6.html)
You can skip running "bootrec.exe /fixmbr" initially and see if it retains grub in MBR.
I just followed those instructions and now everything is back to normal!
Thank you everyone who has contributed their help. I appreciate it very much. :P

---

### Post by ranch hand on 2010-05-22
> **NTHQ said:**
> I just followed those instructions and now everything is back to normal!
Thank you everyone who has contributed their help. I appreciate it very much. :P
My big question is did you

"You can skip running "bootrec.exe /fixmbr" initially and see if it retains grub in MBR."

or not?  If so, did it work that way?

If not, what did you do exactly?  Those of that are MS free should probably know these things.

---

### Post by NTHQ on 2010-05-22
> **ranch hand said:**
> My big question is did you

"You can skip running "bootrec.exe /fixmbr" initially and see if it retains grub in MBR."

or not?  If so, did it work that way?

If not, what did you do exactly?  Those of that are MS free should probably know these things.
Yea I skipped that command.
The other commands gave me unexpected results that worried me a bit but it still worked out in the end.
```
chkdsk /r
```Did not work. Something about not being able to write to the drive.
```
BootRec.exe /FixBoot
BootRec.exe  /ScanOs
```Both said that the number of Windows installation was 0.

---

### Post by ranch hand on 2010-05-22
Wow, that is great.

I forgot one question that I need an answer to.  What in flinderation is a "PW disk"?

---

### Post by wilee-nilee on 2010-05-23
> **NTHQ said:**
> I just followed those instructions and now everything is back to normal!
Thank you everyone who has contributed their help. I appreciate it very much. :P

That is awesome glad everything is working.;)

---


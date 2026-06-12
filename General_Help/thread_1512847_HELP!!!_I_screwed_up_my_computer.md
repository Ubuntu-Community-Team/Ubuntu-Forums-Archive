---
title: "HELP!!! I screwed up my computer"
date: 2010-06-18
forum: General Help
---

### Post by dbaybay on 2010-06-18
Hi there, I just used a Ubuntu LiveCD to install Windows 7 and Ubuntu side by side, when it restarted it gave me only this screen:

GRUB RESCUE



What do I do!?

Please help!

---

### Post by nemiux on 2010-06-18
Ok, lets start. Could you give a photo or full text that is written?

---

### Post by dbaybay on 2010-06-18
> **nemiux said:**
> Ok, lets start. Could you give a photo or full text that is written?

Sure, my computer loads up and goes right to a black screen that says this -

[PHP]
error: file not found.
grub rescue >
[/PHP]

And that's it. The rest is all black.

---

### Post by nemiux on 2010-06-18
I'm not sure will it work but try this: Insert your live cd, and start installing ubuntu again. While on step where you clicked install side my side, check on which partition is your ubuntu (If you have one hard disk it would usually be /dev/sda2) and click the third option to set partitions manually. Then find the partition with ubuntu, click delete, and you will see free space, and a button called "Add" will be active, then you create a partition with ext4 or ext3 (use the newer one, usually ext4). And mount point should be "/" that way you will reinstall it. Maybe it will work. Good luck

---

### Post by dbaybay on 2010-06-18
OMG - so reinstalling it worked, Linux booted up fine BUT!

Windows 7 is no longer on the list! What happened to my Windows Partition?!

---

### Post by QIII on 2010-06-18
Could you issue the following in the terminal and post the results?

```
sudo fdisk -l
```

That's a small "ell", not a "one".

---

### Post by dbaybay on 2010-06-18
> **QIII said:**
> Could you issue the following in the terminal and post the results?

```
sudo fdisk -l
```That's a small "ell", not a "one".

I uploaded the screenshot to tinypic:

[http://tinypic.com/r/1ic3vc/6](http://tinypic.com/r/1ic3vc/6)

---

### Post by dbaybay on 2010-06-18
I can still see all my files on the Windows 7 drive - it's the biggest drive. It just doesn't show up on the list when I turn my computer on.

---

### Post by QIII on 2010-06-18
Could you please issue the following command in the terminal and post the output?

```
sudo update-grub2
```

---

### Post by wilee-nilee on 2010-06-18
If we want to see what is really going on we will need the boot script. OP post the link in my sig in code tags. This may as simple as grub being in the windows partition which can be fixed generally, we wont know if this is the case though without the script. There may be other ways to find this information but the script gives all the information needed in one fell swoop.

---

### Post by dbaybay on 2010-06-18
> **QIII said:**
> Could you please issue the following command in the terminal and post the output?

```
sudo update-grub2
```

Here it is -

[http://tinypic.com/r/33aqcnm/6](http://tinypic.com/r/33aqcnm/6)

---

### Post by Zintha on 2010-06-18
There are lots of other topics about this, especially with 7.

First things first, go into terminal and put 
> sudo update-grub

and you'll get something like
> ubuntu@ubuntu-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
ubuntu@ubuntu-desktop:~$ 



If that doesn't work:

Try looking up about bootfix and other topics. Sorry if this isn't much help, just wanted to point you in the right direction.

Chances are Grub2 overwrote the Windows boot manager.

---

### Post by QIII on 2010-06-18
dbaybay-

Reboot and try to get into Windows.

If you can't, do as wilee-nilee suggested.


Edit -- just reread your first post.  Did you have Vista and 7 installed?

---

### Post by dbaybay on 2010-06-18
> **Zintha said:**
> There are lots of other topics about this, especially with 7.

First things first, go into terminal and put 


and you'll get something like


If that doesn't work:

Try looking up about bootfix and other topics. Sorry if this isn't much help, just wanted to point you in the right direction.

Chances are Grub2 overwrote the Windows boot manager.

I get errors when I put in that command.

It says "ls: cannot access /var/lib/os-prober/mount/boot"
next line "Boot: No such file or directory"

What do I do?

---

### Post by dbaybay on 2010-06-18
When I open the disk utility, it says my Windows 7 partition is -

"Mounted at /media/HP"

If that helps at all?

---

### Post by wilee-nilee on 2010-06-18
> **dbaybay said:**
> When I open the disk utility, it says my Windows 7 partition is -

"Mounted at /media/HP"

If that helps at all?

I will say here that you can peck at it and break it for good, post the script.

---

### Post by QIII on 2010-06-18
> **wilee-nilee said:**
> I will say here that you can peck at it and break it for good, post the script.


For the OP -- I agree with wilee-nilee at this point.  I first like to give update-grub2 a try, since that catches 80% of problems easily.

But before we get too far afield with all sorts of boot management tools that may lead you down a lot of rabbit holes where you will break things completely, just give the script a try.

The os-prober error is another matter we can worry about after taking a look at that.

---

### Post by dbaybay on 2010-06-18
[PHP]

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,911   531,357,622   531,150,712   7 HPFS/NTFS
/dev/sda3         531,357,694   952,680,447   421,322,754   5 Extended
/dev/sda5         531,357,696   921,982,975   390,625,280  83 Linux
/dev/sda6         921,985,024   952,680,447    30,695,424  82 Linux swap / Solaris
/dev/sda4         952,680,448   976,771,071    24,090,624   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5EFCA4A2FCA47645                       ntfs       SYSTEM                        
/dev/sda2        26DA78D4DA78A1AB                       ntfs       HP                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        D67047117046F7AF                       ntfs       FACTORY_IMAGE                 
/dev/sda5        ae55cfac-96c1-4f3d-ad89-85237d3a8f28   ext4                                     
/dev/sda6        5e774784-2450-4635-aa93-228cfc1b7b51   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/HP                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set ae55cfac-96c1-4f3d-ad89-85237d3a8f28
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
search --no-floppy --fs-uuid --set ae55cfac-96c1-4f3d-ad89-85237d3a8f28
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
    search --no-floppy --fs-uuid --set ae55cfac-96c1-4f3d-ad89-85237d3a8f28
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=ae55cfac-96c1-4f3d-ad89-85237d3a8f28 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ae55cfac-96c1-4f3d-ad89-85237d3a8f28
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=ae55cfac-96c1-4f3d-ad89-85237d3a8f28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ae55cfac-96c1-4f3d-ad89-85237d3a8f28
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ae55cfac-96c1-4f3d-ad89-85237d3a8f28 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ae55cfac-96c1-4f3d-ad89-85237d3a8f28
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ae55cfac-96c1-4f3d-ad89-85237d3a8f28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ae55cfac-96c1-4f3d-ad89-85237d3a8f28
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ae55cfac-96c1-4f3d-ad89-85237d3a8f28
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d67047117046f7af
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ae55cfac-96c1-4f3d-ad89-85237d3a8f28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5e774784-2450-4635-aa93-228cfc1b7b51 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 306.5GB: boot/grub/core.img
 362.4GB: boot/grub/grub.cfg
 306.5GB: boot/initrd.img-2.6.32-21-generic
 306.6GB: boot/initrd.img-2.6.32-22-generic
 306.5GB: boot/vmlinuz-2.6.32-21-generic
 273.0GB: boot/vmlinuz-2.6.32-22-generic
 306.6GB: initrd.img
 306.5GB: initrd.img.old
 273.0GB: vmlinuz
 306.5GB: vmlinuz.old

[/PHP]

---

### Post by wilee-nilee on 2010-06-18
Thanks dbaybay the script will help to get you setup. Everything is there as you suggest. The boot flag is on sda1 which appears to be the boot mgr, but there is also one on sda4, so I'm really not sure myself. But the script will standout for those that do know.

what is sda4?

---

### Post by QIII on 2010-06-18
Just wanted to be sure before posting this...

wilee-nilee, if you would take a look and sound off, too.

dbaybay:  Wait until wilee-nilee has a chance to respond to this

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by wilee-nilee on 2010-06-18
> **QIII said:**
> Just wanted to be sure before posting this...

wilee-nilee, if you would take a look and sound off, too.

dbaybay:  Wait until wilee-nilee has a chance to respond to this

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

I missed the grub entry in sda1 I think your probably correct. I'm not a real expert in this area though I just watch others and know the use of the script. The grub entry is suspicious, I have seen it in a different configuration usually, but it is there. Good eye;)

---

### Post by wilee-nilee on 2010-06-18
Just for reference here is the script on my computer sda1 is XP and sdb is a thumb I am actually using to run the computer. There is no grub entry in my sda1.
             ```
   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   312,578,047   312,576,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.1 GB, 16131293184 bytes
255 heads, 63 sectors/track, 1961 cylinders, total 31506432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    31,503,464    31,501,417  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00463C52463C4AA4                       ntfs       ACER                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        cc8f98b8-9bd2-4b45-a9c0-def62ab93531   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/usb0              ext4       (rw,noexec,nodev,sync,noatime,nodiratime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set cc8f98b8-9bd2-4b45-a9c0-def62ab93531
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
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
search --no-floppy --fs-uuid --set cc8f98b8-9bd2-4b45-a9c0-def62ab93531
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
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
	search --no-floppy --fs-uuid --set cc8f98b8-9bd2-4b45-a9c0-def62ab93531
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=cc8f98b8-9bd2-4b45-a9c0-def62ab93531 ro  vga=771 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set cc8f98b8-9bd2-4b45-a9c0-def62ab93531
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=cc8f98b8-9bd2-4b45-a9c0-def62ab93531 ro single  vga=771 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 00463c52463c4aa4
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=9f81e678-873a-4335-8a3d-dcfa31de23ed none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/core.img
  11.1GB: boot/grub/grub.cfg
   3.2GB: boot/initrd.img-2.6.32-22-generic
   2.7GB: boot/vmlinuz-2.6.32-22-generic
   3.2GB: initrd.img
   2.7GB: vmlinuz
```

---

### Post by dbaybay on 2010-06-19
So what do I have to do to fix it? I'm very confused.

---

### Post by chamber on 2010-06-19
In a terminal

> sudo gedit /boot/grub/menu.lst

A large text file will open and at the bottom leave a line and add this:

copy and paste the contents

EDIT, 

copy and paste after this,

## ## End Default Options ##

---

### Post by Zerocool Djx on 2010-06-19
Your grub definitely got messed up.. You can try and reinstall grub, but I'm only guessing if if will pick up the partitions.. Anyway,.. Next time I'd re-partition the main drive first to make space and make a boot disk for windows. Then when you install Ubuntu you just go to the largest unused disk space. Works every time for me an dI never had any issues. 

Good luck!

---

### Post by QIII on 2010-06-19
> **chamber said:**
> In a terminal



A large text file will open and at the bottom leave a line and add this:

copy and paste the contents

EDIT,

copy and paste after this,

## ## End Default Options ##


The OP is using GRUB2.  menu.lst no longer exists.


> **Zerocool Djx said:**
> Your grub definitely got messed up.. You can try and reinstall grub, but I'm only guessing if if will pick up the partitions.. Anyway,.. Next time I'd re-partition the main drive first to make space and make a boot disk for windows. Then when you install Ubuntu you just go to the largest unused disk space. Works every time for me an dI never had any issues.

Good luck!


No.  What got messed up is two files with names that are conflicting.


dbaybay:  The solution is in the URL I gave you.  If you don't understand, I think I might be able to find another forum post on the matter.

---

### Post by dbaybay on 2010-06-19
> **QIII said:**
> The OP is using GRUB2.  menu.lst no longer exists.





No.  What got messed up is two files with names that are conflicting.


dbaybay:  The solution is in the URL I gave you.  If you don't understand, I think I might be able to find another forum post on the matter.

Please if you could! I'm so confused, brand new to this Linux/Ubuntu stuff and I need to be able to use Windows on my desktop too. All my files are still there, it's just not on the list! Thank you so much!

---

### Post by wilee-nilee on 2010-06-19
You have the grub boot in the windows partition sda1 here is the link.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Here are the instructions on the page.

sudo apt-get install testdisk
   sudo testdisk

First   screen:  Select "No Log" and press enter.
Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".
Third   screen:  "intel"
Fourth  screen:  "advanced",
Fifth   screen:  Select the Windows system partition  and choose "boot"
Sixth   screen:  "BackupBS"
Seventh screen:  type "Y" to confirm

Print the whole page or these instructions or have the browser window open when you run it. **Read the solution section** this can also be fixed with a W7 recovery or install disc.

If you decide to use the W7 recovery or install disc here are instructions for it just run the highlighted command and look at the http on how to get to repair. and here is a recovery disc link as well.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
**BootRec.exe /FixBoot** (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by dbaybay on 2010-06-22
> **chamber said:**
> In a terminal



A large text file will open and at the bottom leave a line and add this:

copy and paste the contents

EDIT, 

copy and paste after this,

## ## End Default Options ##


sudo: gedit/boot/grub/menu.lst: command not found

^^ That's what it says when I type in that command in the terminal.

---

### Post by philinux on 2010-06-22
Should be like this. Copy and paste.

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by dbaybay on 2010-06-22
> **wilee-nilee said:**
> You have the grub boot in the windows partition sda1 here is the link.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Here are the instructions on the page.

sudo apt-get install testdisk
   sudo testdisk

First   screen:  Select "No Log" and press enter.
Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".
Third   screen:  "intel"
Fourth  screen:  "advanced",
Fifth   screen:  Select the Windows system partition  and choose "boot"
Sixth   screen:  "BackupBS"
Seventh screen:  type "Y" to confirm

Print the whole page or these instructions or have the browser window open when you run it. **Read the solution section** this can also be fixed with a W7 recovery or install disc.

If you decide to use the W7 recovery or install disc here are instructions for it just run the highlighted command and look at the http on how to get to repair. and here is a recovery disc link as well.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
**BootRec.exe /FixBoot** (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Okay, I followed your directions step by step and got a different screen. I'll walk you through what I see.

After I get to second screen, right before I select "Intel" it tells me - "HIDDEN SECTORS ARE PRESENT"

It lets me continue or quit, so I continue and select Intel. Once I select advanced, I am now looking at several different partitions. I'm assuming the one with a P next to it is my Primary Partition, so I highlight it. This is where I get stuck though, because it doesn't offer me the "BackupBS" option that you told me to select. When I select "BOOT", I see - 

Boot sector - OK
Backup boot sector - OK
Sectors are identical

Options are: Quit, List, Rebuild BS, Repair MFT and Dump


Which should I select? I do not have a Windows 7 recovery disk, it was just installed when I bought the computer a few weeks ago. Boy did I screw something up :(

---

### Post by dbaybay on 2010-06-22
> **philinux said:**
> Should be like this. Copy and paste.

```
sudo gedit /boot/grub/menu.lst
```

Yeah I typed that in and typed out what it gave me (with the ":::" and whatnot)

---

### Post by sf-it-services on 2010-06-22
grub2 is installed by default on new ubuntu distributions, there is no menu.lst.

Windows 7 boot loader will allow you to dual-boot operating systems.

I would suggest [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

the re-install should solve any issues you have created by 'toying' and your system should reconfigure as realistically the grub.cfg file is now truly a configuration file and not a user editable script (although we can edit it if we choose, I hope you know what I mean)

Windows 7 places a small partition on the HDD which I believe grub may be picking up as a useful partition although its still just windows bull***.

OS Prober may find more than just win7 and linux, you need to change permissions in /etc/grub.d/ to stop certain actions being performed on the boot menu through grub2

I still think a sudo update-grub is what you really needed at the beginning, before you may have toyed

---

### Post by yetiman64 on 2010-06-22
> **dbaybay said:**
> Yeah I typed that in and typed out what it gave me (with the ":::" and whatnot)

Never mind about anything to do with menu.lst, **it does not exist in grub2**. Your boot files from the script are 
> [COLOR=#000000][COLOR=#0000bb] Boot files[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]dirs[/COLOR][COLOR=#007700]:   /[/COLOR][COLOR=#0000bb]boot[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]grub[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]grub[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]cfg [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]etc[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]fstab [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]boot[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]grub[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]core[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]img
[/COLOR][/COLOR].

Best to have patience and wait for wilee-nilee or QIII to come back online (both offline at the moment). As far as I can see they seem to be on the right track for you.

Note: reinstalling grub won't fix what wilee-nilee and QIII are referring to -- be careful.

Edit: the script output and the links they gave are for fixing a boot messup in the windows partition and reinstallling grub won't fix that.

---

### Post by dbaybay on 2010-06-22
> **yetiman64 said:**
> Never mind about anything to do with menu.lst, **it does not exist in grub2**. Your boot files from the script are 
.

Best to have patience and wait for wilee-nilee or QIII to come back online (both offline at the moment). As far as I can see they seem to be on the right track for you.

Note: reinstalling grub won't fix what wilee-nilee and QIII are referring to -- be careful.

Edit: the script output and the links they gave are for fixing a boot messup in the windows partition and reinstallling grub won't fix that.

I'll sit patiently and wait, I don't want to screw anything up further.

For some stupid reason there is a Vista loader on my computer, but I only want Linux and Windows 7 - is there anyway I could log on to the Vista Loader to fix the W7 issue though?

Thank you :)

---

### Post by yetiman64 on 2010-06-22
> Thank you :smile: You're welcome. 
There are some good boot problem fixers in this forum and the guys I mentioned are in with them.
 
Just a pity I don't have enough experience with your particular problem. But I'd suggest you wait for someone with more experience with the testdisk method rather than trying anything from windows (from my experience using Windows tools can really mess up grub if you're not careful). 

 Good luck, yetiman64

---

### Post by sf-it-services on 2010-06-22
chances are you have sda1 is the windows 7 loader, sda2 is the windows 7 factory recovery partition (to reset the HD) sda3 is the linux partition and sda4 is the windows 7 Operating system.

perhaps you may remember how the drive was formatted.
sda 3 and 4 should be bootable from the grub menu (leave sda2 in to make a full recovery easier)

I do agree with what was previously said about reinstalling grub2, but reading the guide may help your understanding as to what Grub2 is doing.

---

### Post by yetiman64 on 2010-06-22
By all means read up on grub2. But note from your boot-info-script

> [COLOR=#000000][COLOR=#dd0000]=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
[/COLOR][/COLOR]This your windows partition (sda1) and grub boot files should not be in there. I believe this is what peaked wilee-nilee's and QIII's interest and needs fixing. Correct me if I'm wrong fellas, when you come back online.

Edit: comparison from wilee-nilee's script output
> ================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

 a windows boot entry

---

### Post by dbaybay on 2010-06-22
> **yetiman64 said:**
> By all means read up on grub2. But note from your boot-info-script

This your windows partition (sda1) and grub boot files should not be in there. I believe this is what peaked wilee-nilee's and QIII's interest and needs fixing. Correct me if I'm wrong fellas, when you come back online.

Edit: comparison from wilee-nilee's script output
 a windows boot entry


You lost me, but I did go to the harddrive > HP > Windows > Boot and there is no grub file or folder in the boot folder on my computer - it's just gone!

---

### Post by sf-it-services on 2010-06-22
[COLOR=#000000][COLOR=#DD0000]that is for an XP boot loader, windows 7 partitions differently on install...... do you have an option for the windows vista loader it looks like that is booting to sda4, which is your windows installation........ its just not called windows 7

[/COLOR][/COLOR]

---

### Post by dbaybay on 2010-06-22
> **sf-it-services said:**
> [COLOR=#000000][COLOR=#dd0000]that is for an XP boot loader, windows 7 partitions differently on install...... do you have an option for the windows vista loader it looks like that is booting to sda4, which is your windows installation........ its just not called windows 7

[/COLOR][/COLOR]

Yes, I do have an option for Windows Vista - Let me restart and select it.

I left it alone because I didn't want to screw anything else up.

---

### Post by dbaybay on 2010-06-22
Okay when I selected the Vista Loader, it booted up my "HP RECOVERY" thing. It used Windows 7 to boot it, but it's not my regular Windows 7 Partition.

---

### Post by yetiman64 on 2010-06-22
> You lost me, but I did go to the harddrive > HP > Windows >  Boot and there is no grub file or folder in the boot folder on my  computer - it's just gone!Have you made any changes to the system since the original boot info was collected ? 

I'm only referring to the script output from your earlier post.
If the setup is the same, sda1 should not be showing a **grub** boot entry in the windows partition sda1, as your script indicates - note there may not be "files" visible as such - think of bootsectors and bootcode).
I believe this is what the guys earlier said is "confusing" grub hence no Windows entry, and no amount of reinstalling grub will move what is in a Windows boot sector.


> [COLOR=#000000][COLOR=#dd0000]that is for an XP boot  loader, windows 7 partitions differently on install......[/COLOR][/COLOR] Yes it is for XP, but is only there as a comparison to a "normal" windows boot entry and not one for "grub" as your script is showing.

IMO Best you wait for further opinion/follow up from the guys mentioned. Bye for now and I'll check back when they check what I've commented on :).

---

### Post by nemiux on 2010-06-22
I've been experiencing about the same problem. At the end I got up installing Ubuntu on Windows so boot.ini, at your case bcdedit.exe would boot up first. So, if you want your Vista back to normal, insert the installation disc, click repair, and in the command prompt, write ```
fixboot
``` This will restore your boot back to normal, however, you won't be able to access your Ubuntu. Sorry ;)

---

### Post by dbaybay on 2010-06-22
> **nemiux said:**
> I've been experiencing about the same problem. At the end I got up installing Ubuntu on Windows so boot.ini, at your case bcdedit.exe would boot up first. So, if you want your Vista back to normal, insert the installation disc, click repair, and in the command prompt, write ```
fixboot
``` This will restore your boot back to normal, however, you won't be able to access your Ubuntu. Sorry ;)

Why won't Ubuntu load then!? There must be some way to do this and keep my windows 7 files and my ubuntu?

---

### Post by sf-it-services on 2010-06-22
well thats a start, your recovery partition is known now as SDA4 which means your win7 boot is sda2

---

### Post by sf-it-services on 2010-06-22
[COLOR=#000000][COLOR=#DD0000]manually configure your grub.cfg file(even though it says no)
on the vista loader part it will say :-

set root='(hd0,4)'

change it to

[/COLOR][/COLOR][COLOR=#000000][COLOR=#DD0000]set root='(hd0,2)'[/COLOR][/COLOR]

(and change the title to windows 7)leaving in the ' marks if you aren't sure don't do it

it will work

---

### Post by sf-it-services on 2010-06-22
> **nemiux said:**
> I've been experiencing about the same problem. At the end I got up installing Ubuntu on Windows so boot.ini, at your case bcdedit.exe would boot up first. So, if you want your Vista back to normal, insert the installation disc, click repair, and in the command prompt, write ```
fixboot
``` This will restore your boot back to normal, however, you won't be able to access your Ubuntu. Sorry ;)

Thats not fixing anything

---

### Post by dbaybay on 2010-06-22
> **sf-it-services said:**
> [COLOR=#000000][COLOR=#dd0000]manually configure your grub.cfg file(even though it says no)
on the vista loader part it will say :-

set root='(hd0,4)'

change it to

[/COLOR][/COLOR][COLOR=#000000][COLOR=#dd0000]set root='(hd0,2)'[/COLOR][/COLOR]

(and change the title to windows 7)leaving in the ' marks if you aren't sure don't do it

it will work

I'm sorry I'm so new to all of this - How do I do that exactly? I don't have any grub stuff in my Windows > Boot folder.

The Vista Loader loads Windows 7 HP Recovery Console and it tells I can Restore my system, no other options. I can't get to a command prompt in the recovery console

---

### Post by sf-it-services on 2010-06-22
are you using windows now?

---

### Post by sf-it-services on 2010-06-22
you will be changing the boot config file, the one you copied earlier, you need to edit it

---

### Post by dbaybay on 2010-06-22
> **sf-it-services said:**
> are you using windows now?

I've been using my laptop (windows 7) to communicate on the boards.

My desktop, the one with the problem, only loads Ubuntu and Vista Loader (which is my HP recovery console). I posted some sort of script thing a few pages back if that helps.

---

### Post by sf-it-services on 2010-06-22
edit the boot config file as I said in linux
0,4 to 0,2 

I have read the scripts, your windows 7 installation is at 0,2 change grub.cfg or whatever to that and it should boot yer windows 7 innit geeza

---

### Post by dbaybay on 2010-06-22
> **sf-it-services said:**
> edit the boot config file as I said in linux
0,4 to 0,2 

I have read the scripts, your windows 7 installation is at 0,2 change grub.cfg or whatever to that and it should boot yer windows 7 innit geeza

I just did what you said typed in this command:

sudo gedit /boot/grub/grub.cfg

And changed the hd0,4 to hd0,2 and I saved the file and restarted

I'm still getting the Recovery Console when I check Vista Loader.

---

### Post by sf-it-services on 2010-06-22
now do the sudo update-grub

---

### Post by dbaybay on 2010-06-22
> **sf-it-services said:**
> now do the sudo update-grub

Okay I just did sudo update-grub and it generated grub.cfg ....

Found linux image, initrd image, linux image, initrd image, memtest86+ - then I get this error:

"ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory"

Then it says

Found Windows Vista (loader) on /dev/sda4
done

---

So it like just reset my changes then?

---

### Post by sf-it-services on 2010-06-22
yeah.... you need it to like 0,2

---


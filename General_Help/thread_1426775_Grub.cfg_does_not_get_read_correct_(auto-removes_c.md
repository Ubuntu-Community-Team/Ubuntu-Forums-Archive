---
title: "Grub.cfg does not get read correct (auto-removes characters at boot menu)"
date: 2010-03-10
forum: General Help
---

### Post by TheForumTroll on 2010-03-10
I have a problem with GRUB 2 that I hope someone here can help me fix. Every time I boot I get an error because GRUB deletes that last part of the initrd line in /boot/grub/grub.cfg.

So this:
```

initrd  /initrd.img-2.6.31-20-generic

```

Becomes this (notice the missing "c" at the end):
```

initrd  /initrd.img-2.6.31-20-generi

```

And the windows part is also broken:
```

chainloader +

```


If I add an extra character at the end of the line it get removed instead and then it works. But only until next time the grub.cfg is auto updated. The error is only there when booting. Reading the file every character is in there.

---

### Post by ajgreeny on 2010-03-10
Very weird!

Have you looked in to the /boot folder of your filesystem where those initrd.img files reside to see if the file there is correctly named and has the final "c"?  I can't think why it should not be correct, and I suspect that everything would stop working if it was wrong, but I'm clutching at straws here, and can't think of anything else to suggest.

If the initrd.img file is missing the final "c", rename it with ```
sudo mv /boot/initrd.img-2.6.31-20-generi /boot/initrd.img-2.6.30-20-generic
```and see if that helps.  If I am wrong and the file is already correctly named, I have no idea where to go next.

---

### Post by TheForumTroll on 2010-03-10
The files are named correct with a C at the end. I actually have to edit the boot menu and add the C to boot Ubuntu or add an extra letter in the grub.cfg.

---

### Post by TheForumTroll on 2010-03-13
anyone?

---

### Post by dcstar on 2010-03-13
> **TheForumTroll said:**
> anyone?

Reinstall all the original Grub2 files - including configuration files.

---

### Post by louieb on 2010-03-13
Really weird!  Might try reinstalling GRUB2 - sounds like it has a twisted bit or 2.

You did say grub.cfg has the correct name .
 
Get and run the [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")
see if anything looks strange.

---

### Post by TheForumTroll on 2010-03-14
Yes reading in grub.cfg the filenames match the actual files.

I tried the boot script but I didn't find anything out of the ordinary:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdc7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x094daf20

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   234,436,607   234,434,560   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfbfcfbfc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   234,438,655   234,231,808   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc93adb9a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63     8,000,369     8,000,307  82 Linux swap / Solaris
/dev/sdc2           8,000,370   765,127,754   757,127,385   5 Extended
/dev/sdc5           8,000,433    12,000,554     4,000,122  83 Linux
/dev/sdc6          12,000,618    61,994,834    49,994,217  83 Linux
/dev/sdc7          61,994,898   765,127,754   703,132,857  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F09CFEE39CFEA2F0                       ntfs       Vista                         
/dev/sdb1        283024133023E692                       ntfs       System Reserved               
/dev/sdb2        484A37454A372F56                       ntfs                                     
/dev/sdc1        f848a443-2a98-4937-9597-0731c06fa0f1   swap                                     
/dev/sdc5        1d04faf8-aa0f-4f79-9240-a7242159a74d   ext2                                     
/dev/sdc6        57be93da-88f7-45f7-b1f0-b9f0d2ec09f0   ext4                                     
/dev/sdc7        f335d10f-2a77-4ce4-9145-7ccfb8d66f9a   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc5        /boot                    ext2       (rw)
/dev/sdc7        /home                    ext4       (rw)


============================= sdc5/grub/grub.cfg: =============================

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
if terminal_input console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal console
fi
if terminal_output console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal console
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=8
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set gfxpayload=keep
	insmod ext2
	set root=(/dev/sdc,5)
	search --no-floppy --fs-uuid --set 1d04faf8-aa0f-4f79-9240-a7242159a74d
	echo	Loading Linux 2.6.31-20-generic ...
	linux	/vmlinuz-2.6.31-20-generic root=UUID=57be93da-88f7-45f7-b1f0-b9f0d2ec09f0 ro   quiet splash
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.31-20-genericx
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set gfxpayload=keep
	insmod ext2
	set root=(/dev/sdc,5)
	search --no-floppy --fs-uuid --set 1d04faf8-aa0f-4f79-9240-a7242159a74d
	echo	Loading Linux 2.6.31-20-generic ...
	linux	/vmlinuz-2.6.31-20-generic root=UUID=57be93da-88f7-45f7-b1f0-b9f0d2ec09f0 ro single 
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set gfxpayload=keep
	insmod ext2
	set root=(/dev/sdc,5)
	search --no-floppy --fs-uuid --set 1d04faf8-aa0f-4f79-9240-a7242159a74d
	echo	Loading Linux 2.6.31-19-generic ...
	linux	/vmlinuz-2.6.31-19-generic root=UUID=57be93da-88f7-45f7-b1f0-b9f0d2ec09f0 ro   quiet splash
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set gfxpayload=keep
	insmod ext2
	set root=(/dev/sdc,5)
	search --no-floppy --fs-uuid --set 1d04faf8-aa0f-4f79-9240-a7242159a74d
	echo	Loading Linux 2.6.31-19-generic ...
	linux	/vmlinuz-2.6.31-19-generic root=UUID=57be93da-88f7-45f7-b1f0-b9f0d2ec09f0 ro single 
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set gfxpayload=keep
	insmod ext2
	set root=(/dev/sdc,5)
	search --no-floppy --fs-uuid --set 1d04faf8-aa0f-4f79-9240-a7242159a74d
	echo	Loading Linux 2.6.31-14-generic ...
	linux	/vmlinuz-2.6.31-14-generic root=UUID=57be93da-88f7-45f7-b1f0-b9f0d2ec09f0 ro   quiet splash
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set gfxpayload=keep
	insmod ext2
	set root=(/dev/sdc,5)
	search --no-floppy --fs-uuid --set 1d04faf8-aa0f-4f79-9240-a7242159a74d
	echo	Loading Linux 2.6.31-14-generic ...
	linux	/vmlinuz-2.6.31-14-generic root=UUID=57be93da-88f7-45f7-b1f0-b9f0d2ec09f0 ro single 
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f09cfee39cfea2f0
	chainloader +1x
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 283024133023e692
	chainloader +1x
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdc5: Location of files loaded by Grub: ===================


   6.1GB: grub/core.img
   6.1GB: grub/grub.cfg
   4.1GB: initrd.img-2.6.31-14-generic
   4.1GB: initrd.img-2.6.31-19-generic
   4.1GB: initrd.img-2.6.31-20-generic
   4.1GB: vmlinuz-2.6.31-14-generic
   4.1GB: vmlinuz-2.6.31-19-generic
   4.1GB: vmlinuz-2.6.31-20-generic

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> 						<mount point>   		<type>  		<options>       	<dump>  <pass>
proc            						/proc           		proc    		defaults        	0       0
UUID=57be93da-88f7-45f7-b1f0-b9f0d2ec09f0 			/               		ext4    		errors=remount-ro 	0       1
UUID=1d04faf8-aa0f-4f79-9240-a7242159a74d 			/boot           		ext2    		defaults        	0       2
UUID=f335d10f-2a77-4ce4-9145-7ccfb8d66f9a 			/home           		ext4    		defaults        	0       2
UUID=f848a443-2a98-4937-9597-0731c06fa0f1 			none            		swap    		sw              	0       0



#/dev/scd0                                                      /media/cdrom0                   udf,iso9660             user,noauto,exec,utf8   0       0


=================== sdc6: Location of files loaded by Grub: ===================


   6.2GB: initrd.img
   6.2GB: initrd.img.old
   6.2GB: vmlinuz
   6.1GB: vmlinuz.old

```

---

### Post by TheForumTroll on 2010-03-14
Oh i forgot: Reinstalling didn't help. I think I'll downgrade to good old legacy GRUB instead.

---

### Post by TheForumTroll on 2010-03-15
Purging grub2 and reinstalling it broke the boot of the system. I am now using the much better legacy-grub. Grub2 is so full of bugs it is more like alpha than beta [-X

---

### Post by louieb on 2010-03-15
Its still weird . I did a search of [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu") for GRUB2 of the 400+ listed did not see one where it was truncating statements. Guess you found and new one - oh well.

---

### Post by drs305 on 2010-03-15
A month or or more ago I read of several instances of this happening. As with louieb, I have searched (a long time) and cannot find the references.

I haven't seen any of these reports in the past month so am fairly certain whatever was causing it has been fixed. If you really wanted to use Grub 2, I would completely purge it and reinstall it. I detailed how to do this in post #9:
[http://ubuntuforums.org/showthread.php?t=1425998]("http://ubuntuforums.org/showthread.php?t=1425998")

---

### Post by drs305 on 2010-03-15
A month or so ago I read of several instances of this happening. As with louieb, I have searched (a long time) and cannot find the references.

I haven't seen any of these reports in the past month so am fairly certain whatever was causing it has been fixed. If you really wanted to use Grub 2, I would completely purge it and reinstall it. I detailed how to do this in post #9 of the following thread:
[http://ubuntuforums.org/showthread.php?t=1425998]("http://ubuntuforums.org/showthread.php?t=1425998")

---

### Post by lordskid on 2010-03-15
hi do you by any chance use the grub2 experimental from felix zielcke's ppa?

if so a workaround would be to add an extra 'c' or other character at the end of all menu entries. manually edit your grub.cfg (make a backup first)

such that the generic after the last line would spell out as genericc

also when you get the grub menu press 'c' to display the command line do you see an error that says something about zero dimension? can you post or pm me that error message. thanks one thing you can do is to remove grub2 experimental then remove fzielcke's ppa then reinstall grub-pc and grub-common make sure it is the one from the repository of ubuntu.

hope this helps.

---

### Post by irishbandit on 2010-03-28
Having the same problem with ppa:fzielcke/grub-ppa 
the config deletes the last line of the config when booting.
In my case it deletes the e from pae
lines from grub.cfg as follows shows the correct spelling 

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.31-20-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 38e9e29f-7b9f-42cf-ba34-21de22070875
	echo	Loading Linux 2.6.31-20-generic-pae ...
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=38e9e29f-7b9f-42cf-ba34-21de22070875 ro   quiet splash
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}

On boot I hit e add the e to the last line hit ctrl+x boots fine

The other error that you mention though is 
"error requested to scale to a size w/ a zero dimension"

---

### Post by lordskid on 2010-03-30
I removed fzielcke's ppa from my sources list. and reinstall grub2 beta from the main repo everything is fine now. maybe felix encountered some problem with this last compile and got busy with other projects maybe with the upcoming lucid lynx. Did you try the workaround I posted?

you have to manually edit your grub.cfg and add an extra character at the end of the last line for each menu entry. That way it will delete the extra character not the one that is actually needed.

---

### Post by irishbandit on 2010-03-30
I read the work around you posted and since this is not a horrible problem for me I didn't edit the grub.cfg. I will wait for 10.04 and then switch over to the official repo version. 

Thank-you for the ideas.

---


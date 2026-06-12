---
title: "copy ubuntu installation to new hard drive"
date: 2010-12-08
forum: General Help
---

### Post by then_dude on 2010-12-08
hello,

i have ubuntu 10.04 on a partition of a  drive,

i have bought a new harddrive and want to copy the content of the "ubuntu partition" to a new partition on the new drive. 

can i just copy all the data and then run a live disc to make a new boot loader ? 

thank you so much

---

### Post by coffeecat on 2010-12-08
> **then_dude said:**
> can i just copy all the data and then run a live disc to make a new boot loader ? 

Surprisingly, the answer is almost yes, but there are a couple more steps. You can do the copy with 'sudo cp -a'; this will take care of permissions and will do a recursive copy, but you will end up with a system on a partition with the wrong UUID. You will need to change the UUID of the new partition to the same as that of the original one with 'sudo tune2fs /dev/whatever -U UUID'. You will also need to create a new swap partition and deal with the UUID of that as well.

Post back if you need more help.

---

### Post by sikander3786 on 2010-12-08
I am not trying to jump in here :P

Just to mention that clonezilla is another option.

[http://clonezilla.org](http://clonezilla.org)

[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

Forum member *coffeecat* definitely know their stuff ;-)

---

### Post by coffeecat on 2010-12-08
> **sikander3786 said:**
> I am not trying to jump in here :P

I'm glad you did. It's good to give the OP choice. :)

---

### Post by then_dude on 2010-12-10
hello everybody,

it worked, 

but i have a small problem now, a lot of files are not accesable from my account, even if need them, that was not the case.

for example: my thunderbird profile map is located somewhere on another partition: i cannot run thunderbird except as sudo cause i cannot acces the files. Almost no directory can be openend in nautilus, how can i fix this ?

thanks

---

### Post by coffeecat on 2010-12-10
Your first post suggested that you had only one partition to copy. If your installation was spread over more than one partition that complicates things somewhat. You need to give more information.

---

### Post by then_dude on 2010-12-10
i have changed the ownership of the files, i except that when i copied them (using a live cd) i changed ownership to root.  what do you guys think ?

thanks

---

### Post by coffeecat on 2010-12-10
> **then_dude said:**
> except that when i copied them (using a live cd) i changed ownership to root.

How did you manage to do that? If you've changed ownership of your own files you will certainly have problems. But no one can help unless you give us more information to go.

---

### Post by sikander3786 on 2010-12-10
> **coffeecat said:**
> How did you manage to do that? If you've changed ownership of your own files you will certainly have problems. But no one can help unless you give us more information to go.
+1. We definitely need more and more information before we can offer a solution. But not giving us proper info, you are making it difficult and complicated for yourself.

Anyways, Good Luck!

---

### Post by then_dude on 2010-12-12
i used the chown commando. 

but i only changed the ownership for all my other partitions with data on, i did not do this for the linux partition. So i haven't changed the operating files from Root to myself. 

i think this is what you are refering to as being problematic.

thanks guys for the support

---

### Post by then_dude on 2010-12-12
hello, 

i think i got one of the problems ...


i mounted my new harddrives in /etc/fstab

but it doesn't work, i cannot mount some of them and also mentions something about uuid. 

so i guess i must put back my uuid, but i don't know what my uuid when it was installed on the previous small harddisk.

---

### Post by sikander3786 on 2010-12-12
You need to match the UUIDs in /etc/fstab with the proper one's.

In order to find UUIDs,

```
sudo blkid
```

If you want us to help you on that, post the output of above one as well this one.

```
cat /etc/fstab
```

---

### Post by then_dude on 2010-12-12
thanks, 

i have followed your commands and was able to see the UUID of the "installed UUID" in the fstab file and was able to assign it to the new boot partition /dev/sda5

but when i do the same with the swap i get an error:

couldn't find valid filesystem superblock

---

### Post by coffeecat on 2010-12-13
> **then_dude said:**
> but when i do the same with the swap i get an error:

couldn't find valid filesystem superblock

That's an odd one to get with a swap partition because, or so I undertstand, a swap is not really a filesystem. Perhaps you could clarify what you've done. Do you mean that you've checked the UUID of the swap partition with 'sudo blkid' and that you've ensured the UUID in the swap line of your /etc/fstab is the same? If so, when do you get that error? On bootup?

---

### Post by then_dude on 2010-12-13
euu  guys i think i screwed up...


there were two lines in the fstab, one with the old root and one with the old swap UUID

then i assigned the old root UUID to the new one, and that worked
then i assigned the old swap to the new swap UUID and that gave an error

when i wanted to boot this morning the pc could not found the file system. 

it is a bit complicated for a beginner
thanks.

---

### Post by coffeecat on 2010-12-13
If the only error in your /etc/fstab is the swap partition UUID, it should boot up, but possibly with an error message. What was the exact message about it not finding a filesytem? This may be a different problem.

Boot up with the live Ubuntu CD, make sure you have an internet connection, and go to this webpage:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions and post the contents of the RESULTS.txt file. Make sure you put the output in code tags as described there by using the # icon in the forum message toolbar.

This will give us details of your partition layout, the contents of your fstab, UUIDs and grub configuration. Hopefully, we can then see what's gone wrong.

---

### Post by then_dude on 2010-12-13
thanks guys for the fast intervention

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750 1,953,520,064 1,912,554,315   f W95 Ext d (LBA)
/dev/sda5          40,965,813   121,290,749    80,324,937  83 Linux
/dev/sda6         121,290,813   125,387,324     4,096,512  82 Linux swap / Solaris
/dev/sda7         125,387,388 1,953,520,064 1,828,132,677   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   102,398,309   102,398,247  83 Linux
/dev/sdb2         102,398,310 1,997,104,409 1,894,706,100  83 Linux
/dev/sdb3       1,997,104,410 3,907,024,064 1,909,919,655  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C620205420204E2D                       ntfs       windowsboot                   
/dev/sda2: PTTYPE="dos" 
/dev/sda5        28fbcd36-99e0-406c-8da4-32657805b62d   ext3       linuxboot                     
/dev/sda6        b2599646-b8ad-41b8-b374-df0a2e70dcc1   swap                                     
/dev/sda7        5A31B3BB70729B1D                       ntfs       ntfs_871gb                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        99de66d9-0dcb-4447-a675-1458c8d7bb4b   ext4       datapartition                 
/dev/sdb2        dd70ae44-0728-4d36-a18f-ff5436e4197f   ext4       video                         
/dev/sdb3        e5e55b0d-b0a7-43ce-a467-3ada19f140f6   ext4       music                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set c9533886-e35d-4f68-9a98-789995afb903
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set c9533886-e35d-4f68-9a98-789995afb903
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c9533886-e35d-4f68-9a98-789995afb903
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=c9533886-e35d-4f68-9a98-789995afb903 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c9533886-e35d-4f68-9a98-789995afb903
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=c9533886-e35d-4f68-9a98-789995afb903 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c9533886-e35d-4f68-9a98-789995afb903
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c9533886-e35d-4f68-9a98-789995afb903
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=28fbcd36-99e0-406c-8da4-32657805b62d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=24f58013-b1d8-4ed3-8f09-b526a079564d none            swap    sw              0    0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0    0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0    0
#/dev/sda1    /media/windowsboot auto    rw,user,auto,exec,utf8 0    0
#/dev/sda7    /media/ntfs_871gb  auto    rw,user,auto,exec,utf8 0    0
#/dev/sdb1    /media/datapartition auto    rw,user,auto,exec,utf8 0    0
#/dev/sdb2    /media/video    auto    rw,user,auto,exec,utf8 0    0
#/dev/sdb3    /media/music    auto    rw,user,auto,exec,utf8 0    0


=================== sda5: Location of files loaded by Grub: ===================


  59.6GB: boot/grub/core.img
  60.8GB: boot/grub/grub.cfg
  59.7GB: boot/initrd.img-2.6.32-26-generic
  59.7GB: boot/vmlinuz-2.6.32-26-generic
  59.7GB: initrd.img
  59.7GB: vmlinuz

```

---

### Post by theozzlives on 2010-12-13
I've used clonezilla both with Ubuntu and Windows 7 without incident. If the data on the old HD is still intact, I recommend that method.

---

### Post by coffeecat on 2010-12-13
I've looked at your bootscript. I can see two problems, one major, the other extremely serious. There may be more, but I've had only time to have a quick look in order to be able to post something because I may not be able to post again for some time.

The major problem is the one you've identified, that the UUID for the swap partition in fstab is incorrect. However, this would not prevent you from booting.

The extremely serious problem is that the Ubuntu entry in your grub.cfg is trying to boot Ubuntu from sdb5 (which does not exist) with a UUID that does not exist. This, I suppose, is a result of your cloning attempt. The issue has been muddied by cloning the drive from one which was detected as sdb to one now detected as sda. The reason I suggested using tune2fs in my first post was that avoids the grub UUID problem, but does not prevent a problem arising from changing the physical designation of the drive.

You need to do two things to sort this out, both from the live CD. First, edit the hard drive /etc/fstab directly. Second, chroot into the hard drive install in order to run update-grub to correct the grub.cfg file. You *could* edit the grub.cfg directly, but that's not recommended for various reasons, and it is not editable until you deploy a little trick which I am not going to tell you about just yet.

Don't do anything yet. I haven't got time at the moment to take you through everything step-by-step. Wait until I or sikander3786 or someone experienced posts you a howto.

---

### Post by coffeecat on 2010-12-13
> **theozzlives said:**
> I've used clonezilla

Please read the thread. That was suggested to the OP as an option fully four days ago. The problem has moved on considerably since then.

---

### Post by QLee on 2010-12-13
[QUOTE=coffeecat]...
Don't do anything yet. I haven't got time at the moment to take you through everything step-by-step. Wait until I or sikander3786 or someone experienced posts you a howto.[/QUOTE]

then_dude,
This is very good advice if you aren't very experienced. While you are waiting you might have a look at this post so you can be more familiar with some of the terms that will be used. It is a very good step-by-step by drs305:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You can trust coffeecat to come back and help you as soon as possible.

---

### Post by coffeecat on 2010-12-13
OK. I've had another look at your bootscript and I believe those are the only two problems, except that there is no Windows entry in your grub menu, but the steps below will fix that.

Boot into your live CD. **Don't** mount your Ubuntu root partition from the Places menu. This will only complicate things. Instead, from a terminal:

```
sudo mount /dev/sda5 /mnt
```This will mount sda5 to /mnt which makes some of the typing a little easier below. Now edit /etc/fstab to solve the swap UUID.

```
gksudo gedit /mnt/etc/fstab
```You can probably see what you need to do, but to be sure, this line:

```
UUID=24f58013-b1d8-4ed3-8f09-b526a079564d none            swap    sw              0    0

```...needs to look like this:

```
UUID=b2599646-b8ad-41b8-b374-df0a2e70dcc1 none            swap    sw              0    0
```Save your changes and close gedit. That should take care of the swap partition. Now to chroot into your hard drive partition and update grub. First, change to root in the terminal:

```
sudo su
```[B]
WARNING.[/B] Only ever use that command when being guided or when you have gained more experience. It gives you full root powers which means that a single typo may cause untold damage. Take extreme care. The terminal prompt will have changed from $ to #. Use this as a reminder to double-check everything.

Now chroot into sda5. You may see other sets of commands for this. These are as good as any and have served me well enough. Do each command one after the other.

```
mount -t proc none /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt /bin/bash
```After the last command, you will actually be "in" sda5. Now all you have to do is:

```
update-grub
```If all goes well, this command will regenerate grub.cfg and create menu entries for Ubuntu with the correct device descriptor and UUID.

Now:

```
exit
exit
exit
```That's right - three times. The terminal will close after the last exit. Close down from the live CD and you *should* be able to boot Ubuntu. Post back if you run into any problems. I have this thread subscribed so I'll know if anyone posts.

**EDIT:** @then_dude, you *may* get an error 'Cannot find list of partitions!' when you run update-grub in the chroot environment. Don't worry about this. The only problem this will cause is that there will not be a Windows entry in the grub menu when you first retry it. If this happens, boot into Ubuntu in the normal way (your hard drive installation), open a terminal and:

```
sudo update-grub
```Hopefully, that will fix the Windows entry.

---

### Post by sikander3786 on 2010-12-13
Another +1 to everything suggested by *coffeecat*.

Chroot and running update-grub will definitely generate a new grub.cfg with everything in the correct place.

The only thing I doubt about is this.

> I believe those are the only two problems, except that there is no _Windows_ entry in your grub menu, but the steps below will fix that.

bootinfoscript couldn't find any boot files for Windows on any of the partitions. If Windows was supposed to be there, OP might need to repair the startup for Windows and then re-install Grub once more.

However, at the time being, *coffeecat's* above post is just what you need. In fact, I would recommend to correct your Grub first. I am not even sure if Windows was supposed to be there?

And if update-grub doesn't fix it, re-installing Grub (simple method) should definitely be successful ;-)

---

### Post by coffeecat on 2010-12-13
> **sikander3786 said:**
> 

The only thing I doubt about is this.

bootinfoscript couldn't find any boot files for Windows on any of the partitions. If Windows was supposed to be there, OP might need to repair the startup for Windows and then re-install Grub once more.

Thanks for spotting that, sikander3786. I knew I must have missed something. :) I must admit, I scratched my head over the XP boot sector type in sda1 and the Vista/7 boot sector type in sda7, but missed the absence of any boot files. I think you're right; perhaps Windows is not meant to be there and those are just remnants. I'm sure the OP will enlighten us.

---

### Post by then_dude on 2010-12-15
thanks guys, i works

ps: i have a windows partition but windows is not yet on it.

big thanks again

---

### Post by coffeecat on 2010-12-15
Glad it worked, but...

> **then_dude said:**
> ps: i have a windows partition but windows is not yet on it.

Be aware that if you do install Windows it will write its own code all over the mbr of sda and you won't be able to boot into Ubuntu - temporarily. If that happens, simply follow the instructions in this link:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

After which you will need to run 'sudo update-grub' in Ubuntu to get a Windows entry in the grub menu.

---

### Post by then_dude on 2010-12-17
coffecat, you are the best
thanks again

---


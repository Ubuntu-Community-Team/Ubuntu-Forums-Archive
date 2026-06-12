---
title: "Error: no such partition on non-dualboot sys"
date: 2010-10-01
forum: General Help
---

### Post by ze3rax on 2010-10-01
Hello,

I was so excited when I've removed my Win7 completely and on it's hard disk partition I've installed v.10.04 of Ubuntu. I wanted completely to remove the Win7 habits and I've decided to change the 2nd partition of my 320 GB hard drive from ntfs to ext4.

Everything was great until I deleted the 107 GB partition with the included tool in Ubuntu. When I tried to create a ext3/ext4 partition there was a error (don't have the error msg but I found an answer about it). There was nothing that I can do because most users cases were when they were dualbooting OSs. After the deny of creation in that free space I restarted my PC and booted the USB flash drive where the Live"CD" was, found the tool for partitioning and it was showing no partitions at all. I was mad and exited the live CD and restarted.

Then the real problem show up:

error: no such partition
grub rescue>_

Is there a way to start again the system without the need of complete fresh install on whole hard drive because in the main 20 GB partition where Ubuntu was installed I managed to copy some files from the 2nd partition ( ~8 GBs of data) that I don't want to lose. Also there's a 3rd partition ~190 GB full! with information that I'm really really concerned about.

Any help would be really appreciated because I'm new to Linux on one hand and on another if I lose all that information I'll reconsider if Win7 to control my laptop again.

P.S. 320 GB HD , 1st part - 20 GB (Ubuntu 10.04 64bit installed), ~107 GB left free space, 191 GB download data, 5 GB swap.

Regards,
Z

---

### Post by Quackers on 2010-10-01
Welcome to the Ubuntu Forums ze3rax.
Have a look at the thread in the link below. I think post number 2 will work but post number 3 may work and it will be quicker.
Good luck :-)

[http://ubuntuforums.org/showthread.php?t=1583881&highlight=error+partition](http://ubuntuforums.org/showthread.php?t=1583881&highlight=error+partition)

---

### Post by ze3rax on 2010-10-02
Hello,

Hope you are not sleeping :) 

I did really try what you've linked with extreme caution (obvious why :) ) and found out that the 3rd partition is still there (thank God)

The Linux OS cames up to be installed in /dev/sda7 ( Id 83 , System Linux )

Passed through *sudo mount /dev/sda7 /mnt* and when I type

[I]sudo grub-install --root-directory=/mnt/ /dev/sda7
--> Attempting to install GRUB to a partition instead of the MBR[/I]

[OK my typo mistake when installing]

Redoing it but this time is something different:
[I]sudo grub-install --root-directory=/mnt/ /dev/sda
--> error: no signature[/I]

I don't want to end as the user from the link you gave me because the only solution "Intaller" gives me is "Erase and use the entire disk". There are no OS detected, no partitions in /dev/sda, nothing.

Edit: 
* 3rd partition is visible/usable from Places->Downloads (that's the label)
* 1st (16 GB ext3) partition where Ubuntu is installed is usable though "Disk Utility" [ Mount Point: Mounted at /mnt ]. Guess if needed can move parts of my data from there to 3rd partition.

Regards,
Z

---

### Post by Quackers on 2010-10-02
I don't really know what that error means. It may be better to use the instructions in the link below. This will purge grub and re-install it. If you are sure that your Ubuntu system files are on sda7 then that is the partition to mount. The grub install should be on sda.
Good luck.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by ze3rax on 2010-10-02
ubuntu@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
ubuntu@ubuntu:~$ apt-get purge grub grub-pc grub-common
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Obviously not administrating anything... Will try to use a Windows Live CD to fix what I can and move back to Win7... Such things are ridiculous to happen when you try to partition some parts of your hard drive.

Edit: Also gives this from 1st step of the link given ->

mount: /dev/sda7 already mounted or /mnt/temp busy
mount: according to mtab, /dev/sda7 is already mounted on /mnt/temp

---

### Post by Quackers on 2010-10-02
Your terminal prompt says ubuntu@ubuntu. If you have followed the first instruction your terminal prompt should include "root". This is why you are getting permission errors.
Also maybe try entering umount /dev/sda7 first. Then continue from step 1 in the link.

---

### Post by ze3rax on 2010-10-02
The problem came up from that /dev/sda7 was already mounted. Deleted the command line for that and got root access. Will edit post if things got their happy ending.

---

### Post by Quackers on 2010-10-02
Ok, fingers crossed :-)

---

### Post by ze3rax on 2010-10-02
And we got happy ending :KS Thank God there are helpful people like you ! Thank you 

The only problem that lies ahead is how to partition the free space without screwing things up again. Can you help me out with guidance or I have to open new thread about that issue ?

---

### Post by Quackers on 2010-10-02
Aha! Excellent news, well done. drs305 saves the day, again :-)
The new partition shouldn't really be a problem now. I would do that when the system is not mounted, to be safe.

---

### Post by ze3rax on 2010-10-02
But it is obviously:
[HTML]
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=21475885056, size=100400875387, type=0x83
Entering MS-DOS parser (offset=0, size=320072933376)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 1047552, size 320061047808, type 0x0f)
Entering MS-DOS extended parser (offset=1047552, size=320061047808)
readfrom = 1047552
MSDOS_MAGIC found
readfrom = 1048064
MSDOS_MAGIC found
readfrom = 4999610368
MSDOS_MAGIC found
readfrom = 21476206080
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
Error: Invalid partition table on /dev/sda -- wrong signature 0.
ped_disk_new() failed[/HTML]

Have to mark this thread as [SOLVED] and try to find a walk around this problem.

---

### Post by Quackers on 2010-10-02
Actually, what do you intend doing with the unallocated space?

---

### Post by ze3rax on 2010-10-02
It was NTFS formated and after deleting the partition (did it yesterday) , now I want to make it ext4 ( with ext3 it gives the same error). Want to completely move to Ubuntu and doing that because I've read somewhere that even after deleting files from NTFS Linux was not deleting them in fact but putting 'em in some /trash directory. Have no clue about that.

---

### Post by Quackers on 2010-10-02
Do you intend to extend your Ubuntu pasrtition to include the free space or create a new ext4 partition and leave it empty?
Also are you now booted into your normal system, or are you still in the Live cd system?

---

### Post by ze3rax on 2010-10-02
I want to create new ext4 partition ( I want it to be new non extended partion with 100GB size. now it is 107 GB - tried with default size but get the error even then)  where I can copy information from my 3rd NTFS partition (Downloads) and when everything is copied to the new ext4 part to format the 3rd partition to ext4 also and make it 198 GB (from 191 now and those 7 GB left free from part 2 that I've problems now)

I'm in my normal sys

---

### Post by Quackers on 2010-10-02
I would try that when the system is not loaded and one job at a time. I would use GParted Live CD and boot from it. Alternatively you could do it from the Ubuntu live cd, but I have not used it for that purpose before. I don't know why you are getting the invalid partition table error.

---

### Post by ze3rax on 2010-10-02
Will try the GParted :) One last question: should I have folders like $RECYCLE.BIN , RECYCLER, System Volume Information in the 3rd partition or they are left from Windows, $Recycle and Sys Volume Info are from win$ but Recycler ?

Giving direct link because I cant handle the resize of the image in post : [http://img8.imageshack.us/img8/1231/screenshotdownloadsfiled.png](http://img8.imageshack.us/img8/1231/screenshotdownloadsfiled.png)

---

### Post by Quackers on 2010-10-02
They are definitely left from Windows. Recycler is a Windows folder.

---

### Post by ze3rax on 2010-10-02
That's really odd Quackers - I've added the GParted on spare USB flash and after booting up and getting in the GUI it shows the following:

unallocated 299.09 GiB /dev/sda
fat32 3.82 Gib /dev/sdb

The main idea of the thread is moving to another. Previous problem solved. Will try to find solution.

---

### Post by Quackers on 2010-10-02
Hi ze3rax
it does seem as though there is a problem with your partition table. There is something that has been bothering me though. In your first post you say that you "removed my Win7 completely and on it's hard disk partition" but in a recent post you showed that there were still Windows folders on the disc. This may be the problem. How did you remove Windows? Did you delete the partition or try to resize it? And if so what with?

---

### Post by ze3rax on 2010-10-02
Okay , let's start over Quackers :

On my 320 GB HDD I had 3 partitions when was using win7 :

~ 20 GB - Labeled  " Win7 " [ OS installation and nothing more in it ]
~ 100 GB - Labeled " Software " [ Programs, music, photos ]
~ 190 GB - Labeled "Downloads" [ Mainly torrent files ]

I've started my installation of Ubuntu as many Win users will when they are preinstalling the OS:
* Pointed the 20 GB partition - made of it 16 GB ext3 part and ~5 GB swap [ It was strange for me to find out that in Windows we do have less space for use than here. Obviously the 1st partition was not 20 GB but 21. There's nothing to bother you, it's just my finding ] The ex-Windows partition was 1st formated, after that it was separeted as explained  *All that partitioning was made in the intaller*

* Ubuntu was installed in that new ext3 partition and I was not sure if I've to delete those folders mentioned before - Recycle, System Volume information . . . [ was unsure if Linux also has common folders because under Win those were invisible - I've seen them and cleaned 'em when I had viruses with a Live CD of Linux ]

I'm aware of the fact [ after reading bunch of threads, posts and useless stuff ] that I've problems with the partition table [ it's a new term for me and still trying to find the equivalent of that problem with Windows ]

That's all

Edit: I'm adding a Win7 screenshot to understand the partitions if needed : [http://img405.imageshack.us/img405/2092/tributeshot.jpg](http://img405.imageshack.us/img405/2092/tributeshot.jpg)

---

### Post by Quackers on 2010-10-02
We need to make sure of some things.
Please go to this link and download the boot_info_script and run it. This will create a results.txt file on your desktop. Please include the contents of that in your next post in CODE TAGS (click on New Reply instead of quick reply and click on the # on the top bar then right-click and paste the contents of the results.txt file).

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by oldfred on 2010-10-02
Show us the output of this as it will show you current partition.
```
sudo fdisk -lu
```

Linux & gparted have trouble mounting NTFS partitions that have the chkdsk flag or hibernate flag set. They do not mount so as not to further damage the NTFS partition that chkdsk may be able to repair.

---

### Post by ze3rax on 2010-10-02
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *          2,046   625,121,279   625,119,234   f W95 Ext d (LBA)
/dev/sda5         251,658,288   625,121,279   373,462,992   7 HPFS/NTFS
/dev/sda6               2,048     9,764,863     9,762,816  82 Linux swap / Solaris
/dev/sda7           9,766,912    41,945,087    32,178,176  83 Linux
Invalid MBR Signature found
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2: PTTYPE="dos" 
/dev/sda5        98B492EAB492CA60                       ntfs       Downloads                     
/dev/sda6        31547fda-1108-4365-be6c-8cecedcafd50   swap                                     
/dev/sda7        348d17f3-0d79-4a86-95fa-6980216c3f90   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro)
/dev/sda5        /media/Downloads         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 348d17f3-0d79-4a86-95fa-6980216c3f90
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 348d17f3-0d79-4a86-95fa-6980216c3f90
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 348d17f3-0d79-4a86-95fa-6980216c3f90
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=348d17f3-0d79-4a86-95fa-6980216c3f90 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 348d17f3-0d79-4a86-95fa-6980216c3f90
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=348d17f3-0d79-4a86-95fa-6980216c3f90 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 348d17f3-0d79-4a86-95fa-6980216c3f90
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=348d17f3-0d79-4a86-95fa-6980216c3f90 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 348d17f3-0d79-4a86-95fa-6980216c3f90
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=348d17f3-0d79-4a86-95fa-6980216c3f90 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 348d17f3-0d79-4a86-95fa-6980216c3f90
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 348d17f3-0d79-4a86-95fa-6980216c3f90
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=348d17f3-0d79-4a86-95fa-6980216c3f90 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=31547fda-1108-4365-be6c-8cecedcafd50 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  11.7GB: boot/grub/core.img
  11.0GB: boot/grub/grub.cfg
  11.1GB: boot/initrd.img-2.6.32-24-generic
  11.1GB: boot/initrd.img-2.6.32-25-generic
  11.0GB: boot/vmlinuz-2.6.32-24-generic
  11.0GB: boot/vmlinuz-2.6.32-25-generic
  11.1GB: initrd.img
  11.1GB: initrd.img.old
  11.0GB: vmlinuz
  11.0GB: vmlinuz.old
```


---------------------------------------


```
omitting empty partition (8)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea0aa0cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        2046   625121279   312559617    f  W95 Ext'd (LBA)
/dev/sda5       251658288   625121279   186731496    7  HPFS/NTFS
/dev/sda6            2048     9764863     4881408   82  Linux swap / Solaris
/dev/sda7         9766912    41945087    16089088   83  Linux

Partition table entries are not in disk order

```

---

### Post by Quackers on 2010-10-02
Have you looked at oldfred's post, one up?

---

### Post by ze3rax on 2010-10-02
The results are beneath those you requested and the NTFS partition is unmounted atm.

If that's what you ask. Also here's some additional info:

[]("http://img829.imageshack.us/img829/4555/screenshotdevsdagpartedl.png")[[IMG]http://img697.imageshack.us/img697/2312/screenshotdevsdagparted.th.png[/IMG]]("http://img697.imageshack.us/i/screenshotdevsdagparted.png/")


[[IMG]http://img685.imageshack.us/img685/192/screenshot320gbharddisk.th.png[/IMG]]("http://img685.imageshack.us/i/screenshot320gbharddisk.png/")

---

### Post by Quackers on 2010-10-02
Ah, so I see.
I really don't know what to suggest. I don't know how significant the invalid MBR signature is, or could become. It seems sda8 could be at the root of your partition table problems.
It would be good to know what oldfred thinks about your circumstances. Maybe he'll come back :-)
Is it possible that you could back up all your data to a seperate drive? As much as I hate to suggest it I'm thinking it may be an option to re-install Ubuntu using all of the disc.

---

### Post by ze3rax on 2010-10-02
Yes indeed. I'm looking for extermal HDD to back up all downloads but untill now - no success at all and whole day wasted for me in reading stuff...

---

### Post by Quackers on 2010-10-02
I know what you mean. When you got Ubuntu booted up I thought our troubles were over :-(
I was hoping it wouldn't be necessary to re-install but it may be safest. 
In the meantime we will see if anybody else can come up with a better solution.

---

### Post by ze3rax on 2010-10-02
Hey cheer up ! :D After all you've learned me to fix that "GRUB" alien :) If I manage to move all my data on external HDD I'll reinstall Ubuntu for sure. But let's see if others got more ideas :)

---

### Post by Quackers on 2010-10-02
Yes, lets hope so.

---

### Post by ze3rax on 2010-10-02
So all ended with friends huge external hard drive for backing up my files. 

To sum up : I'm not happy with that 1st impression Ubuntu made...[-X

---


---
title: "Grub is messed up after I upgraded to 10.4"
date: 2010-05-03
forum: General Help
---

### Post by kokkus on 2010-05-03
Hey. when I'm in the grub list and I click on windows 7, a black screen comes up and then it goes back to grub.
So something must have happened during the ubuntu installation.
How do I fix this problem?

---

### Post by kokkus on 2010-05-03
OK I am SO fücking pissed now.
I used testdisk to fix this shït but you know what happend? Now ubuntu can't mount the windows disk.  
Someone plz help me with this thing. I am sick and tired of all these problems with ubuntu. And 10.4 is suppose to be an LTS version?

---

### Post by kokkus on 2010-05-03
And I can't use the windows boot fixer tool because the PC came with windows installed so I don't have the CD.  I know I overwrote the windows boot file during the ubuntu installation but how can I fix it. I think I have tried everything I found on this forum but I don't wanna mess things up so I am a bit scared to try too many things. Can someone plz help me with this. There are like 100 posts about this and none of them helped me much. Many of them are even unsolved so I hope ubuntu will do something about this and make a tool to fix the mbr problems.

---

### Post by GSF1200S on 2010-05-03
> **kokkus said:**
> And I can't use the windows boot fixer tool because the PC came with windows installed so I don't have the CD.  I know I overwrote the windows boot file during the ubuntu installation but how can I fix it. I think I have tried everything I found on this forum but I don't wanna mess things up so I am a bit scared to try too many things. Can someone plz help me with this. There are like 100 posts about this and none of them helped me much. Many of them are even unsolved so I hope ubuntu will do something about this and make a tool to fix the mbr problems.

What is the output when you put:
```
sudo update-grub2
```
in a terminal?

Go here and download this boot script:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Lets say you have it downloaded to your desktop. You would run like:
```
sudo bash ~/Desktop/boot_info_script055.sh
```

It will create a RESULTS.TXT file- paste the contents here.

---

### Post by spiky001 on 2010-05-03
You cold try looking for a win7 boot disc on net or you can make 1 from another copy of win7

---

### Post by kokkus on 2010-05-03
OK thanks. here's the script output:

Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sdb1 for information... 
Finished.

---

### Post by kokkus on 2010-05-03
> **spiky001 said:**
> You cold try looking for a win7 boot disc on net or you can make 1 from another copy of win7
Yea I don't think I wanna install a pirate copy of win7.
Or is the boot cd legal and free?

---

### Post by spiky001 on 2010-05-03
no is free because they supply os on machine not on cd it,s just so you can get back in
You can make 1 off another win7 machine as well

---

### Post by dino99 on 2010-05-03
Beans: 563  : i'm sure ( i hope) you have not made the common newbie fault of installing grub over the windows bootloader, dont you ?

if you had previously grub ( = grub1=grub-legacy) installed , you first need to remove/purge with synaptic ALL the grub packages installed, then install grub-pc and grub-common (menu.list need to be removed), then:

sudo grub-mkconfig && update-grub

---

### Post by GSF1200S on 2010-05-03
> **kokkus said:**
> OK thanks. here's the script output:

Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sdb1 for information... 
Finished.

No, thats the output in the terminal. The script creates a file called RESULTS.TXT that has the information I need contained in it. Did you run update-grub2? What did it say?

---

### Post by kokkus on 2010-05-03
> **dino99 said:**
> Beans: 563  : i'm sure ( i hope) you have not made the common newbie fault of installing grub over the windows bootloader, dont you ?

if you had previously grub ( = grub1=grub-legacy) installed , you first need to remove/purge with synaptic ALL the grub packages installed, then install grub-pc and grub-common (menu.list need to be removed), then:

sudo grub-mkconfig && update-grub
You mean I must remove everything i can find with the word grub? That sounds dangerous.

---

### Post by dino99 on 2010-05-03
> **kokkus said:**
> You mean I must remove everything i can find with the word grub? That sounds dangerous.

we are not April 1th :P
of course dont reboot  !!!! before installing the 2 needed packages

---

### Post by GSF1200S on 2010-05-03
> **kokkus said:**
> You mean I must remove everything i can find with the word grub? That sounds dangerous.

No, its not dangerous. You can just do:
```
sudo apt-get purge grub
```
then do:
```
sudo apt-get install grub-pc grub-common
```
and then:
```
sudo update-grub2
```
and take a look at the output. It should mention Windows. After done and before you restart, will you please post the contents of RESULTS.TXT? That would help us.

---

### Post by kokkus on 2010-05-03
ok I did but ubuntu can still not mount the win7 partition and now I don't even have the win7 os in the grub list.
Is it really possible that I can have deleted the win7 partition when I used testdisk to repair grub?
OMG all this frustration just because Ubuntu didn't install grub correctly.
So what can I do now?

---

### Post by dino99 on 2010-05-03
what is dangerous is to make things you dont understand :confused:

but be happy, Lucid is able to do all you want even run windoz's apps with wine (winehq), no more blue screen of death or flooding by virus, nice dont you ...

now you can erase bill's spyware LOL

---

### Post by spiky001 on 2010-05-03
post 
```
sudo fdisk -l
```

---

### Post by kokkus on 2010-05-03
> **dino99 said:**
> what is dangerous is to make things you dont understand :confused:
you are not helping. As I said, I have tried almost everything on this forum to fix this problem, and I have no idea what i am doing when it comes to all that advanced pc geek stuff.
I just want it to work again. It's frustrating how ubuntu must always make things harder then it has to be. IN the installation, why did it ask for the grub thing? I guess 90 procent of us are lost when it comes to stuff like that.
All the older versions of ubuntu installed the grub thing automatically.
ANyway, I just want this thing fixed now.
Please help.

---

### Post by kokkus on 2010-05-03
> **spiky001 said:**
> post 
```
sudo fdisk -l
```
Ok thanks, here's the output.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27fc082a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1914       18279   131458852    7  HPFS/NTFS
/dev/sda2           31355       60802   236533760    7  HPFS/NTFS
/dev/sda3           18280       31354   105024937+   5  Extended
/dev/sda5           18280       30817   100711453+  83  Linux
/dev/sda6           30818       31354     4313421   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by singercs on 2010-05-03
I had the same issue and I was using xp, I finally had to bit the bullet and try to reinstall but it wouldn't take so I tried a vista disc and that installed but wouldn't boot, I then installed win7 that booted once then nothing, I used a 9.04 disc to reinstall something that I could use and that took three tries to install past 68%, after it finally installed everything seemed great until I had to shut down my machine, it didn't want to shut down so I got sick and tired of this crap and wiped the HDD and started from a fresh disc, I did loose all my files etc however I now have a great working 10.4.

I did the upgrade on my daughters 600mh dell and that went without a hitch and works great with 256m ram.

---

### Post by spiky001 on 2010-05-03
I think you have to get win running 1st then redo grub

---

### Post by kokkus on 2010-05-03
> **spiky001 said:**
> I think you have to get win running 1st then redo grub

ok sure but how?
I got the win 7 cd now from a friend so how do I repair the boot file?

---

### Post by dino99 on 2010-05-03
google: windows+mbr

---

### Post by john newbuntu on 2010-05-03
I had this link handy.  See the section on restoring win 7 boot loader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kokkus on 2010-05-03
thanks but the win7 cd can't find the driver.
So I think I have deleted or unmounted the win7 hdd.
Coz when I boot up ubuntu it tries to mount that disk but I always choose SKIP. The first time I tried to let it mount but I gave it up after 30 minutes mounting process.
So is the partition gone or what do you guys think? is there any hope or do I have to reinstall the ***** windows again?

---

### Post by GSF1200S on 2010-05-03
> **kokkus said:**
> thanks but the win7 cd can't find the driver.
So I think I have deleted or unmounted the win7 hdd.
Coz when I boot up ubuntu it tries to mount that disk but I always choose SKIP. The first time I tried to let it mount but I gave it up after 30 minutes mounting process.
So is the partition gone or what do you guys think? is there any hope or do I have to reinstall the ***** windows again?

In Ubuntu, run:

```
sudo mount /dev/sda1 /mnt
```
Then open your file manager and navigate to /mnt- is any windows data in there? I can clearly see your ntfs partitions listed by fdisk -l.

Is Windows installed on /dev/sda2? Then replace 1 with 2 in the above command. I think your data is fine- its just that grub isnt loading Windows for some reason. Ive never had this issue, so im running out of ideas.

---

### Post by kokkus on 2010-05-03
But only one of them right?
Here's the output from the command you gave me:

Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

So what now?

---

### Post by GSF1200S on 2010-05-03
> **kokkus said:**
> But only one of them right?```
[CODE]
```[/CODE]
Here's the output from the command you gave me:

Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

So what now?

Unmount /dev/sda1:
```
sudo umount /dev/sda1
```
then run:
```
sudo apt-get install ntfsprogs
```
and finally run:
```
sudo ntfsfix /dev/sda1
```

Then, try to remount that partition:
```
sudo mount /dev/sda1 /mnt
```
Hopefully that message will be gone- it seems like this doesnt have anything to do with Grub- it seems like the ntfs file system on Windows is messed up :(

---

### Post by kokkus on 2010-05-03
ok after i ran the command sudo umount /dev/sda1 it says its not mounted, should I just continue anyway?

---

### Post by kokkus on 2010-05-03
It had something to do with grub, until I tried to fix it using testdisk.
Anyway, I tried everyhting you said but sudo mount /dev/sda1 /mnt didn't mount the disk.
But I can see it but when I click on it, the error msg comes up.

---

### Post by GSF1200S on 2010-05-03
> **kokkus said:**
> It had something to do with grub, until I tried to fix it using testdisk.
Anyway, I tried everyhting you said but sudo mount /dev/sda1 /mnt didn't mount the disk.
But I can see it but when I click on it, the error msg comes up.

What was the error message when you tried to mount? That sucks though- if it was a grub problem we could have got it sorted :(

I would run a windows recovery disk and try to run chkdsk C: /R

See this link:
[http://vlaurie.com/computers2/Articles/chkdsk.htm](http://vlaurie.com/computers2/Articles/chkdsk.htm)

Hopefully it can repair the filesystem and get you going again.

---

### Post by kokkus on 2010-05-03
Thanks, I'll try.
Oh and by the way, the win7 cd couldn't locate windows.
The c: disk says 0 b, so it is there but not mounted.

here's the error msg:
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/E2F45950F45927D5

I tried to mount it via root terminal but no luck.

---

### Post by kokkus on 2010-05-03
ok so now I have tried with a win7 recovery cd and when I click the Load Driver button, I can't access c: but my 2nd disk works fine and it seems that the ubuntu installation made a new partition in windows called boot (x:) So my c: partition is still there but I can't mount it nometter what I try. When I boot into ubuntu it tries to mount the disk but with no luck.
I am really desperate now. And no, I can't just reinstall windows since the partition is unmounted, and I don't wanna format the whole thing and loose all my files.

---

### Post by DomesDKG on 2010-05-03
Have you seen this solution on sourceforge?
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by kelvin spratt on 2010-05-03
You need to run 
"sudo os-prober"     then run "sudo update-grub2" 
It does what it says on the packet

---

### Post by kokkus on 2010-05-03
> **DomesDKG said:**
> Have you seen this solution on sourceforge?
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Yes I Have tried that one and that is why its unmounted now..
I only had a grub problem before I tried the testdisk solution.

> **kelvin spratt said:**
> You need to run 
"sudo os-prober"     then run "sudo update-grub2" 
It does what it says on the packet

Thanks but no luck there.
The win7 partition will still not mount.

Sudo os-prober gave me the following errors:


ls: reading catalog /var/lib/os-prober/mount: Input/output error
ls: reading catalog /var/lib/os-prober/mount: Input/output error
ls: reading catalog /var/lib/os-prober/mount: Input/output error
ls: reading catalog /var/lib/os-prober/mount: Input/output error

So, what now?

---

### Post by oldfred on 2010-05-03
We can keep guessing what your problems are or you can post the results.txt. The last thing it said on the command line was where it saved a copy of results.txt. Copy it here and put it inside code tags by using the # when the entire results.txt copy is highlighted. The # is on the edit panel just able where you are editing. You should rerun it if some changes have been make.

Window7 if  a new install creates a 100MB boot partition and then the install partition as standard.

---

### Post by kokkus on 2010-05-03
ok here's my result.txt file:

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 293936934 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 293936798 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     30,734,336   293,652,039   262,917,704   7 HPFS/NTFS
/dev/sda2         503,703,552   976,771,071   473,067,520   7 HPFS/NTFS
/dev/sda3         293,652,135   503,702,009   210,049,875   5 Extended
/dev/sda5         293,652,198   495,075,104   201,422,907  83 Linux
/dev/sda6         495,075,168   503,702,009     8,626,842  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7969 MB, 7969177600 bytes
221 heads, 20 sectors/track, 3521 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192    15,564,799    15,556,608   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        E2F45950F45927D5                       ntfs                                     
/dev/sda2        3C40DE6740DE2802                       ntfs       DATA                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f76f87d5-7a20-4cdb-8d89-615e2ae3cad5   ext4                                     
/dev/sda6        890c10fd-823d-4c44-90f9-68511f659265   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0018-AA10                              vfat       FEDORA                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/FEDORA            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set f76f87d5-7a20-4cdb-8d89-615e2ae3cad5
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
search --no-floppy --fs-uuid --set f76f87d5-7a20-4cdb-8d89-615e2ae3cad5
set locale_dir=($root)/boot/grub/locale
set lang=nb
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f76f87d5-7a20-4cdb-8d89-615e2ae3cad5
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=f76f87d5-7a20-4cdb-8d89-615e2ae3cad5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f76f87d5-7a20-4cdb-8d89-615e2ae3cad5
	echo	'Loading Linux 2.6.32-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=f76f87d5-7a20-4cdb-8d89-615e2ae3cad5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f76f87d5-7a20-4cdb-8d89-615e2ae3cad5
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=f76f87d5-7a20-4cdb-8d89-615e2ae3cad5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f76f87d5-7a20-4cdb-8d89-615e2ae3cad5
	echo	'Loading Linux 2.6.31-20-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=f76f87d5-7a20-4cdb-8d89-615e2ae3cad5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f76f87d5-7a20-4cdb-8d89-615e2ae3cad5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f76f87d5-7a20-4cdb-8d89-615e2ae3cad5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda5 :
UUID=f76f87d5-7a20-4cdb-8d89-615e2ae3cad5	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda2 :
UUID=3C40DE6740DE2802	/media/DATA	ntfs	defaults,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077	0	0
#Entry for /dev/sda1 :
UUID=E2F45950F45927D5	/media/E2F45950F45927D5	ntfs	defaults,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077	0	0
#Entry for /dev/sda6 :
UUID=890c10fd-823d-4c44-90f9-68511f659265	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0



=================== sda5: Location of files loaded by Grub: ===================


 150.4GB: boot/grub/core.img
 156.9GB: boot/grub/grub.cfg
 151.6GB: boot/initrd.img-2.6.31-20-generic-pae
 161.7GB: boot/initrd.img-2.6.32-21-generic-pae
 150.9GB: boot/vmlinuz-2.6.31-20-generic-pae
 151.1GB: boot/vmlinuz-2.6.32-21-generic-pae
 161.7GB: initrd.img
 151.6GB: initrd.img.old
 151.1GB: vmlinuz
 150.9GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ls: lesing av katalog sda1/: Input/output error 
```

So can you tell me now what the problem is and how I can fix it?

---

### Post by kokkus on 2010-05-03
It says "no error found" all the way here so I guess this problem doesn't have much to do with grub anymore now does it?
I mean even if grub could read windows 7, win7 wouldn't be able to start since the partition is unmounted.
I mean I have no idea really but from what I can see in this txt file it seams to be no connection between grub and the win partition. I have no idea.

---

### Post by kokkus on 2010-05-03
New discover;
I tried to use testdisk again and on my NTFS disk I clicked undelete instead of boot, all the files were there so they still exist.
Ok so now I know they aren't gone. 
But I assume that the partition is not only unmounted but also deleted since it says undelete. SO how do I recover the partition now?

---

### Post by oldfred on 2010-05-03
The script shows no windows files - are they deleted or is the script not seeing files? The boot flag is still on sda1 so that would normally be the the windows boot partition. You also installed grub to sda2. You may have recovered the boot block but the rest of the system looks like it is missing. If testdisk can recover I would try it.

---

### Post by bep7987 on 2010-05-04
I had a similar problem with the grub2 update.  Why the update doesn't read the settings from the previous installation is beyond me.

Anyway, this is what I did:
[INDENT] Using the Windows 7 disc you borrowed, boot from the disc and select repair mode.

[http://windows.microsoft.com/en-us/windows7/What-are-the-system-recovery-options-in-Windows-7](http://windows.microsoft.com/en-us/windows7/What-are-the-system-recovery-options-in-Windows-7)

Chose startup repair, which will scan your system for windows installations.

Select yours from the list and click repair.  It will run a series of test and may or may not reboot one or more times.

After the repair is done, reboot your system.

If the repair was successful, you'll boot into windows, if not, boot from the  Windows 7 cd again, this time selecting command prompt from the list of choices.
[/INDENT][INDENT] (I had to use the command prompt and run the commands below.)

At the command prompt, type:

bootrec.exe /fixmbr [enter]
bootrec.exe /fixboot [enter]
bootrec.exe /rebuildbcd [enter]

Then reboot your system.

[/INDENT]That fixed my boot problems.
   
Except now I couldn't boot into linux, so I followed these instructions to reinstall grub2 from a live cd:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Now my system boots up the way it did before the upgrade--into grub where I can select windows or ubuntu.

I hope this works for you.

---

### Post by kokkus on 2010-05-04
Well, that's not exectly the problem.
I overwrote the windows partition with a new boot partition when I upgraded to ubuntu 10.04 so the windows partition god deleted.
But ok it's too late now anyway. I formated the whole thing and reinstalled windows 7. And now I have decided to stay away from ubuntu. Too bad because I really like ubuntu but for a LTS version I must say version 10.04 gave me  too many problems.
And ubuntu are giving me way too much pc work only to repair, fix and stuff like that. It's too advanced and geeky for me I guess. It really gives me too much frustration if you know what I mean.
But one thing, if I give ubuntu another chance, what alternative do I choose when that grub thing comes up, so I don't do the same error again?

---

### Post by oldfred on 2010-05-05
I am still on Karmic which gave me no problems with grub2. My test install of Lucid had some video issues needed nomodeset but once Nvidia was installed it works well.

If you have one drive you can just install grub2 to sda not sda1 or any partitions. If two drives keep windows and its boot loader on one drive and install Ubuntu and grub to the second drive's MBR sdb. Either case grub will find windows and let you boot either Ubuntu or windows. The key is to know to use the advanced button (screen#8 of lucid install) on the last screen that says ready to instal, to control where grub is installed.

---


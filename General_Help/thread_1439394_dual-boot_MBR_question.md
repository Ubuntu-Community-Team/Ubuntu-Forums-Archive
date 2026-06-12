---
title: "dual-boot MBR question"
date: 2010-03-26
forum: General Help
---

### Post by eltopo1 on 2010-03-26
Hello,

I have an XP / Karmic dual-boot, with a fresh install of 9.10 (after XP), and the boot loader installed on the disk's mbr. Now Windows is giving me the kind of grief that would usually have me reaching for the cd to do Windows Repair, or even a fresh install - but isn't that going to mess up the mbr? Will I have to reinstall the grub again? Or can I reinstall freely, since the exact same XP will be installed on the same partition where it was when I installed Ubuntu and configured the bootloader in the first place?

Thanks in advance, this is a great community

---

### Post by velle frak on 2010-03-26
I'm not sure, but I think a new installation of XP will rewrite your MBR.

Maybe you could use a live CD partitioning program afterwards to reactivate GRUB?

---

### Post by timgood on 2010-03-26
You can get info on installing Windows while maintaining your Ubuntu installation [here]("https://help.ubuntu.com/community/WindowsDualBoot")

You will need to re-install Grub from a live CD session, but it is a fairly simple procedure and well documented in this Howto.

Hope this helps.

---

### Post by ajgreeny on 2010-03-26
Installing windows will definitely overwrite the grub presently on the MBR with the windows bootloader, but don't worry too much, you can easily restore grub again with the ubuntu live CD

How to restore the Ubuntu grub bootloader (9.10 and beyond)

Ubuntu 9.10 uses Grub 2, so you need to find out what your drives are using live CD:
```
sudo fdisk -l
```
From that you need to find the device name of your Ubuntu drive, something like &#8220;/dev/sda5&#8243;.
Still in the terminal, type:
```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```
To reinstall grub:
```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```
Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.

---

### Post by eltopo1 on 2010-03-26
Thanks a lot for the quick answers - I will give that last reply a try.

---

### Post by eltopo1 on 2010-03-30
Hello,

So here's the result of my fdisk -1:


> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24b824b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19585   157316481    7  HPFS/NTFS
/dev/sda2           19586       30401    86879520    5  Extended
/dev/sda5           20072       21895    14651248+  83  Linux
/dev/sda6           21896       30401    68324413+  83  Linux
/dev/sda7           19586       20071     3903732   82  Linux swap / Solaris

sda1 is Windows, sda5 the Ubuntu filesystem, sda6 is Home. I'm running Grub 2.6.31.

Just want to make sure that in this case it's **sda5** that I'll have to mount with the Livecd, and reinstall Grub in?

Thanks again

---

### Post by lotharmat on 2010-03-30
Would sda1 (which has the boot flag on it) be the one?

---

### Post by eltopo1 on 2010-04-03
Thanks for your answer... but color me confused now. Why would I reinstall Grub on the Windows partition, surely it has to point to the Ubuntu partition (as the default partition to load)? And in my case I actually have to follow ajgreeny's instructions to the letter (inc the partition number)? 

Anyone? Sorry but I want to be 100% sure before proceeding, I've already had to reinstall Ubuntu once this month, that's enough for me...

---

### Post by yetiman64 on 2010-04-03
eltopo1, 

Grubs files exist in /boot/grub but its bootcode is loaded to the MBR of the HDD.

1 What is the grief you mention that windows is giving and can you currently boot both windows and ubuntu? 

2 Yes a windows repair disk will destroy by overwriting the MBR bootcode of grubs - try to avoid doing this as re-installing grub although possible is difficult (and I have done it due to reinstalling windows in dual boot setups). However when ubuntu is installed 2nd grub "plays the game nice" and allows for booting windows.

Please explain windows behaviour a bit before touching its install disc as someone may sort its problem for you without massive dual boot headaches

---

### Post by louieb on 2010-04-03
> **eltopo1 said:**
> ..., I've already had to reinstall Ubuntu once this month, that's enough for me...

:DPractice make perfect. - when your done reinstalling windows - ajgreeny 	 		in post #4  - shows how to get GRUB working again.

---

### Post by eltopo1 on 2010-04-03
I installed Windows, did the updates (inc SP3), started installing the programs, and Office gives me hassle - asks for the XP cd, but rejects it when I put it in. These are cds I've used countless times at work, and in that order, and they've never done this. The only change I can think of is that this time I fiddled around with the theme (making the fonts bigger etc), which does ask for the Windows cd - possibly while Windows was updating in the background. Some people have told that this can corrupt Windows.

Thing is, I embarked on this whole thing precisely to have really clean installations of both Windows and Ubuntu, image the whole disk, and then be sorted from now on. If Windows is already giving me grief while I'm still in the setup process, there's no point in backing it up.

You don't think ajgreeny's advice is the way to go? From what I've read elsewhere it should work, I just want to be sure about the partition numbers.

---

### Post by yetiman64 on 2010-04-03
<info: unreliable method in previous post link and has been changed, and is out of date for karmic>

Refer grub2 guide or check and if consistent give it a try, sorry fellas,  @ louieb  I'll be checking out the scripts below myself now as I'm dual booting Lucid 10.4 & Jaunty 9.04 upgraded to grub2 with MS OS (Tri boot). Thanks

looks pretty much as is with ajgreeny - apologies for any confusion.

I'll review more  before posting next

---

### Post by louieb on 2010-04-03
In post #6 you said sda6 was /home. that leaves sda5 to be your / root partition.  

to be sure run the script - post the results.txt - [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")

---

### Post by eltopo1 on 2010-04-03
> ============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 778236795.
    Operating System:  
    Boot files/dirs:   


So reinstalling the grub on SDA5, as per ajgreeny's post? That will automatically set up the MBR in SDA, which will point to SDA5, have I got that right?

Thanks

---

### Post by yetiman64 on 2010-04-03
That does look ok to me. But I'd wait for confirmation from louieb now I've seen the scripting and realize the methods between grub and grub2 have changed so drastically.

 If anything this has convinced me to dump Vista totally, install multiple Ubuntu and other linuxes (as they can have there bootloaders in their root partition and be booted from another bootloader such as GAG without having to chainload through grub). I'm very lucky not to be in this situation considering Vista and 2 grub2 Ubuntus are on this machine.

Once again apologies for any confusion I may have caused.

I was currently ready to clean out and reinstall Vista, but now have decided to waste the $$$ on vista and go 100 % Ubuntu and other linuxes.

Thanks for the insight louieb

---

### Post by oldfred on 2010-04-03
Your grub2 already shows that. Are you trying to boot from sda? But sometimes grub has to be reinstalled. ajgreeny's post looks correct.

You did not post to full  script so we cannot see if there is something else missing or misnumbered. It is also easier to review if it is in a code box. Paste, Highlight and click the # in the top edit panel.

---

### Post by eltopo1 on 2010-04-03
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
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 778236795.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24b824b7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   314,633,024   314,632,962   7 HPFS/NTFS
/dev/sda2         314,633,025   488,392,064   173,759,040   5 Extended
/dev/sda5         322,440,678   351,743,174    29,302,497  83 Linux
/dev/sda6         351,743,238   488,392,064   136,648,827  83 Linux
/dev/sda7         314,633,151   322,440,614     7,807,464  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00007823

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   409,593,239   409,593,177   b W95 FAT32
/dev/sdb2         409,593,240   778,236,794   368,643,555   b W95 FAT32
/dev/sdb3         778,236,795   976,768,064   198,531,270   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        CEF81343F813296B                       ntfs                                     
/dev/sda5        1044dd7c-db9c-4e2b-a9c1-ff36e210b617   ext4                                     
/dev/sda6        cc04a029-b4b9-4958-90d9-f88506774594   ext4                                     
/dev/sda7        7e5d90a6-a795-4bfd-b78a-e319a4584fee   swap                                     
/dev/sdb1        BD41-1F70                              vfat       MUZ                           
/dev/sdb2        D7A8-B7BB                              vfat       MOVIEZ                        
/dev/sdb3        D91E-6728                              vfat       TOPO                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/MUZ               vfat       (rw,noexec,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,umask=0000)
/dev/sdb2        /media/MOVIEZ            vfat       (rw,noexec,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,umask=0000)
/dev/sdb3        /media/TOPO              vfat       (rw,noexec,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,umask=0000)
/dev/sda6        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect

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
search --no-floppy --fs-uuid --set 1044dd7c-db9c-4e2b-a9c1-ff36e210b617
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
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
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1044dd7c-db9c-4e2b-a9c1-ff36e210b617
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1044dd7c-db9c-4e2b-a9c1-ff36e210b617 ro  vga=799  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1044dd7c-db9c-4e2b-a9c1-ff36e210b617
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1044dd7c-db9c-4e2b-a9c1-ff36e210b617 ro single  vga=799
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professionnel (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set cef81343f813296b
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
UUID=1044dd7c-db9c-4e2b-a9c1-ff36e210b617 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=cc04a029-b4b9-4958-90d9-f88506774594 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=7e5d90a6-a795-4bfd-b78a-e319a4584fee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1                                  /media/MUZ      vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0
/dev/sdb2                                  /media/MOVIEZ   vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0  
/dev/sdb3                                  /media/TOPO     vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0 

=================== sda5: Location of files loaded by Grub: ===================


 165.3GB: boot/grub/core.img
 166.1GB: boot/grub/grub.cfg
 168.7GB: boot/initrd.img-2.6.31-20-generic-pae
 167.7GB: boot/vmlinuz-2.6.31-20-generic-pae
 168.7GB: initrd.img
 167.7GB: vmlinuz
```

---

### Post by oldfred on 2010-04-03
I do not see anything else in your script that looks like a problem.

Just a comment, you are using FAT for data storage. It has a maximum file size of 4GB less one byte. Any file large will not be saved correctly and usually you do not get any errors saying it lost data. Also FAT is not journalized like NTFS or EXT3 or EXT4. Journals allow easier/better recovery from hard disk errors.

---

### Post by louieb on 2010-04-03
The boot info script confirms that sda5 is the / (root) partition. After re-installing windows - the instructions in post #4 will work to get GRUB back as the bootloader.

---

### Post by eltopo1 on 2010-04-04
It worked perfectly :guitar:

THANK YOU everyone who posted


Love this place :p

---

### Post by eltopo1 on 2010-04-05
Actually I talked too soon :mad:

I cant access Windows when I choose it in the grub - says something about not finding sda1

And then the weird thing is that Gparted shows my whole drive as unallocated, like there are no partitions at all.

It was already the case when I used the Livecd, and also my partition numbers had already changed (filesystem sda5 is now sda3 for some reason), but I figured it was because the livecd was using its own numbers to mount the partitions.

Confused...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 778236795.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24b824b7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   314,633,024   314,632,962   7 HPFS/NTFS
/dev/sda2         314,633,025   488,392,064   173,759,040   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5         314,633,151   322,440,614     7,807,464  82 Linux swap / Solaris
/dev/sda6         351,743,238   488,392,064   136,648,827  83 Linux
/dev/sda3         322,440,678   351,743,174    29,302,497  83 Linux

/dev/sda2 overlaps with /dev/sda3

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00007823

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   409,593,239   409,593,177   b W95 FAT32
/dev/sdb2         409,593,240   778,236,794   368,643,555   b W95 FAT32
/dev/sdb3         778,236,795   976,768,064   198,531,270   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C2CCCBFECCCBEB2D                       ntfs                                     
/dev/sda3        1044dd7c-db9c-4e2b-a9c1-ff36e210b617   ext4                                     
/dev/sda5        7e5d90a6-a795-4bfd-b78a-e319a4584fee   swap                                     
/dev/sda6        cc04a029-b4b9-4958-90d9-f88506774594   ext4                                     
/dev/sdb1        BD41-1F70                              vfat       MUZ                           
/dev/sdb2        D7A8-B7BB                              vfat       MOVIEZ                        
/dev/sdb3        D91E-6728                              vfat       TOPO                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/MUZ               vfat       (rw,noexec,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,umask=0000)
/dev/sdb2        /media/MOVIEZ            vfat       (rw,noexec,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,umask=0000)
/dev/sdb3        /media/TOPO              vfat       (rw,noexec,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,umask=0000)
/dev/sda6        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root=(hd0,3)
search --no-floppy --fs-uuid --set 1044dd7c-db9c-4e2b-a9c1-ff36e210b617
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
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
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 1044dd7c-db9c-4e2b-a9c1-ff36e210b617
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1044dd7c-db9c-4e2b-a9c1-ff36e210b617 ro  vga=799  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 1044dd7c-db9c-4e2b-a9c1-ff36e210b617
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1044dd7c-db9c-4e2b-a9c1-ff36e210b617 ro single  vga=799
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professionnel (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c2cccbfecccbeb2d
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1044dd7c-db9c-4e2b-a9c1-ff36e210b617 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=cc04a029-b4b9-4958-90d9-f88506774594 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=7e5d90a6-a795-4bfd-b78a-e319a4584fee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1                                  /media/MUZ      vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0
/dev/sdb2                                  /media/MOVIEZ   vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0  
/dev/sdb3                                  /media/TOPO     vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0 

=================== sda3: Location of files loaded by Grub: ===================


 167.2GB: boot/grub/core.img
 166.8GB: boot/grub/grub.cfg
 168.7GB: boot/initrd.img-2.6.31-20-generic-pae
 167.7GB: boot/vmlinuz-2.6.31-20-generic-pae
 168.7GB: initrd.img
 167.7GB: vmlinuz
```

---

### Post by oldfred on 2010-04-05
One problem:
Extended  partition  linking to another extended partition

You can only have one extended partition, so you have an error in your partition table.

I am not real knowledgeable on partition table problems. I would first us sfdisk to make a backup like in this post. And if you understand what it says you may be able to use it to fix your problem as it writes a corrected table based on your input.
Using sfdisk to fix partition table problems 
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

I might try this after I had a backup:
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
else if it is not ok
then post the output of option p and v

Third choice is testdisk which you can also download with synaptic, It is fro all sorts of partition problems but do not know if it will easily fix your type of issue.
repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by eltopo1 on 2010-04-05
Thanks a lot for that - the strange thing is that now that Gparted is uninstalled, and I mounted the partition containing Windows in Ubuntu, things seem to work ok again... strange

---

### Post by oldfred on 2010-04-05
If you run this does it show any issues:

```
sudo fdisk -lu
```

---

### Post by eltopo1 on 2010-04-12
Yeah, there's definitely something fishy going on - everything works fine in practice, booting on either Windows or Ubuntu, so I was going to leave it like this, but even using Clonezilla to back up the whole disk won't work now, because of those partition issues.

The results of that script again:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 778236795.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24b824b7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   314,633,024   314,632,962   7 HPFS/NTFS
/dev/sda2         314,633,025   488,392,064   173,759,040   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5         314,633,151   322,440,614     7,807,464  82 Linux swap / Solaris
/dev/sda6         351,743,238   488,392,064   136,648,827  83 Linux
/dev/sda3         322,440,678   351,743,174    29,302,497  83 Linux

/dev/sda2 overlaps with /dev/sda3

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00007823

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   409,593,239   409,593,177   b W95 FAT32
/dev/sdb2         409,593,240   778,236,794   368,643,555   b W95 FAT32
/dev/sdb3         778,236,795   976,768,064   198,531,270   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C2CCCBFECCCBEB2D                       ntfs                                     
/dev/sda3        1044dd7c-db9c-4e2b-a9c1-ff36e210b617   ext4                                     
/dev/sda5        7e5d90a6-a795-4bfd-b78a-e319a4584fee   swap                                     
/dev/sda6        cc04a029-b4b9-4958-90d9-f88506774594   ext4                                     
/dev/sdb1        BD41-1F70                              vfat       MUZ                           
/dev/sdb2        D7A8-B7BB                              vfat       MOVIEZ                        
/dev/sdb3        D91E-6728                              vfat       TOPO                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/MUZ               vfat       (rw,noexec,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,umask=0000)
/dev/sdb2        /media/MOVIEZ            vfat       (rw,noexec,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,umask=0000)
/dev/sdb3        /media/TOPO              vfat       (rw,noexec,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,umask=0000)
/dev/sda6        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root=(hd0,3)
search --no-floppy --fs-uuid --set 1044dd7c-db9c-4e2b-a9c1-ff36e210b617
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
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
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 1044dd7c-db9c-4e2b-a9c1-ff36e210b617
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1044dd7c-db9c-4e2b-a9c1-ff36e210b617 ro  vga=799  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 1044dd7c-db9c-4e2b-a9c1-ff36e210b617
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1044dd7c-db9c-4e2b-a9c1-ff36e210b617 ro single  vga=799
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professionnel (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c2cccbfecccbeb2d
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1044dd7c-db9c-4e2b-a9c1-ff36e210b617 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=cc04a029-b4b9-4958-90d9-f88506774594 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=7e5d90a6-a795-4bfd-b78a-e319a4584fee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1                                  /media/MUZ      vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0
/dev/sdb2                                  /media/MOVIEZ   vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0  
/dev/sdb3                                  /media/TOPO     vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0 

=================== sda3: Location of files loaded by Grub: ===================


 167.2GB: boot/grub/core.img
 169.6GB: boot/grub/grub.cfg
 168.7GB: boot/initrd.img-2.6.31-20-generic-pae
 167.7GB: boot/vmlinuz-2.6.31-20-generic-pae
 168.7GB: initrd.img
 167.7GB: vmlinuz
```

I've attached a screenshot of the horror show that is how palimpsest sees that disk now - it seems to "see" both the real partitions, but also the space they take as unallocated? And how on earth can it see my swap partition as an extended one?!?

I'm in way over my head now, should I try to fix the partition tables using sfdisk or testdisk as Oldfred advised? Or is there something else I can try first?



Thanks

---

### Post by eltopo1 on 2010-04-12
And here's what *sudo fdisk -lu* says:

```
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24b824b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   314633024   157316481    7  HPFS/NTFS
/dev/sda2       314633025   488392064    86879520    5  Extended
/dev/sda3       322440678   351743174    14651248+  83  Linux
/dev/sda5       314633151   322440614     3903732   82  Linux swap / Solaris
/dev/sda6       351743238   488392064    68324413+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00007823

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   409593239   204796588+   b  W95 FAT32
/dev/sdb2       409593240   778236794   184321777+   b  W95 FAT32
/dev/sdb3       778236795   976768064    99265635    b  W95 FAT32
```

---


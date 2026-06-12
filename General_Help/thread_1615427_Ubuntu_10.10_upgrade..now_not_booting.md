---
title: "Ubuntu 10.10 upgrade..now not booting"
date: 2010-11-07
forum: General Help
---

### Post by rohitrp2003 on 2010-11-07
Hi

I upgraded my ubuntu 10.04 to 10.10 and now when i choose ubuntu from the grub loader only a command prompt comes. I can just write commands..all my files of ubuntu 10.04 are there also !! 
Please tell me how do I load properly!

---

### Post by garvinrick4 on 2010-11-07
> **rohitrp2003 said:**
> Hi

I upgraded my ubuntu 10.04 to 10.10 and now when i choose ubuntu from the grub loader only a command prompt comes. I can just write commands..all my files of ubuntu 10.04 are there also !! 
Please tell me how do I load properly!
Put in live cd (install cd for ubuntu) choose Try Ubuntu and when it boots start internet and go to this website and download the Script to DESKTOP and then run the code below in a terminal. Applications to Accessories to Terminal:
website to download:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
copy and paste this below into terminal.
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```Now there will be a file called RESULTS on your desktop:
copy and paste it to this thread. After you paste it here ir you highlight
the whole thing (it is long) and hit the # in upper right of message box you
will put it in a nice box for me to read it in. This whole thing takes about 
a minute to do.

---

### Post by rohitrp2003 on 2010-11-07
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 655. But according to the info from fdisk, 
                       sda6 starts at sector 405882880.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         81,920       286,719       204,800   7 HPFS/NTFS
/dev/sda2             286,720   327,761,919   327,475,200   7 HPFS/NTFS
/dev/sda4         327,763,966   976,771,071   649,007,106   5 Extended
/dev/sda5         327,763,968   335,575,039     7,811,072  82 Linux swap / Solaris
/dev/sda6         405,882,880   976,771,071   570,888,192   7 HPFS/NTFS
/dev/sda7         335,577,088   405,880,831    70,303,744  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        30C21529C214F4B6                       ntfs                                     
/dev/sda2        6E80FF4280FF0EF9                       ntfs       System                        
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5d54ed28-1450-4735-8bb1-80d3ac0498b4   swap                                     
/dev/sda6        980A7D120A7CEE9E                       ntfs       Data                          
/dev/sda7        364fc37a-062f-4e84-834b-c212fac3bbcf   ext3                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/Access Manager    iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda2        /media/System            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=364fc37a-062f-4e84-834b-c212fac3bbcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=364fc37a-062f-4e84-834b-c212fac3bbcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=364fc37a-062f-4e84-834b-c212fac3bbcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=364fc37a-062f-4e84-834b-c212fac3bbcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 30c21529c214f4b6
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=364fc37a-062f-4e84-834b-c212fac3bbcf /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5d54ed28-1450-4735-8bb1-80d3ac0498b4 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 185.2GB: boot/grub/core.img
 185.2GB: boot/grub/grub.cfg
 185.1GB: boot/initrd.img-2.6.32-25-generic
 207.5GB: boot/initrd.img-2.6.35-22-generic
 185.0GB: boot/vmlinuz-2.6.32-25-generic
 185.0GB: boot/vmlinuz-2.6.35-22-generic
 207.5GB: initrd.img
 185.1GB: initrd.img.old
 185.0GB: vmlinuz
 185.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by garvinrick4 on 2010-11-07
Put in Ubuntu install Cd and boot off of and choose Try Ubuntu.
Go to terminal and open. Copy and paste these,'
```
sudo mkdir /media/root
```
```
sudo mount /dev/sda7 /media/root
```
```
sudo grub-install --recheck --root-directory=/media/root /dev/sda
```
```
sudo umount /media/root
```
Now boot into hard drive and choose Ubuntu
and when it boots. Open a terminal and:
```
sudo update-grub
```

You have made a directory
mounted the install with grub files
install grub in sda looking in sda7 for grub files
unmounted partition

update-grub puts all other Operating systems in grub config and boot menu

Now a question for you. What did you put in sda6 a logical partition which Windows does
not like, they only like primary. If obsolete remove it in gparted and use it for data.
Let me know if you need instructions

---

### Post by rohitrp2003 on 2010-11-07
my grub doesnt load now!! i cant go to windows or linux now! what have u done!! reply fast!

---

### Post by cbhargava on 2010-11-07
> **rohitrp2003 said:**
> Hi

I upgraded my ubuntu 10.04 to 10.10 and now when i choose ubuntu from the grub loader only a command prompt comes. I can just write commands..all my files of ubuntu 10.04 are there also !! 
Please tell me how do I load properly!

I should have never upgraded my ubuntu installation. It messed up my ecryptfs settings and now I can't access my account.

---

### Post by rohitrp2003 on 2010-11-08
hey reply !! where did u run away ! ur online activity shows u came recently!! now help me out and clean up the mess u created

---

### Post by garvinrick4 on 2010-11-08
I am back online now. Put in your install Cd and choose try ubuntu and open a terminal
and install this to get back to Windows booting. This will always get your Windows to boot under normal circumstances. EDIT: READ this POST and go to NEXT post.
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```It will say error but ignore we only want the mbr.
It will now boot to Windows.

The previous code should have worked this is not rocket science
and there are a lot of Ubuntu users who are good.
We can get your system going but relax. There are quite a few new users trying to dual  boot
who have trouble booting on these forums you do not need to get
yourself so worked up you damage yourself.
10 people would have jumped in and helped while I was away watching a movie.
I think you scared everyone. Just relax and let us work this out.
you know you do have a boot partition in sda1 that should have been mounted.
That is the problem I do believe. 

##You know there is a boot partition in your system in sda1 that should have been mounted
##and I did not mount it when I put in your grub2. ##Is my mistake.### Can go to next post and use that code.

---

### Post by garvinrick4 on 2010-11-08
Put in Ubuntu install disk and boot and choose Try Ubuntu and open a terminal and COPY and PASTE please:
```
sudo mkdir /media/boot
``````
sudo mkdir /media/root
``````
sudo mount /dev/sda1 /media/boot
``````
sudo mount /dev/sda7 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/boot
``````
sudo umount /media/root
```Now reboot into hard drive and go into ubuntu and open a terminal
```
sudo update-grub
```The same thing except I had to make a directory and mount sda1 the boot partition: I am sorry to  have inconvenienced you.

---

### Post by rohitrp2003 on 2010-11-08
i did what u said..but after rebooting again there is no grub screen!! 
i booted through live cd again and wrote sudo upate-grub
i get this error ```
/usr/sbin/grub-probe:error: cannot find a device for / (is /dev mounted ?).
```

even if i mount all that and write update grub without rebooting same error comes!! at this stage windows cant be loaded but with those 2 previous commands u said windows loads

---

### Post by Quackers on 2010-11-08
Do you have a Windows repair disc?

---

### Post by garvinrick4 on 2010-11-08
```
##This is what your sda2 should look like: It is missing  /bootmgr /boot/BCD 
Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe
Yours looked like this:
  Boot files/dirs:   /Windows/System32/winload.exe (sda2 boot script)

sda6 which is an attempted install of Windows (largest partition size
in drive.) What happened there.

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 655. But according to the info from fdisk, 
                       sda6 starts at sector 405882880.
    Operating System:  
    Boot files/dirs:  
--------------------------------------------------------------------------
 
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         81,920       286,719       204,800   7 HPFS/NTFS
/dev/sda2             286,720   327,761,919   327,475,200   7 HPFS/NTFS
/dev/sda4         327,763,966   976,771,071   649,007,106   5 Extended
/dev/sda5         327,763,968   335,575,039     7,811,072  82 Linux swap / Solaris
/dev/sda6         405,882,880   976,771,071   570,888,192   7 HPFS/NTFS
/dev/sda7         335,577,088   405,880,831    70,303,744  83 Linux

##Notice sda6 is the largest partiton: And nothing in it?




```

---

### Post by garvinrick4 on 2010-11-08
The question is how did an upgrade from 10.10 from 10.04 which has nothing to do
with Windows remove all the boot files from sda2 your Windows install and put a 
huge partition of Windows partition in sda6 with nothing in it? No big deal this is fixable
but would be nice to know. I am the one that read your bootscript wrong and did not
mount boot partition when reinstalling grub2. You did absolutely nothing wrong came here
because had a bit of a mess going, I should have read your script right in first place.
Lets fix this and make it dual-bootable.

---

### Post by garvinrick4 on 2010-11-08
> **Quackers said:**
> Do you have a Windows repair disc?
Quackers lets get a few answers then work this out. OK Quackers would like to
know what OP did besides just try to upgrade. Windows is booting and we can
always put boot files back if he has Windows disk with 2 commands Quackers,
we know that. He has lilo   installed right now to boot with, getting to salution Quackers.

---

### Post by Quackers on 2010-11-08
I think he's sleeping :-)
The 2 boot files (bootmgr and /boot/BCD ) were on sda1. His Windows 7 system is on sda2. This is the normal way for oem Windows 7 to install now. That's why the boot flag is on sda1. I suspect the upgrade borked grub, hence the boot error.

---

### Post by garvinrick4 on 2010-11-08
> **Quackers said:**
> I think he's sleeping :-)
The 2 boot files (bootmgr and /boot/BCD ) were on sda1. His Windows 7 system is on sda2. This is the normal way for oem Windows 7 to install now. That's why the boot flag is on sda1. I suspect the upgrade borked grub, hence the boot error. If a system has a dedicated boot partition then boot files are in sda 1 and sda2. 
### This is a working system and how it should have looked.
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

---

### Post by garvinrick4 on 2010-11-08
> **Quackers said:**
> I think he's sleeping :-)
The 2 boot files (bootmgr and /boot/BCD ) were on sda1. His Windows 7 system is on sda2. This is the normal way for oem Windows 7 to install now. That's why the boot flag is on sda1. I suspect the upgrade borked grub, hence the boot error. Give me a break Quackers Ok, I have an OEM install of 7 with boot partition. I am heading in a direction let me go there OK Quackers. Thank you.

---

### Post by Quackers on 2010-11-08
No problem.

---

### Post by rohitrp2003 on 2010-11-08
I do not have a windows repair disc..the partition on sda6 contains some hidden files!I had converted my hard disk from dynamic to basic type and thats when that partition was created. it occupies only 100mb of my harddisk so it doesnt bother me..

Is there anyway of getting my linux working?!

---

### Post by rohitrp2003 on 2010-11-08
I have 3 partitions in my windows c drive is 156 gb d drive 272 gb and f drive 100 mb..this f drive was formed while converting dynamic to basic drive..the d drive is not empty!!!

---

### Post by garvinrick4 on 2010-11-08
> **rohitrp2003 said:**
> I have 3 partitions in my windows c drive is 156 gb d drive 272 gb and f drive 100 mb..this f drive was formed while converting dynamic to basic drive..the d drive is not empty!!! Hello I do not know what converting dynamic to basic is will be back.

---

### Post by garvinrick4 on 2010-11-08
> **rohitrp2003 said:**
> I do not have a windows repair disc..the partition on sda6 contains some hidden files!I had converted my hard disk from dynamic to basic type and thats when that partition was created. it occupies only 100mb of my harddisk so it doesnt bother me..

Is there anyway of getting my linux working?!
**Warning:** After you convert a basic disk to a dynamic  disk, local access to the dynamic disk is limited to   Windows XP  Professional, Windows 2000 and Windows Server 2003. Additionally, after  you convert a basic disk to a dynamic disk, the dynamic volumes cannot  be changed back to partitions. You must first delete all dynamic volumes  on the disk and then convert the dynamic disk back to a basic disk. If  you want to keep your data, you must first back up the data or move it  to another volume. (I am going to have to read on this subject)

---

### Post by drs305 on 2010-11-09
rohitrp2003,

Would please describe your current situation? Can you boot to either Windows or Ubuntu? If neither, I would first try to restore Windows. You said you didn't have a repair disk. Here are some links where you can get what you need and *oldfred's* link will help you run them.

W7 Repair Disk:  [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")
Vista Repair Disk:  [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/ ]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")
*oldfred's*  Windows repair links:  
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

Once you have repaired Windows then please post a new copy of your RESULTS.txt.

---

### Post by rohitrp2003 on 2010-11-09
I can boot into Windows right now..there is no problem with it. If I use a live cd I am able to access my ubuntu files. my disk is of basic type. it has been converted from dynamic to basic.

The repair cd is a bit too large for me to download since my net speed isnt great, so is there any other solution to get my ubuntu running?! or atleast downgrade to ubuntu 10.04 with all my installed files still there?!

---

### Post by drs305 on 2010-11-09
> **rohitrp2003 said:**
> I can boot into Windows right now..there is no problem with it. If I use a live cd I am able to access my ubuntu files. my disk is of basic type. it has been converted from dynamic to basic.

Would you please post a new copy of RESULTS.txt so we can see the current status of your Ubuntu install. Since you can boot the LiveCD and if your Ubuntu installation is basically intact we should be able to restore it without a reinstall of the entire OS.

---

### Post by rohitrp2003 on 2010-11-12
sorry for the late reply..had my exams going on !
here is the latest copy of results.txt file
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 655. But according to the info from fdisk, 
                       sda6 starts at sector 405882880.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         81,920       286,719       204,800   7 HPFS/NTFS
/dev/sda2             286,720   327,761,919   327,475,200   7 HPFS/NTFS
/dev/sda4         327,763,966   976,771,071   649,007,106   5 Extended
/dev/sda5         327,763,968   335,575,039     7,811,072  82 Linux swap / Solaris
/dev/sda6         405,882,880   976,771,071   570,888,192   7 HPFS/NTFS
/dev/sda7         335,577,088   405,880,831    70,303,744  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        30C21529C214F4B6                       ntfs                                     
/dev/sda2        6E80FF4280FF0EF9                       ntfs       System                        
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5d54ed28-1450-4735-8bb1-80d3ac0498b4   swap                                     
/dev/sda6        980A7D120A7CEE9E                       ntfs       Data                          
/dev/sda7        364fc37a-062f-4e84-834b-c212fac3bbcf   ext3                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /media/364fc37a-062f-4e84-834b-c212fac3bbcf ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/System            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/30C21529C214F4B6  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=364fc37a-062f-4e84-834b-c212fac3bbcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=364fc37a-062f-4e84-834b-c212fac3bbcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=364fc37a-062f-4e84-834b-c212fac3bbcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=364fc37a-062f-4e84-834b-c212fac3bbcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 364fc37a-062f-4e84-834b-c212fac3bbcf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 30c21529c214f4b6
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=364fc37a-062f-4e84-834b-c212fac3bbcf /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5d54ed28-1450-4735-8bb1-80d3ac0498b4 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 185.0GB: boot/grub/core.img
 185.2GB: boot/grub/grub.cfg
 185.1GB: boot/initrd.img-2.6.32-25-generic
 207.5GB: boot/initrd.img-2.6.35-22-generic
 185.0GB: boot/vmlinuz-2.6.32-25-generic
 185.0GB: boot/vmlinuz-2.6.35-22-generic
 207.5GB: initrd.img
 185.1GB: initrd.img.old
 185.0GB: vmlinuz
 185.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by drs305 on 2010-11-12
> **rohitrp2003 said:**
> I can boot into Windows right now..there is no problem with it. If I use a live cd I am able to access my ubuntu files. my disk is of basic type. it has been converted from dynamic to basic.

From what we can see with your RESULTS.txt, your Ubuntu files are intact. To reinstall Grub2 to allow you to boot both Windows and Ubuntu, boot the LiveCD, mount your Ubuntu partition (sda7), verify the folders exist, then install Grub2:

```
sudo mount /dev/sda7 /mnt  # Mount you Ubuntu partition
ls /mnt                    # Make sure normal Ubuntu folders are present
sudo grub-install --root-directory=/mnt /dev/sda  

```
Note in the grub-install command you do NOT include the partition number (i.e. sda, NOT sda7).

---

### Post by rohitrp2003 on 2010-11-12
dint work :( a large blinking cursor came at boot up

---

### Post by drs305 on 2010-11-13
> **rohitrp2003 said:**
> dint work :( a large blinking cursor came at boot up

If there was a "grub" or "grub rescue" prompt, it is a Grub problem. However, normally a flashing prompt means that Grub passed control over to the Linux kernel and there was a failure afterward.

Often it is a video problem. One thing you can try is to edit the menu. If you don't see the Grub menu during boot, try rebooting and holding down the SHIFT key to see if it appears.

If you get the menu, highlight the first item and then press "e". Use the cursor to move to the end of the "linux" line of the entry and add **nomodeset**. It will probably be just after "quiet splash". 

Once you have typed **nomodeset** press CTRL-x to boot and see if you get to the Ubuntu Desktop. If you do, you probably have a driver problem and need to load your video drivers. They may be available via System, Administration, Additional Drivers or Hardware Drivers. 

It would be best to first open a terminal or use Synaptic to update the packages. From Synaptic (System, Administration, Synaptic Package Manager), press the Reload button. Then Edit, Mark All Upgrades, Mark, Apply.

From a terminal (Applications, Accessories, Terminal) type:
```
sudo apt-get update && sudo apt-get upgrade
```

Once you have updated the packages (which may fix the problem by itself), try rebooting. If it still fails, repeat the "nomodeset" boot and install a proprietary drive if one was found in the Additional Drivers section.

---

### Post by DinoT1985 on 2010-11-13
I had this exact problem. I couldnt fix it in the end, so I ended up reinstalling Ubuntu 10.10 with the "download updates" box unticked during the install screens. 

So insurance reasons, use the Live CD to copy files you need/want to an external HD or USB.

---

### Post by rohitrp2003 on 2010-11-13
After pressing shift also nothing comes..the screen is blank!

---

### Post by drs305 on 2010-11-13
> **rohitrp2003 said:**
> After pressing shift also nothing comes..the screen is blank!

Just for accuracy, you hold down the SHIFT key during the entire boot until the menu appears, usually within about 15 seconds of the system beep.

---

### Post by rohitrp2003 on 2010-11-14
I tried..it dint come still

---

### Post by sentinelace on 2011-01-07
I have the same problem but my setup is a little different. Any help appreciated.
 
[LEFT][FONT=DejaVuSans][SIZE=3][FONT=DejaVuSans][SIZE=3]File: /home/ubuntu/Desktop/RESULTS.txt Page 1 of 6[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSans][SIZE=3]
[/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1][FONT=DejaVuSansMono][SIZE=1]Boot Info Script 0.55 dated February 15th, 2010[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1]
[SIZE=1][FONT=DejaVuSansMono]============================= Boot Info Summary: ==============================[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]partition #1 for /grub.[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]sda1: _________________________________________________________________________[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]File system: ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Boot sector type: -[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Boot sector info:[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Operating System:[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Boot files/dirs: /grub/grub.cfg /grub/core.img[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]sda2: _________________________________________________________________________[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]File system: Extended Partition[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Boot sector type: Unknown[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Boot sector info:[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]sda5: _________________________________________________________________________[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]File system: LVM2_member[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Boot sector type: -[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Boot sector info:[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]=========================== Drive/Partition Info: =============================[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Drive: sda ___________________ _____________________________________________________[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Disk /dev/sda: 218.2 GB, 218187694080 bytes[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]255 heads, 63 sectors/track, 26526 cylinders, total 426147840 sectors[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Units = sectors of 1 * 512 = 512 bytes[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Partition Boot Start End Size Id System[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]/dev/sda1 * 2,048 499,711 497,664 83 Linux[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]/dev/sda2 501,758 426,145,791 425,644,034 5 Extended[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]/dev/sda5 501,760 426,145,791 425,644,032 8e Linux LVM[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]blkid -c /dev/null: ____________________________________________________________[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Device UUID TYPE LABEL[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]/dev/loop0 squashfs[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]/dev/sda1 8a2d08fd-1934-4c8b-908c-f84728bcf6f2 ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]/dev/sda2: PTTYPE="dos"[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]/dev/sda5 CazkDH-1TGN-xgQJ-oxsj-1sJY-kKkc-qJsgEg LVM2_member[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]/dev/sda: PTTYPE="dos"[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]============================ "mount | grep ^/dev output: ===========================[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Device Mount_Point Type Options[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]aufs / aufs (rw)[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]/dev/sr0 /cdrom iso9660 (ro,noatime)[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]/dev/loop0 /rofs squashfs (ro,noatime)[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]============================= sda1/grub/grub.cfg: =============================[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]#[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]# DO NOT EDIT THIS FILE[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]#[/FONT][/SIZE]
[/SIZE][/FONT][FONT=DejaVuSans][SIZE=3][FONT=DejaVuSans][SIZE=3]File: /home/ubuntu/Desktop/RESULTS.txt Page 2 of 6[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSans][SIZE=3]
[/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1][FONT=DejaVuSansMono][SIZE=1]# It is automatically generated by grub-mkconfig using templates[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1]
[SIZE=1][FONT=DejaVuSansMono]# from /etc/grub.d and settings from /etc/default/grub[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]#[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### BEGIN /etc/grub.d/00_header ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if [ -s $prefix/grubenv ]; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set have_grubenv=true[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]load_env[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set default="0"[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if [ "${prev_saved_entry}" ]; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set saved_entry="${prev_saved_entry}"[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]save_env saved_entry[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set prev_saved_entry=[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]save_env prev_saved_entry[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set boot_once=true[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]function savedefault {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if [ -z "${boot_once}" ]; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]saved_entry="${chosen}"[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]save_env saved_entry[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]function recordfail {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set recordfail=1[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]function load_video {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod vbe[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod lvm[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(Qmail-root)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root b023ac61-951d-4741-8966-5f7aacb3c7e1[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if loadfont /usr/share/grub/unicode.pf2 ; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set gfxmode=auto[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]load_video[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod gfxterm[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]terminal_output gfxterm[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set locale_dir=($root)/grub/locale[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set lang=en_US[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod gettext[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if [ "${recordfail}" = 1 ]; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set timeout=-1[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]else[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set timeout=10[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### END /etc/grub.d/00_header ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### BEGIN /etc/grub.d/05_debian_theme ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set menu_color_normal=white/black[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set menu_color_highlight=black/light-gray[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if background_color 44,0,30; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]clear[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### END /etc/grub.d/05_debian_theme ###[/FONT][/SIZE]
[/SIZE][/FONT][FONT=DejaVuSans][SIZE=3][FONT=DejaVuSans][SIZE=3]File: /home/ubuntu/Desktop/RESULTS.txt Page 3 of 6[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSans][SIZE=3]
[/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1][FONT=DejaVuSansMono][SIZE=1]### BEGIN /etc/grub.d/10_linux ###[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1]
[SIZE=1][FONT=DejaVuSansMono]if [ ${recordfail} != 1 ]; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set matches_file=${prefix}/gfxblacklist.txt[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set class_match=3[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if lua ${prefix}/hwmatch.lua; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if [ ${match} = 0 ]; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set linux_gfx_mode=keep[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]else[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set linux_gfx_mode=text[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]else[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set linux_gfx_mode=text[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]else[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set linux_gfx_mode=text[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if [ "$linux_gfx_mode" != "text" ]; then load_video; fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]menuentry 'Ubuntu, with Linux 2.6.37-12-server' --class ubuntu --class gnu-linux --class gnu --class os {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]recordfail[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set gfxpayload=$linux_gfx_mode[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]linux /vmlinuz-2.6.37-12-server root=/dev/mapper/Qmail-root ro rootdelay=10 vt.handoff=7 quiet[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]initrd /initrd.img-2.6.37-12-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]menuentry 'Ubuntu, with Linux 2.6.37-12-server (recovery mode)' --class ubuntu --class gnu-linux --class[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]gnu --class os {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]recordfail[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set gfxpayload=$linux_gfx_mode[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]echo 'Loading Linux 2.6.37-12-server ...'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]linux /vmlinuz-2.6.37-12-server root=/dev/mapper/Qmail-root ro single rootdelay=10[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]echo 'Loading initial ramdisk ...'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]initrd /initrd.img-2.6.37-12-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]submenu "Previous Linux versions" {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]menuentry 'Ubuntu, with Linux 2.6.32-27-server' --class ubuntu --class gnu-linux --class gnu --class os {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]recordfail[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set gfxpayload=$linux_gfx_mode[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]linux /vmlinuz-2.6.32-27-server root=/dev/mapper/Qmail-root ro rootdelay=10 vt.handoff=7 quiet[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]initrd /initrd.img-2.6.32-27-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]menuentry 'Ubuntu, with Linux 2.6.32-27-server (recovery mode)' --class ubuntu --class gnu-linux --class[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]gnu --class os {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]recordfail[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set gfxpayload=$linux_gfx_mode[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]echo 'Loading Linux 2.6.32-27-server ...'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]linux /vmlinuz-2.6.32-27-server root=/dev/mapper/Qmail-root ro single rootdelay=10[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]echo 'Loading initial ramdisk ...'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]initrd /initrd.img-2.6.32-27-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]menuentry 'Ubuntu, with Linux 2.6.32-24-server' --class ubuntu --class gnu-linux --class gnu --class os {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]recordfail[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set gfxpayload=$linux_gfx_mode[/FONT][/SIZE]
[/SIZE][/FONT][FONT=DejaVuSans][SIZE=3][FONT=DejaVuSans][SIZE=3]File: /home/ubuntu/Desktop/RESULTS.txt Page 4 of 6[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSans][SIZE=3]
[/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1][FONT=DejaVuSansMono][SIZE=1]insmod part_msdos[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]linux /vmlinuz-2.6.32-24-server root=/dev/mapper/Qmail-root ro rootdelay=10 vt.handoff=7 quiet[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]initrd /initrd.img-2.6.32-24-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]menuentry 'Ubuntu, with Linux 2.6.32-24-server (recovery mode)' --class ubuntu --class gnu-linux --class[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]gnu --class os {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]recordfail[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set gfxpayload=$linux_gfx_mode[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]echo 'Loading Linux 2.6.32-24-server ...'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]linux /vmlinuz-2.6.32-24-server root=/dev/mapper/Qmail-root ro single rootdelay=10[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]echo 'Loading initial ramdisk ...'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]initrd /initrd.img-2.6.32-24-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]menuentry 'Ubuntu, with Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]recordfail[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set gfxpayload=$linux_gfx_mode[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]linux /vmlinuz-2.6.32-21-server root=/dev/mapper/Qmail-root ro rootdelay=10 vt.handoff=7 quiet[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]initrd /initrd.img-2.6.32-21-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]menuentry 'Ubuntu, with Linux 2.6.32-21-server (recovery mode)' --class ubuntu --class gnu-linux --class[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]gnu --class os {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]recordfail[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set gfxpayload=$linux_gfx_mode[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]echo 'Loading Linux 2.6.32-21-server ...'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]linux /vmlinuz-2.6.32-21-server root=/dev/mapper/Qmail-root ro single rootdelay=10[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]echo 'Loading initial ramdisk ...'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]initrd /initrd.img-2.6.32-21-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### END /etc/grub.d/10_linux ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### BEGIN /etc/grub.d/20_linux_xen ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### END /etc/grub.d/20_linux_xen ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### BEGIN /etc/grub.d/20_memtest86+ ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]menuentry "Memory test (memtest86+)" {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]linux16 /memtest86+.bin[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]menuentry "Memory test (memtest86+, serial console 115200)" {[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod part_msdos[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]insmod ext2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set root='(hd0,msdos1)'[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]search --no-floppy --fs-uuid --set=root 8a2d08fd-1934-4c8b-908c-f84728bcf6f2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]linux16 /memtest86+.bin console=ttyS0,115200n8[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]}[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### END /etc/grub.d/20_memtest86+ ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### BEGIN /etc/grub.d/30_os-prober ###[/FONT][/SIZE]
[/SIZE][/FONT][FONT=DejaVuSans][SIZE=3][FONT=DejaVuSans][SIZE=3]File: /home/ubuntu/Desktop/RESULTS.txt Page 5 of 6[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSans][SIZE=3]
[/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1][FONT=DejaVuSansMono][SIZE=1]if [ "x${timeout}" != "x-1" ]; then[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1]
[SIZE=1][FONT=DejaVuSansMono]if keystatus; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if keystatus --shift; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set timeout=-1[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]else[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set timeout=0[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]else[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if sleep --interruptible 3 ; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]set timeout=0[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### END /etc/grub.d/30_os-prober ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### BEGIN /etc/grub.d/40_custom ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]# This file provides an easy way to add custom menu entries. Simply type the[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]# menu entries you want to add after this comment. Be careful not to change[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]# the 'exec tail' line above.[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### END /etc/grub.d/40_custom ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### BEGIN /etc/grub.d/41_custom ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]if [ -f $prefix/custom.cfg ]; then[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]source $prefix/custom.cfg;[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]fi[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]### END /etc/grub.d/41_custom ###[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]=================== sda1: Location of files loaded by Grub: ===================[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono].0GB: grub/core.img[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono].0GB: grub/grub.cfg[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono].0GB: initrd.img-2.6.32-21-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono].0GB: initrd.img-2.6.32-24-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono].0GB: initrd.img-2.6.32-27-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono].0GB: initrd.img-2.6.37-12-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono].0GB: vmlinuz-2.6.32-21-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono].0GB: vmlinuz-2.6.32-24-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono].0GB: vmlinuz-2.6.32-27-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono].0GB: vmlinuz-2.6.37-12-server[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]=========================== Unknown MBRs/Boot Sectors/etc =======================[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]Unknown BootLoader on sda2[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000000 0f 84 8a 01 00 00 83 ec 10 83 c4 04 8b 06 8b 0b |................|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000010 8b 17 81 c2 80 80 80 80 8b ae 00 03 00 00 8d 84 |................|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000020 01 01 01 01 01 8b 8b 00 03 00 00 d1 e8 25 7f 7f |.............%..|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000030 7f 7f 8d ac 29 01 01 01 01 2b d0 8b 87 00 03 00 |....)....+......|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000040 00 89 54 24 14 05 80 80 80 80 d1 ed 8b 96 00 06 |..T$............|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000050 00 00 81 e5 7f 7f 7f 7f 8b 8b 00 06 00 00 2b c5 |..............+.|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000060 8b af 00 06 00 00 89 44 24 24 8d 8c 0a 01 01 01 |.......D$$......|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000070 01 d1 e9 81 c5 80 80 80 80 81 e1 7f 7f 7f 7f 8b |................|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000080 86 00 09 00 00 2b e9 8b 8b 00 09 00 00 89 6c 24 |.....+........l$|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000090 34 8b af 00 09 00 00 8d 8c 08 01 01 01 01 81 c5 |4...............|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000000a0 80 80 80 80 d1 e9 83 c6 04 81 e1 7f 7f 7f 7f 83 |................|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000000b0 c3 04 2b e9 83 c7 04 f7 c4 04 00 00 00 89 6c 24 |..+...........l$|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000000c0 44 0f 84 42 ff ff ff 81 c6 78 01 00 00 81 c7 78 |D..B.....x.....x|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000000d0 01 00 00 f7 c4 08 00 00 00 8d 9b 78 01 00 00 0f |...........x....|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000000e0 85 24 ff ff ff 33 db 33 c9 8a 5c 24 08 8a 4c 24 |.$...3.3..\$..L$|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000000f0 0b e9 33 01 00 00 8d 5e 01 f6 c4 01 0f 84 04 ff |..3....^........|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000100 ff ff 83 ec 40 8b 46 01 8d 14 4d 01 00 00 00 8b |....@.F...M.....|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000110 1e 83 c7 04 03 c3 8b 5c 2e 01 23 d0 8b 2c 2e 33 |.......\..#..,.3|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000120 c2 03 dd d1 e8 03 da d1 eb 83 c6 04 81 e3 7f 7f |................|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000130 7f 7f 8d 44 48 01 03 c3 8b 5f fc d1 e8 03 d9 25 |...DH...._.....%|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000140 7f 7f 7f 7f 83 c4 04 2b d8 bd 80 01 00 00 f7 c4 |.......+........|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000150 04 00 00 00 89 5c 24 44 74 ab 8d 74 35 f8 33 db |.....\$Dt..t5.3.|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000160 f7 c4 38 00 00 00 8d 7c 3d f8 75 99 8a 5c 24 08 |..8....|=.u..\$.|[/FONT][/SIZE]
[/SIZE][/FONT][FONT=DejaVuSans][SIZE=3][FONT=DejaVuSans][SIZE=3]File: /home/ubuntu/Desktop/RESULTS.txt Page 6 of 6[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSans][SIZE=3]
[/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1][FONT=DejaVuSansMono][SIZE=1]00000170 33 c9 8a 4c 24 0b e9 ae 00 00 00 b9 80 80 80 80 |3..L$...........|[/SIZE][/FONT][/SIZE][/FONT][FONT=DejaVuSansMono][SIZE=1]
[SIZE=1][FONT=DejaVuSansMono]00000180 8b 78 f4 03 fe 8b 70 f8 8d 54 6d 00 8d 5c 35 00 |.x....p..Tm..\5.|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]00000190 83 f4 04 8b 07 03 c1 8b 1e 2b c3 8b 1c 2e 89 44 |.........+.....D|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000001a0 24 0c 8b 04 2f 2b c3 8b 1c 6e 03 c1 2b d9 89 44 |$.../+...n..+..D|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000001b0 24 14 8b 04 6f 2b c3 8b 1c ae 89 44 24 1c 00 3b |$...o+.....D$..;|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000001c0 1d 1f 8e fe ff ff 02 00 00 00 00 d0 5e 19 00 00 |............^...|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000001d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]*[/FONT][/SIZE]
[SIZE=1][FONT=DejaVuSansMono]000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|[/FONT][/SIZE][/LEFT]
[SIZE=1][FONT=DejaVuSansMono]00000200[/FONT][/SIZE]
[/SIZE][/FONT]

---


---
title: "Problems booting grub with windows boot loader"
date: 2009-12-27
forum: General Help
---

### Post by rosatimr on 2009-12-27
I want to use dual boot with windows boot manager. I have followed the steps from this link [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). I used bcdedit to add the linux.bin to the boot manager. When my computer boots up I get the option of booting Windows 7 or Grub. When I choose Grub, I get an error that says C:\linux.bin is either missing or corrupt, along with some error code (I posted the exact message below). I must be copying my boot sector incorrectly. 
 
Here is my fdisk -l output:
 
```
 
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a
 
Device Boot Start End Blocks Id System
/dev/sda1 1 851 6833152 27 Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 851 11516 85666420 7 HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3 11517 12161 5178600 5 Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5 11517 12127 4898848+ 83 Linux
/dev/sda6 12127 12161 279688+ 82 Linux swap / Solaris
ubuntu@ubuntu:~$ 

```
 
This is the command I used to copy the boot sector, per the instructions,
```
dd if=/dev/sda5 of=/media/SW_Preload/linux.bin bs=512 count=1
```
 
Here /media/SW_Preload is my C:\
 
It sucessfully copies to the C:\ as I see it when I load into Windows. Is /dev/sda5 my boot sector for Linux? 
 
Here is my find /boot/grub/stage1 output:
(hd0,4)
 
Here is my bcdedit output:
```
 
C:\Windows\system32>bcdedit
Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {f307bca9-edac-11de-bb5a-cf2629439b5f}
displayorder            {current}
                        {f307bcae-edac-11de-bb5a-cf2629439b5f}
toolsdisplayorder       {memdiag}
timeout                 10
Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {572bcd55-ffa7-11d9-aae0-0007e994107d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {f307bca9-edac-11de-bb5a-cf2629439b5f}
nx                      OptIn
Real-mode Boot Sector
---------------------
identifier              {f307bcae-edac-11de-bb5a-cf2629439b5f}
device                  boot
path                    C:\linux.bin
description             GRUB 
 

```
 
Here is what is displayed when I choose GRUB in the Windows Boot Manager:
 
```
 
Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."
 
If you do not have this disc, contact your system administrator or computer manufacturer for assistance.
 
File: C:\linux.bin
 
Status: 0x00000d
 
Info: The selected entry could not be loaded because the application is missing or corrupt.

``` 
 
Thanks in advance for any help.

---

### Post by Mahngiel on 2009-12-27
[removed]

---

### Post by Groundswell on 2009-12-27
I've never had much luck with windows being nice to other installations, so i always let GRUB take care of windows and boot straight to grub and forget about the windows boot loader. I know this isn't an answer to your problem but sometimes the headaches to get it to work a certain way aren't worth it, but i don't know your situation. goodluck

---

### Post by rosatimr on 2009-12-30
Any helpers?  Should I just use grub or what?  I feel like I am close to making this happen.

---

### Post by Leppie on 2009-12-30
try adjusting using the super grub disk, it handles most things for you after selecting where to put grub.

---

### Post by Mark Phelps on 2009-12-30
> **rosatimr said:**
> Any helpers?  Should I just use grub or what?  I feel like I am close to making this happen.

You would do better going to the NeoSmart Technology forums, instead of posting EasyBCD problems here.  They are the provider of EasyBCD, and the have both forums and tutorials available.

---

### Post by meierfra. on 2009-12-31
> Instead of posting EasyBCD problems here. 
?????  The OP is not using EasyBCD, but "bcdedit". (EasyBCD is a GUI for "bcdedit")


> C:\linux.bin is either missing or corrupt, 

You bcd  item for Grub looks fine. So I would guess that something is wrong with "linux.bin". Did you install grub to the boot sector of /dev/sda5 before you run the "dd" command:


```
sudo grub
``` 
and at the "grub>" prompt:

```
root (hd0,4)
setup (hd0,4)
quit
```

Then run the "dd" command again to copy the boot sector to the Windows partition.

---

### Post by john newbuntu on 2009-12-31
fdisk is reporting that the partition is not ending on a cylinder boundary.  Maybe someone can correct me here.  But would'nt it be prudent to fix this with a tool like testdisk.  Following this, he could recopy the linux boot sector in a file and go ahead with the boot process.

---

### Post by meierfra. on 2009-12-31
```
fdisk is reporting that the partition is not ending on a cylinder boundary.
```
That's not a problem. Neither Windows nor Ubuntu cares about cylindrical bounds.

---

### Post by SecretCode on 2009-12-31
I thought Windows did? Maybe MSDOS 5.0 cared. Who knows?

---

### Post by meierfra. on 2009-12-31
> thought Windows did? 
I know that XP, Vista and Windows 7 don't care.  
Don't really have any experience  with earlier Versions of Windows.

---

### Post by rosatimr on 2010-01-02
> **meierfra. said:**
> ????? The OP is not using EasyBCD, but "bcdedit". (EasyBCD is a GUI for "bcdedit")
 
 
 
 
You bcd item for Grub looks fine. So I would guess that something is wrong with "linux.bin". Did you install grub to the boot sector of /dev/sda5 before you run the "dd" command:
 
 
```
sudo grub
``` 
and at the "grub>" prompt:
 
```
root (hd0,4)
setup (hd0,4)
quit
```
 
Then run the "dd" command again to copy the boot sector to the Windows partition.
 
 
Per the instructions I was following, I did that.  First I ran the "find /boot/grub/stage1" command and the output was (hd0,4).  Then I did this:
 
```
 
grub> root (hd0,4)

grub> setup (hd0,4)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,4) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> 

```
 
I then ran the dd command and got this:
 
```
 
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# dd if=/dev/sda5 of=/media/SW_Preload/linux.bin bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.509358 s, 1.0 kB/s
root@ubuntu:~# 

```
 
Same problem.
 
Im at a loss.  I don't necessarily need to use Windows boot loader to dual boot.  Its just one of those things, where I have a problem and it will irritates me not to be able to solve it.

---

### Post by rosatimr on 2010-01-02
> **Leppie said:**
> try adjusting using the super grub disk, it handles most things for you after selecting where to put grub.
 
Sorry for being such a newbie, but can you explain furthur?

---

### Post by meierfra. on 2010-01-02
From your bcdedit  output:

> path C:\linux.bin 

This needs to be 

```
 path \linux.bin
```

(Sorry, I should have noticed that earlier)

---

### Post by rosatimr on 2010-01-02
> **meierfra. said:**
> From your bcdedit output:
 
 
 
This needs to be 
 
```
 path \linux.bin
```
 
(Sorry, I should have noticed that earlier)
 
 
Perfect.  Thanks.  It boots to the grub command and I would like it to boot straight into Ubuntu.  Want save a newbie some reading and guide me?
 
Thanks again.

---

### Post by rosatimr on 2010-01-02
More issues....I had to restore the MBR with the Windows CD.  So I had to go back into the terminal load grub and rerun this
 
```
 
root (hd0,4)
setup (hd0,4)
quit

```Then I did this
 
```
root@ubuntu:~# dd if=/dev/sda5 of=/media/SW_Preload/linux.bin bs=512 count=1
```I then had to go back and re-edit the bcdedit and it looks like this
 
```
 
C:\Windows\system32>bcdedit
Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume1
path                    \bootmgr
description             Windows Boot Manager
locale                  en-US
default                 {current}
displayorder            {current}
                        {3b11f491-f77f-11de-afc8-cc531146495f}
timeout                 10
Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7 Ultimate (recovered)
locale                  en-US
recoverysequence        {3b11f48f-f77f-11de-afc8-cc531146495f}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {e87ef8a4-f76e-11de-871a-806e6f6e6963}
Real-mode Boot Sector
---------------------
identifier              {3b11f491-f77f-11de-afc8-cc531146495f}
device                  boot
path                    \linux.bin
description             GRUB
C:\Windows\system32>

```Now when I choose GRUB, I get that same error again.  It worked for a moment, then I messed it up because I don't know how to get it to boot straight to Ubuntu instead of to the grub command.  What is wrong this time?

---

### Post by meierfra. on 2010-01-02
Just to  get a better picture on what is going on, boot  into Ubuntu (or the Ubuntu Live CD), download the [Boot Info script]("https://sourceforge.net/projects/bootinfoscript/") to your desktop, open a terminal and type

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create the file "RESULTS.txt" on your Desktop. Post the content of that  file (Use the code tags: #)

---

### Post by rosatimr on 2010-01-02
> **meierfra. said:**
> Just to  get a better picture on what is going on, boot  into Ubuntu (or the Ubuntu Live CD), download the [Boot Info script]("https://sourceforge.net/projects/bootinfoscript/") to your desktop, open a terminal and type

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create the file "RESULTS.txt" on your Desktop. Post the content of that  file (Use the code tags: #)

Here you go.
```

=> Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 0.97 in the file /linux.bin looks at sector 
                       185284607 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 185284607 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95f3457a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    13,668,351    13,666,304  27 Hidden HPFS/NTFS
/dev/sda2          13,668,352   185,001,191   171,332,840   7 HPFS/NTFS
/dev/sda3         185,008,320   195,365,519    10,357,200   5 Extended
/dev/sda5         185,008,383   194,806,079     9,797,697  83 Linux
/dev/sda6         194,806,143   195,365,519       559,377  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="BC6035126034D4BC" LABEL="ServiceV002" TYPE="ntfs" 
sda2: UUID="2ABECB36BECAF8F9" LABEL="SW_Preload" TYPE="ntfs" 
sda5: UUID="145f3c89-8563-4fa6-a54c-6a23bbe7f237" TYPE="ext4" 
sda6: UUID="a0bd01d2-4f9f-4ab2-9cf9-27cef2f3795b" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
search --no-floppy --fs-uuid --set 145f3c89-8563-4fa6-a54c-6a23bbe7f237
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 145f3c89-8563-4fa6-a54c-6a23bbe7f237
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=145f3c89-8563-4fa6-a54c-6a23bbe7f237 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 145f3c89-8563-4fa6-a54c-6a23bbe7f237
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=145f3c89-8563-4fa6-a54c-6a23bbe7f237 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 145f3c89-8563-4fa6-a54c-6a23bbe7f237
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=145f3c89-8563-4fa6-a54c-6a23bbe7f237 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 145f3c89-8563-4fa6-a54c-6a23bbe7f237
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=145f3c89-8563-4fa6-a54c-6a23bbe7f237 ro single 
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
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bc6035126034d4bc
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 2abecb36becaf8f9
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
UUID=145f3c89-8563-4fa6-a54c-6a23bbe7f237 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a0bd01d2-4f9f-4ab2-9cf9-27cef2f3795b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb4       /media/mybook   usbfs,                         username=rosatimr, password=robinett     0  0



=================== sda5: Location of files loaded by Grub: ===================


  98.3GB: boot/grub/core.img
  97.6GB: boot/grub/grub.cfg
  94.8GB: boot/grub/stage2
  95.5GB: boot/initrd.img-2.6.31-14-generic
  97.6GB: boot/initrd.img-2.6.31-16-generic
  97.1GB: boot/vmlinuz-2.6.31-14-generic
  98.5GB: boot/vmlinuz-2.6.31-16-generic
  97.6GB: initrd.img
  95.5GB: initrd.img.old
  98.5GB: vmlinuz
  97.1GB: vmlinuz.old
```

Thanks.

---

### Post by meierfra. on 2010-01-02
You have two copies of  bootmgr installed, one in /dev/sda1 and one on /dev/sda2.  Your boot flag is on  /dev/sda1. So you are currently using the one on  /dev/sda1.   Earlier the boot flags must have been on /dev/sda2 and you used the bootmgr on /dev/sda2.  That's the reason why you had to use "bcdedit" again, the bcd on /dev/sda1 did not have an  entry for Ubuntu.  Your Ubuntu item in bcd says:

```
device                  boot
path                    \linux.bin

```
So bootmgr will look on the boot partition for  \linux.bin. Your  boot partition is now /dev/sda1, but \linux.bin is on /dev/sda2. So you get the "missing or corrupt" message.  There are lots ways to fix this:

1)   Put the boot flag onto /dev/sda2

2)   Move the file \linux.bin to your first Windows partition. (Edit: I reworded this to avoid confusions)

3)  Change "device boot" to "device  partition=C:"

Either of these should solve your first problem.


You also have two version of grub installed:  Legacy grub in the file  stage2 on /dev/sda5  and Grub 2 in the file core.img on /dev/sda5.  Legacy Grub is missing "menu.lst", the file necessary to generated the Grub menu.  linux.bin is configured to look for stage2 and you end up at the grub prompt.

So you have two options:

A) Install Grub 2 to the boot sector of /dev/sda5 and run the "dd" command again,

B) Create menu.lst


For now, it seems easiest to create a simple menu.lst.


At the grub prompt (after selecting Ubuntu from the Windows boot menu) type

root (hd0,4)
kernel /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot

 and you should be able to boot into Ubuntu.

Then create  and open the file "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Write this into the file:


default 0
timeout 10

title Ubuntu
root (hd0,4)
kernel /vmlinuz root=/dev/sda5 ro
initrd /initrd.img

title Ubuntu (Recovery mode)
root (hd0,4)
kernel /vmlinuz root=/dev/sda5 ro single
initrd /initrd.img

Save the file. 


Reboot,  and you should now get the Grub menu, rather than the grub prompt.

(Once everything is working, use

timeout 3
hiddenmenu

in menu.lst. Then you won't have to go through two boot menus.)

---

### Post by rosatimr on 2010-01-02
I though it was solved.  Everything you told me to do worked.  I was first able to boot to the grub menu.  Then I put that hidden menu piece into the menu.lst and now it boots straight into Ubuntu, which is what I want after I choose grub from the windows boot loader.  But, right now it skips the windows boot loader and goes right into ubuntu.  Why is it not giving me the windows boot loader to choose between windows and grub?

---

### Post by meierfra. on 2010-01-02
Strange. Did you install grub to the MBR?
Could you run the boot info script again and post the new RESULTS.txt (if you still have the old one, the new one will be called RESULTS1.txt)?

---

### Post by rosatimr on 2010-01-02
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 185284607 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 0.97 in the file /linux.bin looks at sector 
                       185284607 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 185284607 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95f3457a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    13,668,351    13,666,304  27 Hidden HPFS/NTFS
/dev/sda2          13,668,352   185,001,191   171,332,840   7 HPFS/NTFS
/dev/sda3         185,008,320   195,365,519    10,357,200   5 Extended
/dev/sda5         185,008,383   194,806,079     9,797,697  83 Linux
/dev/sda6         194,806,143   195,365,519       559,377  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda2: UUID="2ABECB36BECAF8F9" LABEL="SW_Preload" TYPE="ntfs" 
sda5: UUID="145f3c89-8563-4fa6-a54c-6a23bbe7f237" TYPE="ext4" 
sda6: UUID="a0bd01d2-4f9f-4ab2-9cf9-27cef2f3795b" TYPE="swap" 

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
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)


=========================== sda5/boot/grub/menu.lst: ===========================

default 0
timeout 3
hiddenmenu

title Ubuntu
root (hd0,4)
kernel /vmlinuz root=/dev/sda5 ro
initrd /initrd.img

title Ubuntu (Recovery mode)
root (hd0,4)
kernel /vmlinuz root=/dev/sda5 ro single
initrd /initrd.img


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
search --no-floppy --fs-uuid --set 145f3c89-8563-4fa6-a54c-6a23bbe7f237
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 145f3c89-8563-4fa6-a54c-6a23bbe7f237
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=145f3c89-8563-4fa6-a54c-6a23bbe7f237 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 145f3c89-8563-4fa6-a54c-6a23bbe7f237
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=145f3c89-8563-4fa6-a54c-6a23bbe7f237 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 145f3c89-8563-4fa6-a54c-6a23bbe7f237
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=145f3c89-8563-4fa6-a54c-6a23bbe7f237 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 145f3c89-8563-4fa6-a54c-6a23bbe7f237
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=145f3c89-8563-4fa6-a54c-6a23bbe7f237 ro single 
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
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bc6035126034d4bc
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 2abecb36becaf8f9
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
UUID=145f3c89-8563-4fa6-a54c-6a23bbe7f237 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a0bd01d2-4f9f-4ab2-9cf9-27cef2f3795b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb4       /media/mybook   usbfs,                         username=rosatimr, password=robinett     0  0



=================== sda5: Location of files loaded by Grub: ===================


  94.7GB: boot/grub/core.img
  94.7GB: boot/grub/grub.cfg
  94.7GB: boot/grub/menu.lst
  94.7GB: boot/grub/stage2
  94.7GB: boot/initrd.img-2.6.31-14-generic
  94.7GB: boot/initrd.img-2.6.31-16-generic
  94.7GB: boot/vmlinuz-2.6.31-14-generic
  94.7GB: boot/vmlinuz-2.6.31-16-generic
  94.7GB: initrd.img
  94.7GB: initrd.img.old
  94.7GB: vmlinuz
  94.7GB: vmlinuz.old
```

Do I have to remove grub off of sda1?

---

### Post by meierfra. on 2010-01-02
You install grub to the boot sector of  /dev/sda1, overwriting some of the information necessary to boot Windows. To fix it:

```

sudo apt-get install testdisk
sudo testdisk /dev/sda

```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the first Windows partition, sda1 (although it should be selected already) and choose
"boot"
"BackupBS"
Type "Y" to confirm
  
then press "q" a few times to quit  testdisk. Reboot and  you should get the Windows boot menu again.

---

### Post by rosatimr on 2010-01-02
I only have three options when I have the first Windows partition highlighted:
[Type]         [Image Creation]           [Quit]

---

### Post by meierfra. on 2010-01-02
Thats weird.

Plan B: run "bootrec /fixboot" from the Windows 7 DVD.  Detailed instructions  See "How to restore the Windows Vista or 7 bootloader" in [http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by rosatimr on 2010-01-02
It will have to wait until tomorrow.  I left my Windows 7 disk at my friends house.  Bummer.

---

### Post by meierfra. on 2010-01-02
Actually I figured out why testdisk did not give you the "boot" option. It's confused by the type of the partition. Try this

At the testdisk screen with the "[Type] [Image Creation] [Quit]" choose "Type". Press enter to proceed. type  17 and  press enter. Now you should  have the "Boot" option.

---

### Post by rosatimr on 2010-01-03
When #17 was highlighted and I press enter (to proceed), I get this
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

 1 * Windows RE(store)        0  32 33   850 207 61   13666304


    Previous
0a OS/2 Boot Manager    56 GoldenBow VFeature   be Solaris boot
0b FAT32                61 SpeedStor            bf Solaris
0c FAT32 LBA            63 Unixware, HURD, SCO  c1 secured FAT12
0e FAT16 LBA            64 NetWare 286          c4 secured FAT16
10 OPUS                 65 NetWare 3.11+        c6 sec. Huge-bad FAT16
11 hid. FAT12           67 Novell               c7 Syrinx Boot-bad NTFS
12 Compaq Diagnostics   68 Novell               d8 CP/M-86
14 hid. FAT16 <32M      69 Novell               db CP/M
16 hid. FAT16 >32M      70 DiskSecure MB        de Dell Utility
17 hid. HPFS/NTFS       75 PC/IX                e1 SpeedStor FAT12 ext          
18 AST swap             80 Minix v1.1-1.4a      e3 DOS RO
19 Willowtech Photon    81 Minix / old Linux    e4 SpeedStor FAT16 ext
    Next

New partition type [current 27] ? 
```

With the cursor blinking after that question mark.  What the?

---

### Post by meierfra. on 2010-01-03
Just press  "1" and "7" and  "enter".

---

### Post by rosatimr on 2010-01-03
This is what I got after I selected Boot, and BackupBS, and Y for confirm:

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63
     Partition                  Start        End    Size in sectors
 1 * hid. HPFS/NTFS           0  32 33   850 207 61   13666304

Boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Backup boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.


[  Quit  ]  [  List  ]  [Rebuild BS]  [Repair MFT]  [  Dump  ]
```

Is that all good?

---

### Post by meierfra. on 2010-01-03
That's fine. Just press "q" a few times to quit testdisk.

 Did you ever copy the file "linux.bin" from  your second windows partition to the first one?  Do

```
sudo mkdir sda1 sda2
sudo mount /dev/sda1 sda1
sudo mount /dev/sda2 sda2
sudo cp sda2/linux.bin  sda1/
```

Then reboot and hopefully  everything will be working.

---

### Post by rosatimr on 2010-01-03
Beautiful.  Thanks for all the help meierfra.  I would have not been able to do that without help.

---

### Post by meierfra. on 2010-01-03
> Thanks for all the help 

You are welcome. Have fun with Window 7 and Ubuntu.

---


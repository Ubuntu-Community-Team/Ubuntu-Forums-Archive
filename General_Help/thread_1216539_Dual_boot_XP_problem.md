---
title: "Dual boot XP problem"
date: 2009-07-18
forum: General Help
---

### Post by Jackie68 on 2009-07-18
Sorry if this is in the wrong place, as I'm new to this forum. 

Anyway, I had Windows XP  installed on my laptop and earlier today I installed Ubuntu 9.04 on a separate partition to form a dual boot. 

Loading Ubuntu is fine but when I click on XP in the grub menu it takes me to the previous Windows XP loading page and when I click on XP there I get this message "Windows could not start because of an error in the software. Load needed DLLs for kernel".

 Any help to solve this would be appreciated. Thanks.

---

### Post by merlinus on 2009-07-18
Open a terminal and post results of:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by Jackie68 on 2009-07-18
jackie@jackie-laptop:~$ sudo fdisk -1  
 fdisk: invalid option -- '1'  
 

 Usage: fdisk [-b SSZ] [-u] DISK     Change partition table  
        fdisk -l [-b SSZ] [-u] DISK  List partition table(s)  
        fdisk -s PARTITION           Give partition size(s) in blocks  
        fdisk -v                     Give fdisk version  
 Here DISK is something like /dev/hdb or /dev/sda  
 and PARTITION is something like /dev/hda7  
 -u: give Start and End in sector (instead of cylinder) units  
 -b 2048: (for certain MO disks) use 2048-byte sectors  
 

jackie@jackie-laptop:~$ cat /boot/grub/menu.lst  
 # menu.lst - See: grub(8), info grub, update-grub(8)
 #            grub-install(8), grub-floppy(8),  
 #            grub-md5-crypt, /usr/share/doc/grub  
 #            and /usr/share/doc/grub-doc/.  
 

 ## default num  
 # Set the default entry to the entry number NUM. Numbering starts from 0, and  
 # the entry number 0 is the default if the command is not used.  
 #  
 # You can specify 'saved' instead of a number. In this case, the default entry  
 # is the entry saved with the command 'savedefault'.  
 # WARNING: If you are using dmraid do not use 'savedefault' or your  
 # array will desync and will not let you boot your system.  
 default        0  
 

 ## timeout sec  
 # Set a timeout, in SEC seconds, before automatically booting the default entry  
 # (normally the first entry defined).  
 timeout        10  
 

 ## hiddenmenu  
 # Hides the menu by default (press ESC to see the menu)  
 #hiddenmenu  
 

 # Pretty colours  
 #color cyan/blue white/blue  
 

 ## password ['--md5'] passwd  
 # If used in the first section of a menu file, disable all interactive editing  
 # control (menu entry editor and command-line)  and entries protected by the  
 # command 'lock'  
 # e.g. password topsecret  
 #      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/  
 # password topsecret  
 

 #  
 # examples  
 #  
 # title        Windows 95/98/NT/2000  
 # root        (hd0,0)  
 # makeactive  
 # chainloader    +1  
 #  
 # title        Linux  
 # root        (hd0,1)  
 # kernel    /vmlinuz root=/dev/hda2 ro  
 #  
 

 #  
 # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST  
 

 ### BEGIN AUTOMAGIC KERNELS LIST  
 ## lines between the AUTOMAGIC KERNELS LIST markers will be modified  
 ## by the debian update-grub script except for the default options below  
 

 ## DO NOT UNCOMMENT THEM, Just edit them to your needs  
 

 ## ## Start Default Options ##  
 ## default kernel options  
 ## default kernel options for automagic boot options  
 ## If you want special options for specific kernels use kopt_x_y_z  
 ## where x.y.z is kernel version. Minor versions can be omitted.  
 ## e.g. kopt=root=/dev/hda1 ro  
 ##      kopt_2_6_8=root=/dev/hdc1 ro  
 ##      kopt_2_6_8_2_686=root=/dev/hdc2 ro  
 # kopt=root=UUID=e4447d71-dff1-4bba-b1f0-f1811af24eba ro  
 

 ## default grub root device  
 ## e.g. groot=(hd0,0)  
 # groot=e4447d71-dff1-4bba-b1f0-f1811af24eba  
 

 ## should update-grub create alternative automagic boot options  
 ## e.g. alternative=true  
 ##      alternative=false  
 # alternative=true  
 

 ## should update-grub lock alternative automagic boot options  
 ## e.g. lockalternative=true  
 ##      lockalternative=false  
 # lockalternative=false  
 

 ## additional options to use with the default boot option, but not with the  
 ## alternatives  
 ## e.g. defoptions=vga=791 resume=/dev/hda5  
 # defoptions=quiet splash  
 

 ## should update-grub lock old automagic boot options  
 ## e.g. lockold=false  
 ##      lockold=true  
 # lockold=false  
 

 ## Xen hypervisor options to use with the default Xen boot option  
 # xenhopt=  
 

 ## Xen Linux kernel options to use with the default Xen boot option  
 # xenkopt=console=tty0  
 

 ## altoption boot targets option  
 ## multiple altoptions lines are allowed  
 ## e.g. altoptions=(extra menu suffix) extra boot options  
 ##      altoptions=(recovery) single  
 # altoptions=(recovery mode) single  
 

 ## controls how many kernels should be put into the menu.lst  
 ## only counts the first occurence of a kernel, not the  
 ## alternative kernel options  
 ## e.g. howmany=all  
 ##      howmany=7  
 # howmany=all  
 

 ## specify if running in Xen domU or have grub detect automatically  
 ## update-grub will ignore non-xen kernels when running in domU and vice versa  
 ## e.g. indomU=detect  
 ##      indomU=true  
 ##      indomU=false  
 # indomU=detect  
 

 ## should update-grub create memtest86 boot option  
 ## e.g. memtest86=true  
 ##      memtest86=false  
 # memtest86=true  
 

 ## should update-grub adjust the value of the default booted system  
 ## can be true or false  
 # updatedefaultentry=false  
 

 ## should update-grub add savedefault to the default options  
 ## can be true or false  
 # savedefault=false  
 

 ## ## End Default Options ##  
 

 title        Ubuntu 9.04, kernel 2.6.28-11-generic  
 uuid        e4447d71-dff1-4bba-b1f0-f1811af24eba 
 kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e4447d71-dff1-4bba-b1f0-f1811af24eba ro quiet splash  
 initrd        /boot/initrd.img-2.6.28-11-generic 
 quiet  
 

 title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)  
 uuid        e4447d71-dff1-4bba-b1f0-f1811af24eba 
 kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e4447d71-dff1-4bba-b1f0-f1811af24eba ro  single  
 initrd        /boot/initrd.img-2.6.28-11-generic 
 

 title        Ubuntu 9.04, memtest86+  
 uuid        e4447d71-dff1-4bba-b1f0-f1811af24eba 
 kernel        /boot/memtest86+.bin  
 quiet  
 

 ### END DEBIAN AUTOMAGIC KERNELS LIST  
 

 # This is a divider, added to separate the menu items below from the Debian  
 # ones.  
 title        Other operating systems:  
 root  
 

 

 # This entry automatically added by the Debian installer for a non-linux OS  
 # on /dev/sda3  
 title        Microsoft Windows XP Home Edition  
 rootnoverify    (hd0,2)  
 savedefault  
 makeactive  
 chainloader    +1

---

### Post by ramnarayan on 2009-07-18
> **Jackie68 said:**
> Sorry if this is in the wrong place, as I'm new to this forum. 

Anyway, I had Windows XP  installed on my laptop and earlier today I installed Ubuntu 9.04 on a separate partition to form a dual boot. 
.

was your xp working when you installed Ubuntu ??

---

### Post by merlinus on 2009-07-18
l is a lowercase L -- sudo fdisk -l

---

### Post by Jackie68 on 2009-07-18
> **r[LEFT][COLOR=red][FONT=serif]**_amnarayan said:**
> [/COLOR][/LEFT]7637212]was your x[LEFT][COLOR=red][FONT=serif]**_p _**[/FONT][/COLOR][/LEFT]working when you installed U[LEFT][COLOR=red][FONT=serif]**_buntu _**[/FONT][/COLOR][/LEFT]??
It was working normally until I installed Ubu[LEFT][COLOR=red][FONT=serif]**_ntu.  _**[/FONT][/COLOR][/LEFT]

---

### Post by ramnarayan on 2009-07-18
Ok two things, it would have been helpful to have fdisk -l but if you cannot post that 

try this
```
sudo fdisk -l > fdisk.txt
```

this will send the output to a text file in youe /home/foouser/ directory from where you can copy and paste

Or you can copy in the terminal by selecting it and pressing ctrl+Shift+copy to copy.

Second - lest see your menu.lst entry for windows xp 
> **Jackie68 said:**
> jackie@jackie-laptop:~$ 
 # This entry automatically added by the Debian installer for a non-linux OS  
 # on /dev/sda3  
 title        Microsoft Windows XP Home Edition  
 rootnoverify    (hd0,2)  
 savedefault  
 makeactive  
 chainloader    +1

the rootverify   (hd0,2) indicates where the boot loader for windows is

if windows was installed first and on your first primary partition then it should be (hd0,0)

try and change this and see if you can boot to windows.

If not post back fdisk -l as above as well as 
df -h

---

### Post by Jackie68 on 2009-07-18
> **merlinus said:**
> l is a lowercase L -- sudo fdisk -l
Sorry about that. :P

          Disk /dev/sda: 80.0 GB, 80026361856 bytes  
 255 heads, 63 sectors/track, 9729 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0x2996ace0  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1               1         997     8008371   83  Linux  
 /dev/sda2             998        1274     2225002+   5  Extended  
 /dev/sda3   *        1275        9729    67914787+   7  HPFS/NTFS  
 /dev/sda5             998        1274     2224971   82  Linux swap / Solaris  
 

 Disk /dev/sdb: 1010 MB, 1010826752 bytes  
 255 heads, 63 sectors/track, 122 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0x91f72d24  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb1   *           1         123      987104    6  FAT16  
 Partition 1 has different physical/logical endings:  
      phys=(121, 254, 63) logical=(122, 227, 40)

---

### Post by merlinus on 2009-07-18
You might try supergrub to boot xp and fix grub.

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by ramnarayan on 2009-07-18
> **Jackie68 said:**
> 
          Disk /dev/sda: 80.0 GB, 
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1               1         997     8008371   83  Linux  
 /dev/sda2             998        1274     2225002+   5  Extended  
 /dev/sda3   *        1275        9729    67914787+   7  HPFS/NTFS  
 /dev/sda5             998        1274     2224971   82  Linux swap / Solaris  
 

 Disk /dev/sdb: 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb1   *           1         123      987104    6  FAT16  
 

Ok
your menu.lst entry was correct
Windows is located where is says
sda3 = (HD0,2)

However its not the primary partition and infact a logical partition of an extended primary, and am wondering if that is causing the problem. Hope someone can say what next because this is out of my league, meaning i don't know how to rectify that

Second - what is the vfat device thats appearing looks to me like a bootable flash disk, if thats so why not pull that out and try the boot up again ?? 

Third - from your partition table it seems you have only swap and only one partition for your Ubuntu /

It may not be helpful here but its useful to have a separate /(root) where all the Ubuntu os is located, a separate /boot where you can manipulate multiple boots and a separate /home this so that whatever you do to your OS your work and other data remains safe.

Finally, is it possible that you can reinstall XP again - if so do that start afresh reinstall XP and then do Ubuntu but make sure XP is kept in the first primary partition.

This last makes me wonder - did you know you where going to install Ubuntu when you were installing WIn XP and could that be a reason why you kept Windows XP in a logical partition

---

### Post by c0mput3r_n3rD on 2009-07-18
If you can find what DLL's are missing, you could download them from ubuntu and put them in the correct folder.

---

### Post by Jackie68 on 2009-07-18
Thanks for the help guys. I finally got it to work by following a suggestion of replacing the hal.dll in system32 and unbelievably it's worked. :o :)

---


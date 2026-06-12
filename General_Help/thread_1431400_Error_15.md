---
title: "Error 15"
date: 2010-03-16
forum: General Help
---

### Post by s-jwagone2 on 2010-03-16
I'm running a Lenovo ThinkPad T61, dualbooting Vista and Ubuntu 9.10. 
I had a virus on Vista, so I used system restore to fix it and I haven't been able to run my precious Ubuntu since. I don't know what a distro is, although I have been running linux for about a year now, I am essentially helpless to solve its problems.(This is all from a live disk)

 

  I keep getting “Error 15: File not found” whenever I try to boot ubuntu with grub.  

The screen that comes up has: 

> Grub
Ubuntu 9.10, Kernel 2.6.31-16-generic
Ubuntu 9.10, Kernel 2.6.31-15-generic (recovery mode)
(There are several more of these options, I'm assuming different updated versions of ubuntu)
Windows Vista/Longhorn loader (This is the safe mode option)
Windows Vista/Longhorn loaderWhen I click on any of the ubuntu options, the grub screen says: 

Boot from (hd0,4) ext3 e2f54956-1248-49f3-b518-c5f4436731b8. 
Error 15: File not found. 
 

 My friend who is a computer science grad student, tester, etc, said I need to reinstall grub. I'm Pretty sure I'm running grub, not grub 2.


 So I searched the web for grub re-installation stuff
 

 I scoured the first five, and last ten pages of this thread (I'm not trying to double post!)
 [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
 

 Nothing seemed to help.  
 

 Here are some of the things I tried...

                                 ```
ubuntu@ubuntu:~$ sudo fdisk -l  
```Here's what it found:


                           ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes  
 255 heads, 63 sectors/track, 19457 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0x56128d5f  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1               1         821     6592512   27  Unknown  
 Partition 1 does not end on cylinder boundary.  
 /dev/sda2   *         821       17290   132287484    7  HPFS/NTFS  
 Partition 2 does not end on cylinder boundary.  
 /dev/sda3           17291       17316      204120   83  Linux  
 Partition 3 does not end on cylinder boundary.  
 /dev/sda4           17316       19457    17199000    5  Extended  
 Partition 4 does not end on cylinder boundary.  
 /dev/sda5           17316       18432     8958568+  83  Linux  
 /dev/sda6           19362       19457      763528+  82  Linux swap / Solaris  
 
```                                   Then I did the find grub thing:
 

```
grub> find /boot/grub/stage1  
  (hd0,4)  
  grub> sudo grub  
  Error 27: Unrecognized command  
   
 grub> root (hd0,5)  
  grub> setup (hd0)  
  Error 17: Cannot mount selected partition  
  grub>  
  grub> find /grub/stage2  
  (hd0,2)  
  grub> find /grub/stage1  
  (hd0,2)  

```It looks to me that it is trying to boot from a different partition than where ubuntu is, but I don't know...

                                 I downloaded boot_info_script055.sh and ran it in terminal this is what was in terminal:


                           ```

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh  
 Identifying MBRs...  
 Computing Partition Table of /dev/sda...  
 Searching sda1 for information...  
 Searching sda2 for information...  
 Searching sda3 for information...  
 Searching sda4 for information...  
 Searching sda5 for information...  
 Searching sda6 for information...  
 Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop  
 

  
```                                 Here is RESULTS.txt from my desktop:[INDENT] Boot Info Script 0.55    dated February 15th, 2010                     


============================= Boot Info Summary: ==============================  


 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive  
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.  


sda1: _________________________________________________________________________ 


    File system:       ntfs  
    Boot sector type:  Windows Vista/7  
    Boot sector info:  No errors found in the Boot Parameter Block.  
    Operating System:   
    Boot files/dirs:   /bootmgr /boot/bcd  


sda2: _________________________________________________________________________ 


    File system:       ntfs  
    Boot sector type:  Windows Vista/7  
    Boot sector info:  No errors found in the Boot Parameter Block.  
    Operating System:  Windows Vista  
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe  


sda3: _________________________________________________________________________ 


    File system:       ext3  
    Boot sector type:  -  
    Boot sector info:   
    Operating System:   
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf  


sda4: _________________________________________________________________________ 


    File system:       Extended Partition  
    Boot sector type:  -  
    Boot sector info:   


sda5: _________________________________________________________________________ 


    File system:       ext3  
    Boot sector type:  -  
    Boot sector info:   
    Operating System:  Ubuntu 9.10  
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab  


sda6: _________________________________________________________________________ 


    File system:       swap  
    Boot sector type:  -  
    Boot sector info:   


=========================== Drive/Partition Info: =============================  


Drive: sda ___________________ _____________________________________________________  


Disk /dev/sda: 160.0 GB, 160041885696 bytes  
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors  
Units = sectors of 1 * 512 = 512 bytes  
Disk identifier: 0x56128d5f  


Partition  Boot         Start           End          Size  Id System  


/dev/sda1               2,048    13,187,071    13,185,024  27 Hidden HPFS/NTFS  
/dev/sda2    *     13,187,072   277,762,039   264,574,968   7 HPFS/NTFS  
/dev/sda3         277,769,520   278,177,759       408,240  83 Linux  
/dev/sda4         278,177,760   312,575,759    34,398,000   5 Extended  
/dev/sda5         278,177,823   296,094,959    17,917,137  83 Linux  
/dev/sda6         311,048,703   312,575,759     1,527,057  82 Linux swap / Solaris  




blkid -c /dev/null: ____________________________________________________________  


Device           UUID                                   TYPE       LABEL                          


/dev/loop0                                              squashfs                                  
/dev/sda1        4C4E30E34E30C80A                       ntfs       ServiceV002                    
/dev/sda2        0E4E36934E367415                       ntfs       SW_Preload                     
/dev/sda3        00f3887e-f308-4788-a416-100e138a8017   ext3       /boot                          
/dev/sda5        e2f54a56-1248-49f3-b518-c5f4436731b8   ext3                                      
/dev/sda6        0935fda0-1ab5-49d6-9f15-96583f4ef6d5   swap                                      


============================ "mount | grep ^/dev  output: ===========================  


Device           Mount_Point              Type       Options  


aufs             /                        aufs       (rw)  
/dev/sr0         /cdrom                   iso9660    (rw)  
/dev/loop0       /rofs                    squashfs   (rw)  




============================= sda3/grub/grub.conf: =============================  


# grub.conf generated by anaconda  
#  
# Note that you do not have to rerun grub after making changes to this file  
# NOTICE:  You have a /boot partition.  This means that  
#          all kernel and initrd paths are relative to /boot/, eg.  
#          root (hd0,2)  
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00  
#          initrd /initrd-version.img  
#boot=/dev/sda  
default=0  
timeout=5  
splashimage=(hd0,2)/grub/splash.xpm.gz  
hiddenmenu  
title Fedora (2.6.29.5-191.fc11.i586)  
    root (hd0,2)  
    kernel /vmlinuz-2.6.29.5-191.fc11.i586 ro root=/dev/VolGroup00/LogVol00 rhgb quiet  
    initrd /initrd-2.6.29.5-191.fc11.i586.img  
title Other  
    rootnoverify (hd0,1)  
    chainloader +1  


=================== sda3: Location of files loaded by Grub: ===================  




 142.2GB: grub/grub.conf  
 142.2GB: grub/menu.lst  
 142.2GB: grub/stage2  
 142.2GB: initrd-2.6.29.5-191.fc11.i586.img  
 142.2GB: vmlinuz-2.6.29.5-191.fc11.i586  


=========================== sda5/boot/grub/menu.lst: ===========================  


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
# kopt=root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro  


## default grub root device  
## e.g. groot=(hd0,0)  
# groot=e2f54a56-1248-49f3-b518-c5f4436731b8  
  
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


title        Ubuntu 9.10, kernel 2.6.31-16-generic  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro quiet splash  
initrd        /boot/initrd.img-2.6.31-16-generic 
quiet  


title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro  single  
initrd        /boot/initrd.img-2.6.31-16-generic 


title        Ubuntu 9.10, kernel 2.6.31-15-generic  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro quiet splash  
initrd        /boot/initrd.img-2.6.31-15-generic 
quiet  


title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro  single  
initrd        /boot/initrd.img-2.6.31-15-generic 


title        Ubuntu 9.10, kernel 2.6.31-14-generic  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro quiet splash  
initrd        /boot/initrd.img-2.6.31-14-generic 
quiet  


title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro  single  
initrd        /boot/initrd.img-2.6.31-14-generic 


title        Ubuntu 9.10, kernel 2.6.28-16-generic  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro quiet splash  
initrd        /boot/initrd.img-2.6.28-16-generic 
quiet  


title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro  single  
initrd        /boot/initrd.img-2.6.28-16-generic 


title        Ubuntu 9.10, kernel 2.6.27-15-generic  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/vmlinuz-2.6.27-15-generic root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro quiet splash  
initrd        /boot/initrd.img-2.6.27-15-generic 
quiet  


title        Ubuntu 9.10, kernel 2.6.27-15-generic (recovery mode)  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/vmlinuz-2.6.27-15-generic root=UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 ro  single  
initrd        /boot/initrd.img-2.6.27-15-generic 


title        Ubuntu 9.10, memtest86+  
uuid        e2f54a56-1248-49f3-b518-c5f4436731b8 
kernel        /boot/memtest86+.bin  
quiet  


### END DEBIAN AUTOMAGIC KERNELS LIST  


# This is a divider, added to separate the menu items below from the Debian  
# ones.  
title        Other operating systems:  
root  
  


# This entry automatically added by the Debian installer for a non-linux OS  
# on /dev/sda1  
title        Windows Vista/Longhorn (loader)  
root        (hd0,0)  
savedefault  
makeactive  
chainloader    +1  




# This entry automatically added by the Debian installer for a non-linux OS  
# on /dev/sda2  
title        Windows Vista/Longhorn (loader)  
root        (hd0,1)  
savedefault  
makeactive  
chainloader    +1  




=============================== sda5/etc/fstab: ===============================  


# /etc/fstab: static file system information.  
#  
# <file system> <mount point>   <type>  <options>       <dump>  <pass>  
proc            /proc           proc    defaults        0       0  
# /dev/sda5  
UUID=e2f54a56-1248-49f3-b518-c5f4436731b8 /               ext3    relatime,errors=remount-ro 0       1  
# /dev/sda6  
UUID=0935fda0-1ab5-49d6-9f15-96583f4ef6d5 none            swap    sw              0       0  
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0  


=================== sda5: Location of files loaded by Grub: ===================  




 150.1GB: boot/grub/menu.lst  
 143.2GB: boot/grub/stage2
[/INDENT]I tried this:  
 

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu  
 ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/ubuntu  
 ubuntu@ubuntu:~$ sudo grub-instal /dev/sda --root-directory=/mnt/ubuntu  
 sudo: grub-instal: command not found  
 ubuntu@ubuntu:~$  
 
```.....didn't work. 



From this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I got:   


```
ubuntu@ubuntu:~$ mount | tail -1 
 /dev/sda5 on /media/e2f54a56-1248-49f3-b518-c5f4436731b8 type ext3 (rw,nosuid,nodev,uhelper=devkit)
 

 ubuntu@ubuntu:~$ ls /media/e2f54a56-1248-49f3-b518-c5f4436731b8 
 bin   cdrom  etc   lib         media  opt   root  selinux  sys  usr 
 boot  dev    home  lost+found  mnt    proc  sbin  srv      tmp  var 
 

 ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/e2f54a56-1248-49f3-b518-c5f4436731b8 /dev/sda 
 grub-probe: error: Cannot open `/boot/grub/device.map' 
 [: 494: =: unexpected operator 
 Installing GRUB to /dev/sda as (hd0)... 
 Installation finished. No error reported. 
 This is the contents of the device map /media/e2f54a56-1248-49f3-b518-c5f4436731b8/boot/grub/device.map. 
 Check if this is correct or not. If any of the lines is incorrect, 
 fix it and re-run the script `grub-install'. 
  
 (hd0)    /dev/sda 
 ubuntu@ubuntu:~$  

```                                  Should I try the super grub disk?...whatever that means  
 

 I tried running a few commands that had “.lst” in it and the list came up empty...I don't think this is supposed to happen. 



I am totally lost, and this is really frustrating as I recently got ubuntu to work the way I wanted it to #-o. Sorry the post is so long, but I figured more info is better than less.

---

### Post by s-jwagone2 on 2010-03-30
Oh c'mon somebody has to know something....

Anybody?

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
The answer is actually in your post like 7 times. update-grub. Open a terminal in the live cd and type ```
sudo update-grub
```

---

### Post by oldfred on 2010-03-30
It looks like you have a separate boot partition.

grub> find /boot/grub/stage1  
  [COLOR=DarkRed](hd0,4[/COLOR])  
  grub> sudo grub  
  Error 27: Unrecognized command  
   
 grub> root ([COLOR=DarkRed]hd0,5[/COLOR])  
  grub> setup (hd0)

Your entries have to be the same.

But because you have a boot partition this find was the correction one but you did not complete  the root & setup.

grub> find /grub/stage2  
  (hd0,2)

---


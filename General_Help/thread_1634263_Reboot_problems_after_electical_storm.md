---
title: "Reboot problems after electical storm"
date: 2010-11-30
forum: General Help
---

### Post by brewster-mac on 2010-11-30
Ubuntu 9.10  (noob)

Rebooting and selecting the following option ...
Ubuntu 9.10, kernel 2.6.31-34-fitpc2 (recovery mode)

I get part-way through bootup and after a few errors it ends with a suggestion,

[4.9979001] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[5.026082] EXT3 on sda1, internal journal


Then after about 60 seconds I have a 'Recovery Menu' displayed.

How do I go about running the file e2fsck, what is the correct syntax and how do I get the desktop to display or is it a lost cause and I need to reinstall Ubuntu?

Thanks for your help.

---

### Post by Rubi1200 on 2010-11-30
Hi and welcome to the forums :)

Is sda1 your Ubuntu install?

If yes, use the LiveCD (make sure no partitions are mounted) and run the following commands:
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

if it reports errors, run this:
```
sudo e2fsck -f -y -v /dev/sda1
```

Reboot without the CD and let us know if it worked.

---

### Post by brewster-mac on 2010-11-30
Thanks for the quick reply. As its 3Am I will get some shuteye now and try this later on today with hopefully a clearer head.

Very much appreciated.

---

### Post by Rubi1200 on 2010-11-30
No problem, let us know how it works out please.

---

### Post by Dans564 on 2010-11-30
sounds like the storm took out some hardware, like your HDD #-o
I hope not that would stink.  SURGE PROTECTOR OR UPS BACKUP!!  Best of luck though lol:p

---

### Post by brewster-mac on 2010-11-30
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Is sda1 your Ubuntu install?

If yes, use the LiveCD (make sure no partitions are mounted) and run the following commands:
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```if it reports errors, run this:
```
sudo e2fsck -f -y -v /dev/sda1
```Reboot without the CD and let us know if it worked.

Ok. I have Ubuntu 9.10 on a USB stick and have booted using the USB stick.
The hard drive that needs repair of which the FitPC2 Ubuntu install is on, is /dev/sda1 159Gb Ext3
with a 1.1Gb Swap Space on /dev/sda2

Now the USB stick has partitions ...
16Gb MYLINUXLIVE on /dev/sdb1   FAT32
131Mb file system on /dev/sdbd2   Ext3
131Mb unrecognised on /dev/sdb3

Where you have said 'make sure no partitions are mounted', does this appear ok to go ahead and run the command/s as suggested?

Thanks.

---

### Post by Rubi1200 on 2010-12-01
Yes, if the partition is sda1 then you can go ahead and try the commands.

If they are mounted, fsck will report an error anyway (I believe).

---

### Post by brewster-mac on 2010-12-01
> **Rubi1200 said:**
> Yes, if the partition is sda1 then you can go ahead and try the commands.

If they are mounted, fsck will report an error anyway (I believe).

Ran the first command and after a couple of hours I have ended up with...

------------------------------------------------------------------------------------------------
Entry 'linc-1ca4-0-6714864fab5f' in /tmp/orbit-fit (303062) has deleted/unused inode 311383. CLEARED.
FITPC2_FS: Entry 'linc-6936-0-69d2b1b5b6e39' in /tmp/orbit-fit (303062) has deleted/unused inode 362001. CLEARED.
Unattached inode 371148

FITPC2_FS: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
-----------------------------------------------------------------------------------------------

I assume I should run the second command now (but to be sure I'll wait for comformation)

Thanks again for your assistance!

---

### Post by Rubi1200 on 2010-12-01
Yes, run the second command now and let's keep our fingers crossed.

Let me know what happens please.

---

### Post by brewster-mac on 2010-12-02
Took ~8 hours to complete that command and there were many fixes performed and all appeared to have 'yes' response for each error.

Removed USB stick and stated a normal bootup, until it hung after displaying this text 

[B][2.576102] usb 4-1: new full speed USB device using uhci_hcd and address 2
[2.743498] [/B]**usb 4-1: configuration #1 chosen from 1 choice**
**init: ureadahead main process (403) terminated with status 5**

This info showed previously when attempting normal bootup initially


Is there anything else that can be done?


Thanks for your continued help.

---

### Post by Rubi1200 on 2010-12-02
Hi brewster-mac,
could you please boot from the USB again and run the boot info script.

It is linked at the bottom of my post (instructions included).

Post the results back here and we will try and find out what is going on.

Thanks.

EDIT: if you have any other external devices plugged in I would try removing them and booting. Also, check your BIOS for boot priority settings (maybe something got messed up?).

If none of that works, run the script please.

---

### Post by brewster-mac on 2010-12-02
Later I tried a reboot in (Recovery mode) ...

After loading a number of files this was the last text displayed before it hung ...

[B]AppArmor parser error in /etc/aparmor.d/usr.sbin.ntpd at line 1: Found unexpected character: ''
Failure: AppArmor profiles failed to load
Done.
init: ureadahead main process (387) terminated with status 5
[32.694416] EXT3 FS on sda1, internal journal[/B]


Thanks.

---

### Post by brewster-mac on 2010-12-02
I just noticed you had already replied to my previous post. Sorry, I will give that a try

---

### Post by brewster-mac on 2010-12-02
Here is the result of running the boot info script.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa49732da

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   310,391,864   310,391,802  83 Linux
/dev/sda2         310,391,865   312,576,704     2,184,840  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.2 GB, 16166944768 bytes
64 heads, 32 sectors/track, 15418 cylinders, total 31576064 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    31,064,063    31,064,032   c W95 FAT32 (LBA)
/dev/sdb2          31,064,064    31,320,063       256,000  83 Linux
/dev/sdb3          31,320,064    31,576,063       256,000  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        49239d23-e54b-49df-a518-8ff0e0f71ea1   ext3       FITPC2_FS                     
/dev/sda2        d9ac921a-31d5-4153-a5ad-0ab44c84a836   swap       FITPC2_SWAP                   
/dev/sdb1        E059-9536                              vfat       MYLINUXLIVE                   
/dev/sdb2        cff5d832-23cc-456b-90df-cfab9c87bc45   ext3                                     
/dev/sdb3                                               swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=splash

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-34-fitpc2
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-34-fitpc2 root=LABEL=FITPC2_FS ro splash 
initrd        /boot/initrd.img-2.6.31-34-fitpc2
quiet

title        Ubuntu 9.10, kernel 2.6.31-34-fitpc2 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-34-fitpc2 root=LABEL=FITPC2_FS ro  single
initrd        /boot/initrd.img-2.6.31-34-fitpc2

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>     <mount point>   <type>  <options>       <dump>  <pass>
proc                   /proc           proc    defaults        0       0
LABEL=FITPC2_FS        /               ext3    errors=remount-ro 0       0
LABEL=FITPC2_SWAP    none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .9GB: boot/grub/menu.lst
   3.0GB: boot/grub/stage2
   1.7GB: boot/initrd.img-2.6.31-34-fitpc2
   1.3GB: boot/vmlinuz-2.6.31-34-fitpc2
   1.7GB: initrd.img
   1.3GB: vmlinuz
```

---

### Post by Rubi1200 on 2010-12-02
Is there a particular reason you still have GRUB-legacy?

Was this an upgrade from 9.04?

Versions from 9.10 onwards use GRUB2 and I advise you to use it.

As long as the drive and file-system were not damaged in all this, let's try and purge and reinstall GRUB2.

This needs to be done from the LiveCD using this guide for the chroot method by drs305:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by brewster-mac on 2010-12-02
Hi,

This was the version of Ubuntu pre-installed when I purchased the fitPC2

[http://www.fit-pc.com/web/fit-pc2/fit-pc2-specifications/](http://www.fit-pc.com/web/fit-pc2/fit-pc2-specifications/)[URL="http://www.fit-pc.com/web/fit-pc2/fit-pc2-specifications/"]
[/URL]

---

### Post by brewster-mac on 2010-12-02
I did not appear to get an opportunity to specify sda1
I was presented with a text input line on a colored screen but I didn't know the syntax to write, it didn't display any options?
Sorry if I am mucking this up. Can I run that same command again?


```
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libqt4-dbus os-prober libqt4-xml libqt4-network
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub* grub-common*
0 upgraded, 0 newly installed, 2 to remove and 77 not upgraded.
After this operation, 3,363kB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 138999 files and directories currently installed.)
Removing grub ...
Purging configuration files for grub ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
root@ubuntu:/# 
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-dbus libqt4-xml libqt4-network
Use 'apt-get autoremove' to remove them.
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 77 not upgraded.
Need to get 1,428kB of archives.
After this operation, 4,170kB of additional disk space will be used.
Get:1 http://mirror.aarnet.edu.au karmic-updates/main grub-common 1.97~beta4-1ubuntu4.1 [994kB]
Get:2 http://mirror.aarnet.edu.au karmic-updates/main grub-pc 1.97~beta4-1ubuntu4.1 [434kB]                                                             
Fetched 1,428kB in 10s (143kB/s)                                                                                                                        
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub-common.
(Reading database ... 138908 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4.1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for ureadahead ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
sed: warning: failed to get security context of /tmp/grub.5hfFwvzzwN: No data availablesed: warning: failed to get security context of /tmp/grub.5hfFwvzzwN: No data availablesed: warning: failed to get security context of /tmp/grub.5hfFwvzzwN: No data availablesed: warning: failed to get security context of /tmp/grub.5hfFwvzzwN: No data available
Creating config file /etc/default/grub with new version
Generating core.img
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 
root@ubuntu:/# 

```

---

### Post by oldfred on 2010-12-02
Your list does not show the chroot. Did you chroot into sda1 before running the commands?

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by brewster-mac on 2010-12-02
Yes I did, sorry I didn't include that part!

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp /mnt/temp/boot
mkdir: cannot create directory `/mnt/temp': File exists
mkdir: cannot create directory `/mnt/temp/boot': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
Hit http://mirror.aarnet.edu.au karmic Release.gpg
Ign http://mirror.aarnet.edu.au karmic/main Translation-en_US                                                                    
Ign http://mirror.aarnet.edu.au karmic/restricted Translation-en_US                                                              
Ign http://mirror.aarnet.edu.au karmic/universe Translation-en_US                                                                
Ign http://mirror.aarnet.edu.au karmic/multiverse Translation-en_US                                                              
Get:1 http://mirror.aarnet.edu.au karmic-updates Release.gpg [198B]                                                              
Ign http://mirror.aarnet.edu.au karmic-updates/main Translation-en_US                                                            
Ign http://mirror.aarnet.edu.au karmic-updates/restricted Translation-en_US                                                      
Ign http://mirror.aarnet.edu.au karmic-updates/universe Translation-en_US                                                        
Ign http://mirror.aarnet.edu.au karmic-updates/multiverse Translation-en_US                                                      
Get:2 http://mirror.aarnet.edu.au karmic-security Release.gpg [198B]                                                             
Ign http://mirror.aarnet.edu.au karmic-security/main Translation-en_US                                                           
Ign http://mirror.aarnet.edu.au karmic-security/restricted Translation-en_US                                                     
Ign http://mirror.aarnet.edu.au karmic-security/universe Translation-en_US                       
Ign http://mirror.aarnet.edu.au karmic-security/multiverse Translation-en_US                     
Hit http://mirror.aarnet.edu.au karmic Release                                                   
Get:3 http://mirror.aarnet.edu.au karmic-updates Release [51.3kB]                                
Get:4 http://ppa.launchpad.net karmic Release.gpg [316B]                                                                  
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                   
Hit http://packages.medibuntu.org karmic Release.gpg                                                                         
Get:5 http://mirror.aarnet.edu.au karmic-security Release [51.3kB]                                                               
Hit http://mirror.aarnet.edu.au karmic/main Packages                                                                             
Get:6 http://ppa.launchpad.net karmic Release [66.0kB]                                                                           
Hit http://mirror.aarnet.edu.au karmic/restricted Packages                                                                       
Hit http://mirror.aarnet.edu.au karmic/main Sources                                                                              
Hit http://mirror.aarnet.edu.au karmic/restricted Sources                                                                        
Hit http://mirror.aarnet.edu.au karmic/universe Packages                                                                         
Hit http://mirror.aarnet.edu.au karmic/universe Sources                                                                          
Hit http://mirror.aarnet.edu.au karmic/multiverse Packages                                                                       
Hit http://mirror.aarnet.edu.au karmic/multiverse Sources                                                                        
Get:7 http://mirror.aarnet.edu.au karmic-updates/main Packages [311kB]                                                           
Get:8 http://mirror.aarnet.edu.au karmic-updates/restricted Packages [1,631B]                                                    
Get:9 http://mirror.aarnet.edu.au karmic-updates/main Sources [157kB]                                                            
Get:10 http://mirror.aarnet.edu.au karmic-updates/restricted Sources [878B]                                                      
Get:11 http://mirror.aarnet.edu.au karmic-updates/universe Packages [183kB]                                                      
Get:12 http://ppa.launchpad.net karmic/main Packages [3,706B]                                                                    
Ign http://packages.medibuntu.org karmic/free Translation-en_US                                                                  
Get:13 http://mirror.aarnet.edu.au karmic-updates/universe Sources [62.5kB]                                                      
Get:14 http://mirror.aarnet.edu.au karmic-updates/multiverse Packages [11.4kB]                                                   
Ign http://fit-pc2.com binary/ Release.gpg                                                                                       
Ign http://fit-pc2.com binary/ Translation-en_US                                                                                 
Get:15 http://mirror.aarnet.edu.au karmic-updates/multiverse Sources [5,628B]                                                    
Get:16 http://mirror.aarnet.edu.au karmic-security/main Packages [194kB]                                                         
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US                                                              
Ign http://fit-pc2.com source/ Release.gpg                                                                                       
Ign http://fit-pc2.com binary/ Release                                                                                           
Get:17 http://mirror.aarnet.edu.au karmic-security/restricted Packages [14B]                                                     
Get:18 http://mirror.aarnet.edu.au karmic-security/main Sources [117kB]                                                          
Ign http://fit-pc2.com source/ Release                                                                                           
Get:19 http://mirror.aarnet.edu.au karmic-security/restricted Sources [14B]                                                      
Get:20 http://mirror.aarnet.edu.au karmic-security/universe Packages [91.0kB]                                                    
Get:21 http://mirror.aarnet.edu.au karmic-security/universe Sources [31.9kB]                                                     
Hit http://packages.medibuntu.org karmic Release                                                                                 
Get:22 http://mirror.aarnet.edu.au karmic-security/multiverse Packages [4,713B]                                                  
Get:23 http://mirror.aarnet.edu.au karmic-security/multiverse Sources [1,425B]                                                   
Hit http://packages.medibuntu.org karmic/free Packages                                                                           
Ign http://fit-pc2.com binary/ Packages                                                                                          
Ign http://fit-pc2.com source/ Sources                                                                                           
Hit http://packages.medibuntu.org karmic/non-free Packages                                                                         
Ign http://fit-pc2.com binary/ Packages                                                                                            
Ign http://fit-pc2.com source/ Sources                                                                                             
Hit http://fit-pc2.com binary/ Packages                                                                                            
Hit http://fit-pc2.com source/ Sources                                                                                             
Fetched 1,346kB in 12s (108kB/s)                                                                                                   
Reading package lists... Done
root@ubuntu:/# 
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libqt4-dbus os-prober libqt4-xml libqt4-network
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub* grub-common*
0 upgraded, 0 newly installed, 2 to remove and 77 not upgraded.
After this operation, 3,363kB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 138999 files and directories currently installed.)
Removing grub ...
Purging configuration files for grub ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
root@ubuntu:/# 
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-dbus libqt4-xml libqt4-network
Use 'apt-get autoremove' to remove them.
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 77 not upgraded.
Need to get 1,428kB of archives.
After this operation, 4,170kB of additional disk space will be used.
Get:1 http://mirror.aarnet.edu.au karmic-updates/main grub-common 1.97~beta4-1ubuntu4.1 [994kB]
Get:2 http://mirror.aarnet.edu.au karmic-updates/main grub-pc 1.97~beta4-1ubuntu4.1 [434kB]                                                             
Fetched 1,428kB in 10s (143kB/s)                                                                                                                        
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub-common.
(Reading database ... 138908 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4.1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for ureadahead ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
sed: warning: failed to get security context of /tmp/grub.5hfFwvzzwN: No data availablesed: warning: failed to get security context of /tmp/grub.5hfFwvzzwN: No data availablesed: warning: failed to get security context of /tmp/grub.5hfFwvzzwN: No data availablesed: warning: failed to get security context of /tmp/grub.5hfFwvzzwN: No data available
Creating config file /etc/default/grub with new version
Generating core.img
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 
root@ubuntu:/# 

```

---

### Post by oldfred on 2010-12-02
I did not see 
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done

I would reboot the liveCD so you do not get the errors on mounts existing (but that should not matter.
And rerun all the commands from full chroot:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by brewster-mac on 2010-12-02
Ok. I got through the re-install process using Chroot until I get to section ...

4. Reinstall the grub packages

I entered the command    
apt-get install grub-common grub-pc

Program executes and I am presented with a new window that has a prompt to enter a Linux command line:

At the top of the window it says 'Configuring grub-pc'

Then the following text ...
The following Linux command line was extracted from /etc/default/grub or the 'kopt' parameter in GRUB Legacy's menu.lst. 
Please verify that it is correct, and modify it if necessary.

Then it shows an area to type in some text which is 'blank' at the moment.



Is this where the startup sequence originally faltered when it said there was an unrecognised character ''  ?

Continuing Thanks for this help :)

I've left the install at this prompt for text entry.

---

### Post by oldfred on 2010-12-02
The first couple of pages are parameters that you can add to grub config. Normally you leave this blank. But if your hardware required on every boot a parameter like acpi=off then you would enter it. you would see these in 
/etc/default/grub

Enter thru the first couple of screens. It should get to the last page that lets you choose where to install grub and you want the MBR or sda, not sda1 or a partition.

---

### Post by brewster-mac on 2010-12-03
Ok, have completed that and rebooted after removing the Live CD.
By the way, I didn't get the option to choose where to install grub

Now I have a screen that has a choice of bootup options ...


Chainload into GRUB 2
------------------------------------------
When you have verified GRUB 2 works, you can use this command to complete the upgrade: upgrade-from-grub-legacy
------------------------------------------
Ubuntu 9.10, kernel 2.6.31-34-fitpc2
Ubuntu 9.10, kernel 2.6.31-34-fitpc2 (recovery mode)


Use the up/down keys ....
Press enter to boot the selected OS, 'e' to edit the commands before booting, or 'c' for command-line


Really appreciate the time you are both giving to me.
What would be the next step, if thats okay?

Thanks.

---

### Post by Rubi1200 on 2010-12-03
I would prefer you wait until oldfred responds, but I think you would choose the regular option (i.e. not the recovery one).

EDIT:
take a look here:
[https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)
Go to section 4 and work your way from there.

If you have questions, please ask first.

---

### Post by oldfred on 2010-12-03
That is the grub legacy with the chainload/option to upgrade to grub2. Never actually used it as I just jumped to grub2.

I would try both the Chainload into grub2 as that is to test booting from the grub2 menu. Of if that has problems then the first kernel entry.

---

### Post by brewster-mac on 2010-12-03
I tried the 'Chainload into GRUB 2' option and it did indead load a new menu.

GRUB GRUB version 1.97^beta4
From here I chose the option - Ubuntu, Linux 2.6.31-34-fitpc2

This ran the startup sequence until it hung with the display showing ...

**init: ureadahead main process (374) terminated with status 5**

(The hard drive light is on and occasionally flickers but it still hangs)



I then rebooted and tried the menu item
Ubuntu 9.10, kernel 2.6.31-34-fitpc2

and had the same result where the startup process hung after showing the usual

'Loading essential drivers ....  ok
(etc. etc. with the last line showing)
Starting AppArmour profiles


then it clears the screen and presents the same error and hangs
**init: ureadahead main process (374) terminated with status 5**


Thanks.

---

### Post by oldfred on 2010-12-03
Some discussion says entries in fstab may cause this error. You only have your / & swap and are using label which is supposed to actually be a better way as it is more understandable.

But I might make a copy of /etc/fstab and edit it to be either UUID or drive entry.

```
Your blkid:
/dev/sda1        49239d23-e54b-49df-a518-8ff0e0f71ea1   ext3       FITPC2_FS                     
/dev/sda2        d9ac921a-31d5-4153-a5ad-0ab44c84a836   swap       FITPC2_SWAP                   

Current fstab:
LABEL=FITPC2_FS        /               ext3    errors=remount-ro 0       0
LABEL=FITPC2_SWAP    none            swap    sw              0       0

Alternative:
UUID=49239d23-e54b-49df-a518-8ff0e0f71ea1         /               ext3    errors=remount-ro 0       0
UUID=d9ac921a-31d5-4153-a5ad-0ab44c84a836    none            swap    sw              0       0

/dev/sda1         /               ext3    errors=remount-ro 0       0
/dev/sda2    none            swap    sw              0       0

```

It does show either grub or grub2 boot exactly the same way.

---

### Post by brewster-mac on 2010-12-03
Thanks. 
So I need to edit a file in the /etc/fstab directory from what it shows currently to the alternative suggested?

The file doesn't include this part ...

```
/dev/sda1        49239d23-e54b-49df-a518-8ff0e0f71ea1   ext3       FITPC2_FS                     
/dev/sda2        d9ac921a-31d5-4153-a5ad-0ab44c84a836   swap       FITPC2_SWAP 
```Dumb question: how do i change to login as 'root' when in Live Cd mode, so i can make a copy and edit the file
or does this need to be done from a terminal window?

---

### Post by oldfred on 2010-12-03
The first part was a copy of the command blkid which was run by the boot info script. It shows partitions and UUIDs which was what I used to figure out which partition was which label or which UUID.

I have used command line, but from liveCD it adds /media and not sure if anything else to path. Have not used liveCD for a while.

I often use nautilus to show path and copy and paste into a command line that I have typed cd [space] & paste entry. If new version of Nautilus that does not show path as you can copy use cntl-l (el) to change format.

Probably easier just to do this from command line, but you have to be extremely careful to only copy and edit fstab. With sudo you can do anything and that can be dangerous.

gksudo nautilus

Not sure if it asks for password on liveCD or not. There is no password on liveCD as far as I know.

---

### Post by brewster-mac on 2010-12-03
Ok did a copy of fstab, edited the original fstab and replaced the text

```
LABEL=FITPC2_FS        /               ext3    errors=remount-ro 0       0
LABEL=FITPC2_SWAP    none            swap    sw              0       0

```with
```
UUID=49239d23-e54b-49df-a518-8ff0e0f71ea1         /               ext3    errors=remount-ro 0       0
UUID=d9ac921a-31d5-4153-a5ad-0ab44c84a836    none            swap    sw              0       0


```Then rebooted after removing Live CD.

Unfortunately it has hung at the same position with ...

init: ureadahead main process (371) terminated with status 5

---

### Post by oldfred on 2010-12-03
This says a bug, but it relates more to those who have separate partitions for /var. Some fixed it with a reinstall of ureadahead.

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/542334](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/542334)

If you want we can chroot into your system, update & reinstall 

Copy this long string to chroot. I changed it to sda1.

kansasnoob's change sda1 to correct partition
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Then run these commands. Do not copy anything with a # or after a # as those are comments.

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
sudo apt-get install --reinstall ureadahead
apt-get -f install
dpkg --configure -a

---

### Post by brewster-mac on 2010-12-04
Sorry to take so long to respond. Stupidly I missed the fact the response was on the following page and when I refreshed the screen, I hadn't noticed until this mornin. Embarrassed.


So I got into chroot mode,  (root@ubuntu:/#) copied and pasted that long command and ran it. This is what reurned ...

sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
cp: ' /etc/resolv.conf' and '/mnt/etc/resolv.conf' are the same file


Again sorry for the delay

---

### Post by brewster-mac on 2010-12-04
> **brewster-mac said:**
> Sorry to take so long to respond. Stupidly I missed the fact the response was on the following page and when I refreshed the screen, I hadn't noticed until this mornin. Embarrassed.


So I got into chroot mode,  (root@ubuntu:/#) copied and pasted that long command and ran it. This is what reurned ...

sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
cp: ' /etc/resolv.conf' and '/mnt/etc/resolv.conf' are the same file


Again sorry for the delay

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp /mnt/temp/boot
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i; done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
cp: `/etc/resolv.conf' and `/mnt/etc/resolv.conf' are the same file
root@ubuntu:/# 

```

---

### Post by oldfred on 2010-12-04
You do not have a separate /boot so you should not have to create a mount and mount that separately. I think that confuses chroot.

You should just be able to copy & paste the chroot version I posted.

OR.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

---

### Post by brewster-mac on 2010-12-04
> **oldfred said:**
> You do not have a separate /boot so you should not have to create a mount and mount that separately. I think that confuses chroot.

You should just be able to copy & paste the chroot version I posted.

OR.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

I have almost completed the option ...
 
drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

where it says ...
```
Now unmount what you previously mounted:
     Code:
     umount /mnt/dev /mnt/proc /mnt/sys /mnt/usr 
umount /mnt 
Reboot, then run:
     Code:
     sudo update-grub 

```I have unmounted and rebooted.

Do I need to be in chroot to run the file
sudo update-grub ?

And when that is done, what do I do next?
Run those commands you indicated previously perhaps?

Thanks

---

### Post by oldfred on 2010-12-04
If you can reboot you then can run from the command line.
sudo update-grub

Chroot is just to get into a broken system using the kernel from the liveCD but working on the damaged system. CHange ROOT.

If you have not run all the other update commands it would be a good idea.

Also this sometime reinstalls grub better:
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by brewster-mac on 2010-12-04
> **oldfred said:**
> If you can reboot you then can run from the command line.
sudo update-grub

Chroot is just to get into a broken system using the kernel from the liveCD but working on the damaged system. CHange ROOT.

If you have not run all the other update commands it would be a good idea.

Also this sometime reinstalls grub better:
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Sorry if these questions are so basic.
So I need to run sudo update-grub from LiveCD?

---

### Post by oldfred on 2010-12-04
No, the sudo update-grub has to be run from the system, either after you have booted or within the chroot.

---

### Post by brewster-mac on 2010-12-04
> **oldfred said:**
> No, the sudo update-grub has to be run from the system, either after you have booted or within the chroot.

Ok. Went ahead and got into chroot and started running the commands you had listed after doing the sudo update-grub.

Did the #houseclean
#refresh

When I went to run the apt-get dist-upgrade, this is what I got ...
I've grabbed a snippit of the info returned at the end of the command response for apt-get upgrade, what I'm referring to is in the last few lines of this snippet.

```
Removing obsolete conffile /etc/gre.d/1.9.1.13.system.conf ...
Unpacking replacement xulrunner-1.9.1 ...
Preparing to replace mesa-utils 7.6.0-1ubuntu4 (using .../mesa-utils_7.6.0-1ubuntu4.1_i386.deb) ...
Unpacking replacement mesa-utils ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
/var/lib/dpkg/info/menu.postinst: 33: update-menus: not found
dpkg: subprocess installed post-installation script returned error exit status 127
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# apt-get dist-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@ubuntu:/# 
root@ubuntu:/# 

```

---

### Post by brewster-mac on 2010-12-04
Took a deep breath and run the suggested command displayed...

```
'sudo dpkg --configure -a'
```**Seemed to run okay until in the most part until I ran the command 'apt-get dist-upgrade **... (snippet follows)

```
 
* Starting web server apache2                                                                                                                               /usr/sbin/apache2: error while loading shared libraries: libapr-1.so.0: cannot open shared object file: No such file or directory
                                                                                                                                                      [fail]
invoke-rc.d: initscript apache2, action "start" failed.

Setting up firefox-branding (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) ...
Setting up chromium-browser-inspector (10.0.602.0~svn20101204r68270-0ubuntu1~ucd1~karmic) ...
Setting up firefox (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Please restart all running instances of firefox, or you will experience problems.

Setting up firefox-3.5 (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-3.5-branding (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) ...
Setting up chromium-codecs-ffmpeg (0.6+svn20101129r67548+68119-0ubuntu1~ucd1~karmic) ...
Setting up chromium-browser (10.0.602.0~svn20101204r68270-0ubuntu1~ucd1~karmic) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/chromium-browser because link group gnome-www-browser is broken.

Setting up firefox-gnome-support (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) ...

Setting up firefox-3.5-gnome-support (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 menu
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up menu (2.1.41ubuntu1) ...
chmod: cannot access `/usr/bin/update-menus': No such file or directory
dpkg: error processing menu (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 menu
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 
root@ubuntu:/# 

```**I went ahead and ran the next commands but it appears that there is an issue with the menu item** ...

```
root@ubuntu:/# dpkg --configure -a
Setting up menu (2.1.41ubuntu1) ...
chmod: cannot access `/usr/bin/update-menus': No such file or directory
dpkg: error processing menu (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 menu
root@ubuntu:/# 

```[B]I'll exit out and try a reboot, here's hoping.

[/B]Unfortunately same error ...
[B]init: ureadahead main process (379) terminated with status 5

[/B]

---

### Post by oldfred on 2010-12-04
I do not know why you are getting the errors, it still looks like something in your system is not quite correct. It seemed to do a lot of the process, but errors should not occur. And then your booting does not work. Some of the errors consistently relate to possibly folders not mounted.
/dev/pts not mounted?

What I can find on ureadahead errors seems to relate to invalid entries in fstab or /var in a separate partition, neither of which I can see in your case.

---

### Post by brewster-mac on 2010-12-05
> **oldfred said:**
> I do not know why you are getting the errors, it still looks like something in your system is not quite correct. It seemed to do a lot of the process, but errors should not occur. And then your booting does not work. Some of the errors consistently relate to possibly folders not mounted.
/dev/pts not mounted?

What I can find on ureadahead errors seems to relate to invalid entries in fstab or /var in a separate partition, neither of which I can see in your case.

So should I mount /dev/pts when the others are mounted and try the process again from chroot?

Do you think I need to reformat my hard drive?

---

### Post by oldfred on 2010-12-06
It would not hurt to also mount /dev/pts, but I do not know if that is the problem or not.

Do you have good backups. If not use liveCD to copy /home and any other data you may want. Perhaps the voltage spike caused too many errors to fix. Reinstall can be pretty quick if drive is still ok.

---

### Post by brewster-mac on 2010-12-06
Thanks Oldfred, I'll work on that.
Thanks again for all your help, I'll let you know how I go.

Would there be a problem deleting the file:  **/etc/apparmor.d/usr.sbin.ntpd**
It has been suggested that I delete this file and if its ok and I guess I have nothing to lose?

I used           sudo rm -i /etc/apparmor.d/usr.sbin.ntpd    but returns  - No such file or directory


[B]AppArmor parser error in /etc/apparmor.d/usr.sbin.ntpd at line 1: Found unexpected character: ''
Failure: AppArmor profiles failed to load
Done.
init: ureadahead main process (387) terminated with status 5
[32.694416] EXT3 FS on sda1, internal journal[/B]

---

### Post by brewster-mac on 2010-12-08
After some more changes

[http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04](http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04)

although I am on version 9.10 I tried it[FONT=monospace]
[/FONT]sudo mv /etc/init/ureadahead.conf /etc/init/ureadahead.conf.disable

I rebooted and it hung again with just a flashing cursor so I restarted in recovery mode and then I had this
Error: Unable to resolve host[U]
after a while[U] it ran some load up files and finished at a prompt to login

[/U][/U]

 I logged in as root but now I don't know what command to use to bring up the GUI
 Do you know what it is?
 Thanks.

---

### Post by oldfred on 2010-12-08
It used to be just startx, but now I see other recommendations.

startx
or 
now preferred:
sudo service gdm start
sudo /etc/init.d/gdm restart
sudo start gdm

Back in post #31 was a set of commands to rerun & update. You may want to also run them again, if you are in system. Each line will require sudo if not from a chroot enviroment where sudo not required.

---


---
title: "recovery mode only entries in grub"
date: 2009-12-19
forum: General Help
---

### Post by booah on 2009-12-19
Hello Everyone,

When I boot up grub only contains Memory test and Memory test serial console without including my Ubuntu and Windows entries. 
What I believe may have caused this problem was installing my mobile broadband when I had to install libusb and usb_switchmode. After getting it working eventually I thought it better to clean up the bad versions (non 64bit etc) by using packet manager(i have no connection apart from mobile broadband so was downloading files from windows and then rebooting and installing them in ubuntu) I selected the appropiate packets I wanted. With libusb I noticed a more recent version to the one I am using so I marked the old one for removal and the later one for installation. 
When i rebooted my machine I came across this problem. Any help would be greatly appreciated as I've been trying to fix it for hours. Sorry for the long winded post too.

regards,
Booah

---

### Post by utnubuuser on 2009-12-19
You might have to boot from grub command-line.

> [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

--Check: rescue - about halfway down the page.

 - when you're in you can update grub

---

### Post by booah on 2009-12-19
> **utnubuuser said:**
> You might have to boot from grub command-line.



--Check: rescue - about halfway down the page.

 - when you're in you can update grub

Thanks for the fast reply utnubuuser!
Unfortunatley I cant get into ubuntu, it says "no kernel specified". I can get into windows buts thats it. I really dont know what to do now, if I could get in I could just fix grub.

---

### Post by Puck7 on 2009-12-19
You could try to boot from the Live CD.

Here are the details how to reinstall from the Live CD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Leppie on 2009-12-19
> **booah said:**
> Unfortunatley I cant get into ubuntu, it says "no kernel specified". I can get into windows buts thats it.

seems like you do get into grub, have you tried pressing "c" when the grub menu appears? this will take you to the grub shell.

---

### Post by booah on 2009-12-19
> **Leppie said:**
> seems like you do get into grub, have you tried pressing "c" when the grub menu appears? this will take you to the grub shell.

yes Leppie, I can get into grub. This is what has worked:

root=(hda0,3)   #windows partition
chainloader +1
boot

this gets me into windows, i tried the same with  the other entries from 'ls' but nothing worked. when I type 'find' it says its an unknown command.

at the minute Im trying the install from live CD, sorry for the newbieness of this question but which is the linux filesystem i am supposed to install it on:
/dev/sda4   57999   60801   22515097+   5   Extended
/dev/sda5   57999   60801   21535101    82   Linux

I assumed it is sda5?

very much appreciate the help so far guys :)

---

### Post by Leppie on 2009-12-19
> **booah said:**
> yes Leppie, I can get into grub. This is what has worked:

root=(hda0,3)   #windows partition
chainloader +1
boot

this gets me into windows, i tried the same with  the other entries from 'ls' but nothing worked. when I type 'find' it says its an unknown command.

at the minute Im trying the install from live CD, sorry for the newbieness of this question but which is the linux filesystem i am supposed to install it on:
/dev/sda4   57999   60801   22515097+   5   Extended
/dev/sda5   57999   60801   21535101    82   Linux

I assumed it is sda5?

very much appreciate the help so far guys :)

most probably you can boot into your ubuntu system from the grub shell:
```
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro		
initrd /initrd.img		
boot
```

---

### Post by booah on 2009-12-19
> **Leppie said:**
> most probably you can boot into your ubuntu system from the grub shell:
```
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro        
initrd /initrd.img        
boot
```

cheers Leppie,
the first line goes in good but when I do the second it says "error: file not found"
i tried it without the 'ro' too but same problem

---

### Post by Leppie on 2009-12-19
> **booah said:**
> cheers Leppie,
the first line goes in good but when I do the second it says "error: file not found"
i tried it without the 'ro' too but same problem

do you have a seperate /boot partition? you may need to change the /dev/sda5 to match your /boot partition.

otherwise, using the livecd please provide the output of "sudo fdisk -l"

---

### Post by booah on 2009-12-19
> **Leppie said:**
> do you have a seperate /boot partition? you may need to change the /dev/sda5 to match your /boot partition.

otherwise, using the livecd please provide the output of "sudo fdisk -l"

really appreciate this help Leppie.

I set windows7 as the default os in grub.
here is the output:

  ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b9914f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    6  FAT16
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1918       57998   450467636    7  HPFS/NTFS
/dev/sda4           57999       60801    22515097+   5  Extended
/dev/sda5           57999       60679    21535101   83  Linux
/dev/sda6           60680       60801      979933+  82  Linux swap / Solaris

Disk /dev/sdb: 7969 MB, 7969177600 bytes
246 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15252 * 512 = 7809024 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       51019      125862   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(51018, 151, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(125861, 218, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       11061      137997   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(11060, 38, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(137996, 44, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      122600      249536   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(122599, 24, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(249535, 29, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      189201      189204       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(189200, 44, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(189203, 201, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by Leppie on 2009-12-19
from the livecd, can you still access /dev/sda5? what's the contents of /boot?

---

### Post by booah on 2009-12-19
> **Leppie said:**
> from the livecd, can you still access /dev/sda5? what's the contents of /boot?

i can mount to it yes with "sudo mount /dev/sda5 /mnt"

the contents of boot are grub (dir) and memtest86+.bin
grub contains 146 files.

---

### Post by Leppie on 2009-12-19
> **booah said:**
> i can mount to it yes with "sudo mount /dev/sda5 /mnt"

the contents of boot are grub (dir) and memtest86+.bin
grub contains 146 files.

could you post the contents of /boot/grub/device.map?

---

### Post by booah on 2009-12-19
> **Leppie said:**
> could you post the contents of /boot/grub/device.map?

this is the only entry :

(hd0)      /dev/sda

---

### Post by Leppie on 2009-12-19
> **booah said:**
> this is the only entry :

(hd0)      /dev/sda

that's how it should be.
now try the following (thanks to ranch hand for posting his template):
```
sudo mkdir /mnt/Daily-root
sudo mount /dev/sda5 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev
sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf
sudo chroot /mnt/Daily-root /bin/bash
```
this will make your actual system make the root when booting off the live cd.
then do perform the following to repair grub:
```
update-grub
grub-install --recheck /dev/sda
```

---

### Post by booah on 2009-12-19
> **Leppie said:**
> that's how it should be.
now try the following (thanks to ranch hand for posting his template):
```
sudo mkdir /mnt/Daily-root
sudo mount /dev/sda5 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev
sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
**sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf**
sudo chroot /mnt/Daily-root /bin/bash
```this will make your actual system make the root when booting off the live cd.
then do perform the following to repair grub:
```
update-grub
grub-install --recheck /dev/sda
```

**sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf**

got an error here :
cp: cannot stat `/etc/resolv.conf': no such file or directory

argh i thought we were onto a winner :)

---

### Post by booah on 2009-12-20
hey guys,
i get this warning/error when I try to reinstall grub. Any ideas where to go with it? :(
thanks

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda5
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
ubuntu@ubuntu:~$

---

### Post by Leppie on 2009-12-20
because /dev/sda5 is your linux partition and not the master boot record.

the error you got with the resolv.conf, the file isn't something you would require that badly if only re-installing grub to the mbr. it's only there in case grub needs to be re-installed using apt.

try again like this:
```
$sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by booah on 2009-12-20
> **Leppie said:**
> because /dev/sda5 is your linux partition and not the master boot record.

the error you got with the resolv.conf isn't something you would require that badly if only re-installing. it's only there in case grub needs to be re-installed using apt.

thanks again Leppie for the fast reply.
What would you suggest I do to get my grub up and running again? the post you made but omit the .conf file line?

---

### Post by Leppie on 2009-12-20
or continue with the last thing you were trying.
it should be a bit quicker, just use sda instead of sda5

---

### Post by booah on 2009-12-20
> **Leppie said:**
> or continue with the last thing you were trying.
it should be a bit quicker, just use sda instead of sda5

by using blocklists? to be honest I'm not too sure what i'm doing. I've only been using ubuntu for about a month and I love it but dont know too much about it.
is there a command to force install that line?


edit : oh sorry I see your suggestion of sda over sda5, brillaint gonna try now :)

---

### Post by Leppie on 2009-12-20
don't forget to mount the partition first (if you rebooted) ;)

---

### Post by booah on 2009-12-20
> **Leppie said:**
> don't forget to mount the partition first (if you rebooted) ;)
great, that seemed to work. Thanks leppie.I got the following :

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
ubuntu@ubuntu:~$ 


If i run update grub will that add the ubuntu and windows entries in the grub display?

edit: i dont trust myself to try it without your opinion :)

---

### Post by booah on 2009-12-20
i just tried "sudo update-grub" and it gave me an error :/
something about cannot find /           i think
gonna restart now and see if anything is different

edit : nothing different only 2 grub entries -
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

dont have a clue what to do to be honest, i got so much important college work on ubuntu i cant reinstall it and I only have a mobile broadband connection i will never get it all updated :/

---

### Post by booah on 2009-12-20
> **Leppie said:**
> that's how it should be.
now try the following (thanks to ranch hand for posting his template):
```
sudo mkdir /mnt/Daily-root
sudo mount /dev/sda5 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev
sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf
sudo chroot /mnt/Daily-root /bin/bash
```this will make your actual system make the root when booting off the live cd.
then do perform the following to repair grub:
```
update-grub
grub-install --recheck /dev/sda
```

I tried this again and left out the resolve.conf copy and the rest of it worked great. the only problem is that it didnt recognise ubuntu and only added windows to the boot list. I think when i stupidly 'marked for complete removal' libusb (i tried to update it with a more recent one in package manager) it must of removed some important files.
Any ideas what to do now heh? :P

---

### Post by spect8 on 2009-12-20
I've tried all that, but when I try to use the chroot sudo chroot /mnt/name /bin/bash, it comes with this error: chroot: cannot run command '/bin/bash': Exec format error.

I've searched for a long time after a solution, can't seem to find one =(

---

### Post by Leppie on 2009-12-20
> **booah said:**
> I tried this again and left out the resolve.conf copy and the rest of it worked great. the only problem is that it didnt recognise ubuntu and only added windows to the boot list. I think when i stupidly 'marked for complete removal' libusb (i tried to update it with a more recent one in package manager) it must of removed some important files.
Any ideas what to do now heh? :P

Check that you have the latest kernel installed, I am using kernel 2.6.31-16. You could use synaptic for this. Once installed you need to run update-grub again.

---

### Post by Leppie on 2009-12-20
> **spect8 said:**
> I've tried all that, but when I try to use the chroot sudo chroot /mnt/name /bin/bash, it comes with this error: chroot: cannot run command '/bin/bash': Exec format error.

I've searched for a long time after a solution, can't seem to find one =(

after booting off a livecd try the following:
```
sudo mount /dev/sdaY /mnt  ##replace sdaY with the partition you installed ubuntu
sudo grub-install --root-directory=/mnt /dev/sda
```

if this is not working you need to provide more info.

---

### Post by spect8 on 2009-12-20
Can I update that through the live cd? If so, how?

---

### Post by Leppie on 2009-12-20
> **spect8 said:**
> Can I update that through the live cd? If so, how?

you have to issue these commands in a terminal:
```
sudo mount /dev/sdaY /mnt  ##replace sdaY with the partition you installed ubuntu
sudo grub-install --root-directory=/mnt /dev/sda
```

but you have to know on which partition you installed ubuntu. if you don't know where you installed it, please post the output of the command "sudo fdisk -l"

---

### Post by spect8 on 2009-12-20
It says:

grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

---

### Post by Leppie on 2009-12-20
> **spect8 said:**
> It says:

grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

there is a difference between the reference in the first line and the one in the second line. the one in the first line is a reference to your linux partition. the one in the second line is a reference to the mbr of your harddrive. this is why the reference in the first line ends in **sda_Y_** (this should be your linux partition) and the one in the second line ends in **sda** (this is the harddrive you're installing grub to).
```
sudo mount /dev/**sda_Y_** /mnt  ##replace sdaY with the partition you installed ubuntu
sudo grub-install --root-directory=/mnt /dev/**sda**
```

---

### Post by spect8 on 2009-12-20
Okay that worked, thought the Y was a spelling mistake =)


Now it boots up, this time only in Grub command line.
Before I had the grub menu, the ubuntu distro just didn't work after the update.

Any idea where I go from here?

---

### Post by Leppie on 2009-12-20
do the following:
```
sudo mount /dev/**sda_Y_** /mnt
sudo grub-install --root-directory=/mnt/ /dev/**sda**
```

if you want you can do "update-grub" as well, to see if everything is picking up as it should.

---

### Post by spect8 on 2009-12-20
Yeah I already did that.

Now it boots up in:

GNU GRUB version 1.97~~ beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.

sh:grub>

---

### Post by Leppie on 2009-12-20
boot using the livecd, then issue this command:
```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.41/boot_info_script041.sh/download' \
&& chmod 755 boot_info_script041.sh \
&& sudo ./boot_info_script041.sh
```

and post the output

---

### Post by spect8 on 2009-12-20
--2009-12-20 23:28:46--  [http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.41/boot_info_script041.sh/download](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.41/boot_info_script041.sh/download)
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/0.41/boot_info_script041.sh?use_mirror=sunet](http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/0.41/boot_info_script041.sh?use_mirror=sunet) [following]
--2009-12-20 23:28:46--  [http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/0.41/boot_info_script041.sh?use_mirror=sunet](http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/0.41/boot_info_script041.sh?use_mirror=sunet)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://sunet.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.41/boot_info_script041.sh](http://sunet.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.41/boot_info_script041.sh) [following]
--2009-12-20 23:28:46--  [http://sunet.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.41/boot_info_script041.sh](http://sunet.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.41/boot_info_script041.sh)
Resolving sunet.dl.sourceforge.net... 194.71.11.73
Connecting to sunet.dl.sourceforge.net|194.71.11.73|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 57404 (56K) [application/x-sh]
Saving to: `boot_info_script041.sh'

100%[=====================================================================================>] 57.404      --.-K/s   in 0,1s    

2009-12-20 23:28:47 (531 KB/s) - `boot_info_script041.sh' saved [57404/57404]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda3 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop

---

### Post by Leppie on 2009-12-20
> **spect8 said:**
> Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop

could you also post the just created RESULTS.txt?

---

### Post by spect8 on 2009-12-20
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub.

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

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009454f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,920,159    81,920,097   7 HPFS/NTFS
/dev/sda2         152,376,525   156,296,384     3,919,860   5 Extended
/dev/sda5         152,392,590   156,296,384     3,903,795  82 Linux swap / Solaris
/dev/sda3          81,931,500   152,376,524    70,445,025  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="E450037C500354A8" TYPE="ntfs" 
/dev/sda3: UUID="31cbb738-4f17-431f-8f3f-c600c53bd944" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="b58ce9cf-a4ea-4d2f-a323-d4b003c32a9e" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda3/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=31cbb738-4f17-431f-8f3f-c600c53bd944 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=31cbb738-4f17-431f-8f3f-c600c53bd944 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=31cbb738-4f17-431f-8f3f-c600c53bd944 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=31cbb738-4f17-431f-8f3f-c600c53bd944 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=31cbb738-4f17-431f-8f3f-c600c53bd944 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=31cbb738-4f17-431f-8f3f-c600c53bd944 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b58ce9cf-a4ea-4d2f-a323-d4b003c32a9e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  41.9GB: boot/grub/menu.lst
  41.9GB: boot/grub/stage2
  41.9GB: boot/initrd.img-2.6.24-19-generic
  41.9GB: boot/initrd.img-2.6.24-19-generic.bak
  41.9GB: boot/initrd.img-2.6.31-16-generic
  41.9GB: boot/vmlinuz-2.6.24-19-generic
  41.9GB: boot/vmlinuz-2.6.31-16-generic
  41.9GB: initrd.img
  41.9GB: vmlinuz

---

### Post by Leppie on 2009-12-21
from the grub prompt, issue these commands to boot into ubuntu:
```
set root=(hd0,3)
linux /vmlinuz root=/dev/sda3 ro        
initrd /initrd.img        
boot
```

once logged on, issue the following commands:
```
$sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.old
$sudo update-grub
```

---

### Post by spect8 on 2009-12-21
I got that far yesterday, and the end result is, that it goes into black screen when I select the top linux in the grub menu =(

Its like its the wrong kernel and initrd that the grub menu has.

Its:

Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.24-19-generic
Ubuntu, Linux 2.6.24-19-generic (recovery mode)

They are all in /boot, bot the files I used, and as you said, I loaded in grub command, are in the root?

---

### Post by Leppie on 2009-12-21
> **spect8 said:**
> I got that far yesterday, and the end result is, that it goes into black screen when I select the top linux in the grub menu =(

Its like its the wrong kernel and initrd that the grub menu has.

Its:

Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.24-19-generic
Ubuntu, Linux 2.6.24-19-generic (recovery mode)

They are all in /boot, bot the files I used, and as you said, I loaded in grub command, are in the root?

if you have not renamed menu.lst to menu.lst.old (as I suggested in my previous post), you are still using the grub legacy boot menu configuration file (menu.lst) with grub 2 (grub2 uses grub.cfg instead of menu.lst) installed on your system. partition enumeration has changed, so grub2 will never be able to find the correct linux partition with your current setup.
please, also verify that grub legacy has been removed from your system.

---

### Post by rossruther on 2009-12-21
Very informative stuff..

---

### Post by spect8 on 2009-12-22
I did do as you said, and it runs with Grub2 now, I tried editing in the grub.cfg, so I now starts up. But its not a good solution, and will for sure crash with next update.

I added this to the grub.cfg

menuentry "Ubuntu, 9.10" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,3)
        linux   /vmlinuz root=/dev/sda3 ro
        initrd  /initrd.img
}

So how do I fix it so grub2, will find the correct kernel and initrd?

---

### Post by Leppie on 2009-12-24
if you have been able to boot normally into ubuntu with this menu entry, you can regenerate the grub.cfg:
```
$sudo grub-mkconfig
```
this command will show you the grub.cfg as it's being generated. check that the ubuntu entries are there.

---

### Post by spect8 on 2009-12-25
I looks the same with the exact same entries that I had put in it.
So I guess this is it, Ubuntu can't make it right.
I like Ubuntu for programming, but when it comes to upgrades, its even more buggy than Windows. Thank god that I don't use it for more personnal stuff.

Thx for the help, even though it didn't fix it entirely. I guess the only thing to do, if I wan't it as it should be, would be to re-install the whole shi*.

Many people don't like Microsoft, especially in here, but when it comes to upgrades an OS, the people behind Ubuntu could sure learn some from MS.

---

### Post by Leppie on 2009-12-25
you could try removing all grub packages (as I stated previously, it looks like something from grub legacy is stuck on your system) completely (including configuration files):
```
$sudo apt-get purge grub grub-pc grub-common
```

then re-install grub2:
```
$sudo apt-get install grub-pc grub-common
```
this will re-install grub2 and regenerate the necessary files (debconf will come up with a couple of questions).


i don't entirely agree with you on the ms upgrades, there very often are quite some limititations for upgrades (for example if there's been several releases your os, you need the latest otherwise you have to do a clean install).

---

### Post by spect8 on 2009-12-25
You don't give up.. I like that =)

I did the 2 lines, and its the same output as before.

Sætter grub-pc (1.97~beta4-1ubuntu4.1) op...

Creating config file /etc/default/grub with new version
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.24-19-generic
Found initrd image: /boot/initrd.img-2.6.24-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP (loader) on /dev/sda1
done

Again, the wrong kernels and images, so black screen when trying to boot.

---

### Post by Leppie on 2009-12-25
> **spect8 said:**
> You don't give up.. I like that =)
men created the computer, so it will be hard for a computer to become smarter than men (as we do not know how to create things  that will not have our limitations ;)).

> **spect8 said:**
> Again, the wrong kernels and images, so black screen when trying to boot.
which kernels do you have installed? it's not the kernels you listed?

---

### Post by spect8 on 2009-12-25
Possible me who got the wrong idea of what the kernel is. I thought it was the one loaded when: linux /linus..... was loaded.

I'm not that into how the whole Ubuntu works, as you might have guessed by now =)

---


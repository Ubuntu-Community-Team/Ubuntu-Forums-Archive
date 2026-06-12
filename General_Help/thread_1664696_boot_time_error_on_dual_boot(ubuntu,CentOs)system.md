---
title: "boot time error on dual boot(ubuntu,CentOs)system"
date: 2011-01-11
forum: General Help
---

### Post by amite on 2011-01-11
Yesterday i had to install ubuntu10.10 and Centos5.5 on my friend's system.First i installed centos without installing grub.I suppose centos use grub legacy.then i installed ubuntu.After installing ubuntu i boot system and run these command from
[COLOR=DarkRed]$sudo grub-install /dev/sda
$sudo update-grub[/COLOR]

After that when i opened [COLOR=DarkRed]/boot/grub/grub.cfg[/COLOR] and found the following lines....

> 
###BEGIN /etc/grub.d/30_os-prober ###
menuentry "CentOS release 5.5 (Final) (on /dev/sda)" {
           insmod part msdos
           insmod ext2
           set root='(hdo,msdos1)'
           search --no-floppy --fs-uuid --set .......#uuid here
           linux /boot/vmlinuz-2.6.18.194.el5xen root=/dev/sda1            
}
###END  /etc/grub.d/30_os-prober ###


here is the result of [COLOR=DarkRed]$sudo fdisk -l[/COLOR]
> 
Device          Boot       Start         End              Blocks              Id          System
/dev/sda1        *              1                                                    83         Linux
/dev/sda2                                                                              82    Linux swap/Solaris
/dev/sda3                                                                                5         Extended
/dev/sda4                                                                               83        Linux



Now when i try to boot Centos following error occurs....
[COLOR=DarkRed]error : Invalid Magic Number

/dev/sda2 is swap partition which is shared by both ubuntu and centos.
[COLOR=Black]I need guidance where i am making mistake and what i can do now ?[/COLOR]
[/COLOR]

---

### Post by amite on 2011-01-11
any solution ???

---

### Post by amite on 2011-01-12
i didn't my solution here also....any1 please ...
[http://ubuntuforums.org/showthread.php?t=1305252](http://ubuntuforums.org/showthread.php?t=1305252)
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---


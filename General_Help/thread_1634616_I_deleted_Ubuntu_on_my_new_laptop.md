---
title: "I deleted Ubuntu on my new laptop"
date: 2010-11-30
forum: General Help
---

### Post by crackpotfox on 2010-11-30
Hello,
On my new laptop, i installed ubuntu. i decided to not use it anymore, so I deleted the ubuntu partition with gparted.
when i rebooted to go to windows to expand the windows partition, it said grub rescue

thanks for your help

---

### Post by overdrank on 2010-11-30
My apologies for moving as I did not see the request for support.:confused:

---

### Post by wilee-nilee on 2010-11-30
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

Hmm no mention of the actual MD distro personally I have to see the script and a identification of said MS distro.;)

---

### Post by ivarn on 2010-11-30
If your windows version is 7 and if you have the dvd, the dvd should help you with the bootloader. just boot up the cd and click where it says repair (or something).
The repair button (as far as I can remember) is at the bottom of the screen in the left corner when you boot up the cd and the menu window pops up.

---

### Post by crackpotfox on 2010-11-30
alrighty, i tried the boot script on ubuntu10.04 live cd, and it says file not found

---

### Post by wilee-nilee on 2010-11-30
> **crackpotfox said:**
> alrighty, i tried the boot script on ubuntu10.04 live cd, and it says file not found

Look at the instructions closer just drag that bootscript down load to the desktop and copy and paste this command from the link to the terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by crackpotfox on 2010-11-30
i dragged to desktop, then ran the commands:



ubuntu@ubuntu:~$ sudo bash boot_info_script055.sh
bash: boot_info_script055.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script*.sh
bash: /home/ubuntu/desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script055.sh
bash: /home/ubuntu/desktop/boot_info_script055.sh: No such file or directory
ubuntu@ubuntu:~$

---

### Post by wilee-nilee on 2010-11-30
> **crackpotfox said:**
> i dragged to desktop, then ran the commands:



ubuntu@ubuntu:~$ sudo bash boot_info_script055.sh
bash: boot_info_script055.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script*.sh
bash: /home/ubuntu/desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script055.sh
bash: /home/ubuntu/desktop/boot_info_script055.sh: No such file or directory
ubuntu@ubuntu:~$

Your typing the commands and and making a mistake in every one. Copy and paste the one I posted, it is the exact same as the one on the link. This is not rocket science man.;)

Your not reading the posts either would you identify the MS distro, and say just for fun tell us if you have a install or recovery disc, do you see where I'm going, it is called full disclosure if you want actual help that will get you up and running.

---

### Post by crackpotfox on 2010-11-30
it worked. i was stupid!!!!!!!!!!!!!! here it is


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

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

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   467,554,303   467,144,704   7 HPFS/NTFS
/dev/sda3         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B0F8CF62F8CF2606                       ntfs       SYSTEM                        
/dev/sda2        FA1217701217315D                       ntfs                                     
/dev/sda3        2625-2F63                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by crackpotfox on 2010-11-30
by the way, i have A windows 7 install disc, so i could so the repair thing, but it did not come with the computer. thee was no cd with the computer. HP didnt give one. i am running windows 7, though. I am not trying to keep secrets though ;)

---

### Post by wilee-nilee on 2010-11-30
Stupid heh its always nice to have a new member welcome aboard.;)

Okay download this recovery cd and boot it per the instructions, or use a W7 install DVD. Notice the W7 http link to recognize getting to the recovery command line.

I see W7 looked like Vista you can use the W7 DVD or this link for a recovery cd.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Just run the highlighted command to restore the MS bootloader and you should be set.

---

### Post by crackpotfox on 2010-11-30
Will Do!!!!!


Tomorrow:)

---

### Post by wilee-nilee on 2010-11-30
> **crackpotfox said:**
> Will Do!!!!!


Tomorrow:)

Like totally tubular man, let us know if there is a problem.

---

### Post by crackpotfox on 2010-12-01
OMG!
I used the link you provided for the instructions and it frigging worked.

THANK YOU SOOOOOO MUCH!!!!!!!!!

But really, thank you

---

### Post by lisati on 2010-12-01
I defer to the advice already given for getting your machine usable again, and wish to offer the following suggestion: once you are satisfied that Windows is working again, you might want to look for and use any software installed on it that will let you make a set of recovery disks for your machine.

---

### Post by Slim Odds on 2010-12-01
> **lisati said:**
> I defer to the advice already given for getting your machine usable again, and wish to offer the following suggestion: once you are satisfied that Windows is working again, you might want to look for and use any software installed on it that will let you make a set of recovery disks for your machine.

+5

This should be one of the first things that you do!!!

---


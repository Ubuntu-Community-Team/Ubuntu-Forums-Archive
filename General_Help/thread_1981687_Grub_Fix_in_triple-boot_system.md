---
title: "Grub Fix in triple-boot system"
date: 2012-05-17
forum: General Help
---

### Post by drofart on 2012-05-17
Greeting Folks, Great Face Lift !

 So to the point, I have a triple boot system, earlier have windows & ubuntu 11.04 & few days before got precise. Now I want to remove precise but have a bitter experience in past about grub. So i wish if  some one could help me out here.

Result.txt is somthing like this
```


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 104848825. But according to the info from 
                       fdisk, sda5 starts at sector 209712567.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   104,863,274   104,863,212   7 NTFS / exFAT / HPFS
/dev/sda2         104,863,742   934,506,495   829,642,754   f W95 Extended (LBA)
/dev/sda5         209,712,567   251,658,224    41,945,658   7 NTFS / exFAT / HPFS
/dev/sda6         251,658,290   641,732,489   390,074,200   7 NTFS / exFAT / HPFS
/dev/sda7         641,732,556   934,506,495   292,773,940   7 NTFS / exFAT / HPFS
/dev/sda8         104,863,744   205,590,527   100,726,784  83 Linux
/dev/sda9         205,592,576   209,711,103     4,118,528  82 Linux swap / Solaris
/dev/sda3         934,506,496   976,769,023    42,262,528  83 Linux

```Thanks in advance,
Dr Mrinal

---

### Post by satish_j on 2012-05-17
can you specify which all OS are included in triple boot,you said windows & 12.04 and then precise.
If you are not aware, 12.04 == precise

[EDIT]:-okay,so the list provided by you mentions 3rd OS as 11.04.So,if you want to remove Precise.As long as you are not fiddling with the windows,it should not cause any issues with grub.
From which OS(11.04 or 12.04)is the grub.cfg file read at boot?

---

### Post by drofart on 2012-05-17
Sorry for mistake. that's 11.04.

---

### Post by drofart on 2012-05-17
> **satish_j said:**
> 
From which OS(11.04 or 12.04)is the grub.cfg file read at boot?
How to know that ?

---

### Post by satish_j on 2012-05-18
> **drofart said:**
> How to know that ?

Never mind,grub.cfg will be read from the latest distro you installed.
But,as i said earlier,you should not have any problems with removing any distro.
You can post a new thread in case any issue faced..

---

### Post by wilee-nilee on 2012-05-18
In the Ubuntu you want to keep, run these commands to give that version grub control, it does matter which one has the control othrwise you will be reinstalling grub to the mbr to get into the one kept. Chances are precise has the control since installed last.

```
sudo grub-install /dev/sda
```then

```
sudo update-grub
```Now this Ubuntu has the control and the other can be removed safely.

Also in the future post all of the results.txt

---

### Post by kiftox on 2012-10-06
if anybody can help me with this issue..I've also got a triple boot environment with windws **xp** sp3, Mac OS X **Leopard 10.5.7** and **ubuntu** 12.04 (and a fat32 partition for data). The computer is a netbook, an old **msi wind u1oo** clone.

  Everything has been working well since a few days ago. I had ubuntu   11.10 installed (next to XP and Leopard), and I used the same partition   to install ubuntu 12.04 (I didnt updated, I made a fresh new install).   After that the GRUB seems to be OK (like always before) but when the   system boots into Leopard (I dont need to log in manually, it was   configured for autologin) I can only see a light blue screen ... in the   screen of my netbook.

  I dont know if there is something wrong with the VGA drivers, or  **perhaps GRUB2 has not "copied" the right monitor  boot options to the  new ubuntu 12.04**  install or something like that, but it's a bit weird,  and it's a  problem I've never had before.  Before installing ubuntu 12.04, OS X was  running OK in this computer, but now I only can see this blue screen,  and i can only imagine a **GRUB2 **related issue if last time I used OS X everything was OK:

[IMG]http://imageshack.us/a/img26/2869/windosxerror.jpg[/IMG]


  I'd like to think it's not something really serious, because   everything seems OK until the end of the boot process, when the lght   blue screen appears.

  If anybody can point me in the right direction...

**PD:** I can "feel" leopard behind that bluescreen,(some buttons  still work) that's why I've also pointed to a VGA drivers related issue,  but I still cant understand which is the relation between updating  ubuntu and a malfunction in OS X graphic drivers.
PD: Here is the part of my grub2 of mac os x 10.5.7 32bits (there's another for 64bits,but it's the same): Perhaps the problem is in this grub2 config:

    menuentry "Mac OS X (32-bit) (on /dev/sda3)" --class osx --class darwin --class os {
    insmod part_msdos
    insmod hfsplus
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 4a05c02442c0186f
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 4a05c02442c0186f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}

---


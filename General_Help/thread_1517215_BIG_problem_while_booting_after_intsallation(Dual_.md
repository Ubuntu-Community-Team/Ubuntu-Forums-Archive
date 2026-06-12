---
title: "BIG problem while booting after intsallation(Dual booting with Vista)"
date: 2010-06-24
forum: General Help
---

### Post by silentrock on 2010-06-24
Hello guys,im really new to this partition, OS installing and ubunt stuff.
Yesterday i decided to install ubuntu in my PC,i downloaded the .ISO image and i  installed it in my USB.
After trying it and all that i observed that i really liked it and i decided to formally install it to my computer in the hard drive.

When i reached the partition thing,i selected to dual boot with Vista and select between each them in every startup,when i clicked FORWARD it gave me an error which i did not read(because,again im a noob) so i clicked cancel.

Today i wanted to go through the process again and now really install it,so again i went to the time zone part and i clicked forward but then,instead of taking me straight to the partition phase,it appeard a window saying "The installer has detected that the following disks have mounted partitions: /dev/sda ...." 
I clicked yes,to unmount this partitions so it took me to the partition thing,once there i selected the option to install Ubuntu with Vista and select between them i neach startup,then i clicked forward and went to the username/computer name process,once i finished i continued to the next part,the installation,but i selected to import all of my WIndows VIsta default user data,after that i clicked forward and went to the installation process,i went down stairs to eat soemthing while it finishes,i came back and it was finished,it asked me to reboot so i clicked in Restart Now.



When it tried to boot,appeared an error saying:
Error: no such devide found: ####################
Grub load(or something like that)
grub rescue:


and it was a command line,since there i havent been able to boot into vista or Ubuntu,im really scared because is the first thing related to OS installing ive done,so i booted my USB and ran the trial and right now im trying to find out what to do from that trial version.
I just went to the INSTALL UBUNTU 10.04 LTS application under the System>Administration Menu and found out that in the partition phase the Install and allow to select between both systems in eahc startup option,i dont know what to do,i foudn out that my HD has still all its data(MUsic/Videos/Folders/Programs/ect.)its just that i cannot boot from it.

Also in GParted it appears as /dev/sda1/ and a warning icon besides it,also when i go into information, thers this warning there [http://yfrog.com/evselection006p](http://yfrog.com/evselection006p)


I dont know what to do and the other peopel that uses this computer are going to kill me if i dont repair this,thank you.

---

### Post by silentrock on 2010-06-24
BUMP.

dont get forgotten thread.

---

### Post by oldfred on 2010-06-24
What you did was fine for XP but for Vista & 7 they are more sensitive to size changes. It is better but not required to use the Windows tools to resize Vista & 7. At the very least even when you use the windows tools the system wants to run chkdsk on reboot, so I am sure that is the minimum you need to do to get windows working. Grub will only boot working windows.

The grub rescue says something is not quite right. You can often manually boot and then update once you have booted to keep Ubuntu working.

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

Express Boot to the Most Recent Kernel
 Command Summary where X is drive & Y is partition shown by ls :
      ls
      set root=(hdX,Y)
      linux /boot/vmlinuz root=/dev/sdxY ro
      initrd /boot/initrd
      boot

---

### Post by silentrock on 2010-06-24
Excuse my UBER ignorance,and thanks for replying and taking the time to help this huge noob.

but.am i exactly supposed to do?

---

### Post by silentrock on 2010-06-24
COuld you tell me exactly what am i supossed to do?

i tried the GRUP 2 installation but i get some errors trying to install them in every device 

and also what am i supossed to do with those codes?

THanks and sorry.

---

### Post by oldfred on 2010-06-25
At the grub rescue command type ls and it should find the partition(s) with bootable installs. Then type in the rest of the commands replacing X drive and Y partition with the drive & partition found by the ls command or try all if more than one.

---

### Post by silentrock on 2010-06-25
Ok so i typed ls and it returned me:

(hd0) (hd0,3) (hd1) (hd1,1)

then i typed set root=(hd1,1) 

and it returned nothing so i typed:

linux /boot/vmlinuz 

it returned me :

Unknown Command " LInux" 


Some questions:



1st: in the set root command,what partition should i choose?

2nd:is it normal that it doesnt returns me nothing in the set root command?

3rd: im supposed to write the following command like that? ```
linux /boot/vmlinuz/ root= /dev/sdxy ro
```  

cause it appears as unknown command

4rd:do i have to write the commands separated or in one line?


thanks and please excuse me.

---

### Post by oldfred on 2010-06-25
Do you know if your install is in sda3 hd0,3 or sdb1 hd1,1?

You have to type each line. Where it has sdxy you replace X with either 0 or 1 and Y with 3 or 3 depending on which you are using so it will be the first if you used set root=(hd0,3), second if set root=(hd1,1)

linux /boot/vmlinuz/ root=/dev/sda3 ro
linux /boot/vmlinuz/ root=/dev/sdb1 ro

Do not add spaces or change capitalization.

---

### Post by silentrock on 2010-06-25
Vista is in sda1 and Vista loader is in sda3 

It seems that Vista is occupying 390 GB from HD and loader the other 10


i don't see Ubuntu anywhere from the Install 10.04 LTS menu.

---

### Post by silentrock on 2010-06-25
also i have two U S B flash drives in the PC 

one is the one i am booting Ubuntu trial version from

and the second one is just empty

the first one represents hd1 hd0,1 and hd1,1

as the second one represents hd2 hd2,1 and hd2,2

i guess i should ignore them and just focus in hd0 hd0,3

and i still get the linux command as unknown

---

### Post by oldfred on 2010-06-25
run this, so we know what is where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by silentrock on 2010-06-25
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   763,469,279   763,469,217   7 HPFS/NTFS
/dev/sda3         763,469,280   781,416,719    17,947,440   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,818,047     7,817,985   b W95 FAT32


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 4009 MB, 4009754624 bytes
5 heads, 32 sectors/track, 48947 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *          8,064     7,831,551     7,823,488   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        84E6F91AE6F90CE4                       ntfs       HP                            
/dev/sda3        2C88743C8874071C                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5378-9756                              vfat       Felipe                        
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        461C-5663                              vfat       UBUNTU                        
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdg1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)




there are my results,i dont seem to find Ubuntu anywhere,maybe its because the option i selected during installation couldt be processed due to Vista and its loader(sda3) using all of sda space.

---

### Post by oldfred on 2010-06-25
I do not see either Ubuntu nor your actual windows install. 

You have 2 partitions with windows boot loaders but neither have the 
  /Windows/System32/winload.exe executable????

Did you overwrite a windows partition?

You do not have any linux partitions which would be ext3 or ext4?

---

### Post by silentrock on 2010-06-25
so what you suggest me to do?
 
install again Ubuntu?

---

### Post by silentrock on 2010-06-25
things arent looking good for my computer right?

---

### Post by oldfred on 2010-06-25
First do you still have your full windows partition? You should repair it first if it is still there. If not and you want windows you need to reinstall.
With Vista & 7 you should use the windows tools to shrink the windows partition.

And then yes you need to reinstall Ubuntu and use the largest free space available option to use the space you made by shrinking Vista.

---

### Post by silentrock on 2010-06-26
well i still see Vista in sda1 from the installation menu and,i guess,that FACTORY_IMAGE is sda3

My comp didnt come with a vista installation disc neither with a recovery one,its just a partition called Factory_Image
also my CD/DVD reader isnt working for some reason.

do the recovery disc will help me to repair Vista without loosing data or itll just return it to factory status?

also

is it possible to burn an ISO to an usb flash drive and boot from that USB as the vista recovery disc?

THanks

---

### Post by oldfred on 2010-06-26
Most factory images are just that. They erase everything and restore the computer to exactly as it was the day you purchased it.

Most iso can be put on USB, not sure of the procedure for  a windows iso. 

Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by silentrock on 2010-06-26
well i backed up my important files but i jsut hate to go back to factory status cause its so outdated,and with UNETBooting i can just install OS's into USBs but i cant burn any ISO to it right?

THanks.

---


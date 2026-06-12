---
title: "mounting drive : message inconvenience"
date: 2010-09-18
forum: General Help
---

### Post by thomaskprakash on 2010-09-18
hi all,
  
     I have a multi boot system with xp,vista,windows7 and ubuntu 10.04 installed. 

     My Disk has 4 windows partitions of which three were NTFS and one was FAT 32. The FAT 32 drive was not detected in Ubuntu. So i reformated it in windows and made it too NTFS. After that, when i rebooted the system into Ubuntu, there was a message which read :

'Continue to wait : or Press S to skip or M for manual recovery' 

     Only the 'Skip' option worked and i am able to boot into Ubuntu. My newly formatted drive is mounted by ubuntu and i can store files there.


my /etc/fstab entries are :

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=4bf730bc-dd2b-49e0-a7a2-dc6514f251e0 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda12 during installation
UUID=d29f6fde-11fd-414a-a352-9d15a9cb2f3f /home           ext3    defaults        0       2
# /usr was on /dev/sda11 during installation
UUID=feab58ce-1f95-4f00-b0c8-e01e885d9337 /usr            ext3    defaults        0       2
# /var was on /dev/sda9 during installation
UUID=a0144c26-1839-43ab-8f78-32cb3c33a1c5 /var            ext3    defaults        0       2
# /windows was on /dev/sda14 during installation
UUID=607E-C94B  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda13 during installation
UUID=e2e87fb6-fef2-4ee5-8a80-94bb984a1be5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


  How can i get rid of the annoying message during startup ?


thomas k prakash

---


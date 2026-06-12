---
title: "Please help"
date: 2010-03-26
forum: General Help
---

### Post by jmr423 on 2010-03-26
Solved it, Lvm partition manager failed. 

Hello, so i spent about hours setting up ubuntu 9.10 server. I installed it using [http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3) i followed every step in it took me a few tries and i had to reformat it a few times until i finished the last step. Im not sure i  formatted the lvm partition properly. I finnaly got to the last step of the guide and was able to log into ISPConfig 3 i looked through it and changed the password. I was using the ssh-putty for alot of it.

I then restarted my server and i get this error.



```
/ect/apparmor/functions: line 40: /sbin/apparmor_parder: No such file or directory


fsck from util-linux-ng 2.16


/dev/mapper/server1-root: clean, 68709/200800 files, 385733/801792 blocks (check in 5 mounts)


[ 11.138192] ACPI: I/O resource nForce2_smbus [0X5000-0x503f] conflicts with ACPI region SMRG [0X5000-0x5004]


[ 11.138245] nForce2_smbus 0000:00:01.1:error probing SMB1.


One or more of the mounts listed in /ect/fstab cannout yet be mounted:


(ESC for recovery shell)


/boot:waiting for UUID=9ea34148-31b7-4d5c-baee-c2e2022562ea


* stopping NTP server ntpd
    ...done.


* starting NTP server ntpd
    ...done.


mountall: Cancelled


init: mountall main process (397) terminated with status 1


general error mounting filesystems.


A mainenance shell will now be started.


Control-d will terminate this shell and re-try.


Give root password for maintenance


(or type control-D to continue)


```i tried running these commands in the recovery shell,


```
/etc/init.d/apparmor stop
  
update-rc.d -f apparmor remove

aptitude remove apparmor apparmor-utils
```And 



```
aptitude install ntp ntpdate
```But it did not fix anything.




This is what the fstab looks like


```
# /ect/fstab: static file system information


#


# Use 'blkid -o value -s UUID' to print the universally unique identifier


# for a device; this may be used with UUID= ad a more robust way to name


# devices that works even if disks are added and removed. See fstab(5).


#


# <file system> <mount point> <type> <options> <dump> <pass>


     proc               /proc               proc     defaults     0            0


/dev/mapper/server1-root /   ect4     errors=remount-ro,usrjquota=aqota=aquota.user,grpjquota=aquota.group,jqftm=vsfv0 0              


# /boot was on /dev/sda5 during installation


UUID=9ea34148-31b7-4d5c-baee-c2e2022562eaboot      /boot     ext2     defaults     s     0     2


/dev/mapper/server1-swap_1     none     swap     sw     0     0


/dec/scd0     /media/cdrom0     udf,iso9660 user,noauto,exec,utf8     0     0


/dev/fd0      /media/floppy0     auto     rw,user,noauto,exec,utf8     0     0



```NOTE I TYPED ALL OF THIS OUT BY HAND SO SOME OF IT MIGHT BE A BIT OFF.

I am using a 4 gig hard drive on a pc with 1 gig of ram i can give you more info if you need it. 

how do i fix this?



Ps. my isp blocks ports 21,25,80,110,6667,135-139,443,445,1433,1434 although i dont think that has anything to do with this problem.

---

### Post by UCSBGauchosRock on 2010-03-26
Something MAY be wrong with your harddrive but it may also be corrupt data or something not installing correctly. My reccommendation in this case is to first try to boot from CD-drive and attempt installation again... and if that does NOT work, make a new liveCD with the Ubuntu Server Edition and try it with the nw CD

Oh and make SURE that before you select anything in the configuration dialogs to know exactly what you are doing and double and triple check it before continuing. Configuring a server can be tricky...

---

### Post by jmr423 on 2010-03-26
> **UCSBGauchosRock said:**
> Something MAY be wrong with your harddrive but it may also be corrupt data or something not installing correctly. My reccommendation in this case is to first try to boot from CD-drive and attempt installation again... and if that does NOT work, make a new liveCD with the Ubuntu Server Edition and try it with the new CD

Oh and make SURE that before you select anything in the configuration dialogs to know exactly what you are doing and double and triple check it before continuing. Configuring a server can be tricky...

I didnt really want to have to reinstall the server but if thats what i have to do i guess ill do it :(. Do you have any other sugestions? i followed the guide step by step that is linked to the top of the page step by step. Do you know of any good guides i can follow if i do end up having to reinstall it? 

I'm trying to host a site off it and my isp blocks a bunch of ports.

---

### Post by UCSBGauchosRock on 2010-03-26
Here is a guide that may help, but it is a little on the long side...



[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by jmr423 on 2010-03-26
> **UCSBGauchosRock said:**
> Here is a guide that may help, but it is a little on the long side...



[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)


hmmm, i was trying to install 9.10, can i use this guide for 9.1 or are there alot of differences?

---

### Post by UCSBGauchosRock on 2010-03-26
I'm very sorry I gave you the wrong link. Here is 9.10:

[https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)

Again my apologies. Jeez I can't believe I didn't notice :(

---

### Post by jmr423 on 2010-03-26
alright thanks i guess il read through that. Are there any more logs i can post to help you help me solve this?


Edit: Wow i was just looking through it and i have alot of reading to do.


Solved it, Lvm partition manager failed.

---


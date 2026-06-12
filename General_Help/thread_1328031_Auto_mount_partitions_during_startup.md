---
title: "Auto mount partitions during startup"
date: 2009-11-16
forum: General Help
---

### Post by ashokmkd on 2009-11-16
When i install ubuntu, i used to specify the mount points of each partition in the installation.. When i installed karmic, i forgot to do this and now i have to mount the partitions in each log-in. How can i set it to mount automatically during startup?

---

### Post by JBAlaska on 2009-11-16
Are you talking about NTFS partitions? If so this is new specific to Karmic...You can add the partition info to fstab manually or install ```
sudo apt-get install ntfs-config
``` and running it from System, Administration, NTFS configuration tool (with your wanted partitions UNMOUNTED) and click on the enable checkbox.

---

### Post by ashokmkd on 2009-11-16
Thanks, but i needed to do it manually.. Partitions are NTFS. Can u just tell me what to add in fstab?

---

### Post by Chikitulfo on 2009-11-16
What would be the fstab line for a NTFS partition (/dev/sda6) to be mounted in /media/DATA?
I tried this line but it doesn't seem to work
```
/dev/sda6 "/media/DATA" ntfs defaults 0 0
```

BTW the folder /media/DATA already exists.

---

### Post by JBAlaska on 2009-11-16
[quote="ashokmkd"]Thanks, but i needed to do it manually.. Partitions are NTFS. Can u just tell me what to add in fstab?[/quote]

Welll fair enough I guess.. Enter this in a term:
```
sudo fdisk -l
```

Find your NTFS partition(s) and enter a line in fstab:
```
gksudo gedit /etc/fstab
```
[COLOR="Red"]One of mine for EXAMPLE only:[/COLOR]
```
/dev/sdc1 /media/Storage_Drive_1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

---

### Post by aquavitae on 2009-11-16
> **Chikitulfo said:**
> What would be the fstab line for a NTFS partition (/dev/sda6) to be mounted in /media/DATA?
I tried this line but it doesn't seem to work
```
/dev/sda6 "/media/DATA" ntfs defaults 0 0
```

BTW the folder /media/DATA already exists.

It should be ntfs-3g, not ntfs.  Also, you don't need the quotations around /media/DATA, and you might need to add a few options to allow non-root users to access the drive.  I use uid=1000, setting my user as the owner.

---

### Post by dcstar on 2009-11-16
> **ashokmkd said:**
> Thanks, but i needed to do it manually.. Partitions are NTFS. Can u just tell me what to add in fstab?

Install the **pysdm** package and use the GUI:

[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

---

### Post by ashokmkd on 2009-11-16
I tried many options and at last found it.. I added the following line to fstab

/dev/sda5      /media/disk1     ntfs     loop     0     1

It seems working perfect, i dont know the meaning of loop, 0 and 1 yet.. :-)

---

### Post by Chikitulfo on 2009-11-16
I thought that just ntfs instead of ntfs-3g worked since hardy or so...

---

### Post by ashokmkd on 2009-11-16
Thanks people, but can anyone tell me the use of "loop" option? And   the 0 and 1 used for dump and pass?

---

### Post by aquavitae on 2009-11-16
> **ashokmkd said:**
> Thanks people, but can anyone tell me the use of "loop" option? And   the 0 and 1 used for dump and pass?
Not entirely sure sure about dump and pass - I remember the man page once making sense to me, but I've forgotten it now. loop means that its using a loopback device - i.e. a device that actually points to a file on your system.  Typically it would be used if you're mounting an iso image.  I'm not sure why you need it in this situation though.

---

### Post by ashokmkd on 2009-11-16
> **aquavitae said:**
> Not entirely sure sure about dump and pass - I remember the man page once making sense to me, but I've forgotten it now. loop means that its using a loopback device - i.e. a device that actually points to a file on your system.  Typically it would be used if you're mounting an iso image.  I'm not sure why you need it in this situation though.

Thanks for the information. I am almost unfamiliar with linux, but very enthusiastic about it.. I am learning each and every bit of info now.. Thats the reason for asking such questions. Hope the forum will be a great support for me..

---

### Post by oldfred on 2009-11-16
from man fstab and man mount 

The fifth field, (fs_freq),  is  used  for  these  filesystems  by  the
       dump(8)  command  to determine which filesystems need to be dumped.  If
       the fifth field is not present, a value of zero is  returned  and  dump
       will assume that the filesystem does not need to be dumped.

       The  sixth field, (fs_passno), is used by the fsck(8) program to deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       root  filesystem  should  be specified with a fs_passno of 1, and other
       filesystems should have a fs_passno of 2.  Filesystems within  a  drive
       will  be checked sequentially, but filesystems on different drives will
       be checked at the same time to utilize  parallelism  available  in  the
       hardware.   If  the sixth field is not present or zero, a value of zero
       is returned and fsck will assume that the filesystem does not  need  to
       be checked.

---

### Post by ashokmkd on 2009-11-16
That was really helpful. Thanks.. I have learned fstab in detail using man. I didn't know about these manuals. Now its so easy refering them..

---


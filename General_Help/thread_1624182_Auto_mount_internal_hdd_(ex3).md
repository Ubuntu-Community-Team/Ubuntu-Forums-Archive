---
title: "Auto mount internal hdd (ex3) ?"
date: 2010-11-17
forum: General Help
---

### Post by xperiax10 on 2010-11-17
Hello im currently useing kubunt 10.10 and i need help to have this drive automounted at boot
for all users.

/dev/sda1               1       14590   117185536   83  Linux
UUID: 32dc7bba-7605-4543-ab73-d8cbb16c0f76

i have tested diffrent options but non work.
before i could use psydm but that was for a ntfs drive for ext3 it dont work aswell.
i find kubuntu @ ubuntu very userfriendly but when it comes to this part its not that good
for users like me that not are so experienced with linux
so if some one can help me on this it would be great.
----------------------------------------------------------------------
current fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=55f9c112-e0cf-40d2-b3cf-37ad0f955702  /              ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=9e9cbb09-8202-4616-a5cf-5f87ca22a4cf  none           swap         users                       0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0

---

### Post by Morbius1 on 2010-11-17
If I read your post correctly this partition is formatted in ext3?

First: Make a mount point for the partition to live in ( this is just an example ):
```
sudo mkdir /media/Data
```Then add a line to fstab that looks like this:
```
UUID=32dc7bba-7605-4543-ab73-d8cbb16c0f76 /media/Data ext3 defaults 0 2
```After you add the line and save fstab, run the following command to test for errors and mount the new partition:
```
sudo mount -a 
```If this is an existing partition then you should be good to go but if this is a newly created and formatted partition then you will have to modify ownership / permissions after the mount.

---

### Post by xperiax10 on 2010-11-17
Yes its a new partion formated to ext3 i had to set permisons probably
not did it the right way used sudo dolphin and changed owner ship of the created folder in media
thanks for the help :)

---


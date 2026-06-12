---
title: "Username and Password for Ubuntu 12.04"
date: 2012-08-27
forum: General Help
---

### Post by feeliks83 on 2012-08-27
I created a Multiboot USB stick within Ubuntu 12.04 but when I enter the destop I get asked for an user and password..
Tried many combinations none worked P:

ubuntu-12.04-desktop-amd64.iso
The file I used

combinations I tried

Blank - Blank
ubtuntu - ubuntu
ubuntu - blank
root - root
root - toor
admin - admin
admin ubuntu
.. and many more..don´t know right know ^^

When I remember right there wasn´t a password request the last time I used Ubuntu but I´m not sure because of I installed it to my hdd(not sure if I testet the liveUSB)

thanks in advance

---

### Post by spiky001 on 2012-08-27
Hi  Did you leave the login blank enter nothing and let it time out?

---

### Post by Cheesemill on 2012-08-27
Check your ISO file.

Every time I've come accross a situation where the Live CD is asking for a username and password it's been because of a corrupt download.

(The correct username is ubuntu with a blank password).

---

### Post by feeliks83 on 2012-08-29
> Hi  Did you leave the login blank enter nothing and let it time out?     Yes I did..tried many combinations ^^

> Check your ISO file.

Every time I've come accross a situation where the Live CD is asking for  a username and password it's been because of a corrupt download.

(The correct username is ubuntu with a blank password).     Ok I´ll try it to download the iso again
The User: ubuntu pass: blank I tried..so it seems like the download was corrupt :)



um, well..I downloaded the new version 12.04.1 but again the user: ubuntu and password: blank doesn´t work P:

Edit2

I checked now the md5 of the iso from 12.04(because the md5 of 12.04.1 I didn´t found on the site [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes))
and they are similar..um, well..what now? :D

Edit3

I solved it..
I created a multiusb stick
in the root of the stick was the .disc directory of clonezilla not ubuntu..I deleted and copied the ubuntu .disk directory and it did work..without a password prompt :)
now I have to look if clonezilla is working ..I guess not xD

---

### Post by feeliks83 on 2012-08-29
both are working now :))
what I need to fix is now trinity rescue disc..it´s the last who doesn´t boot till the end :) 

Tryiing to find TRK on your 1 CD-drive(s)
TRK not founs on CD, checking harddisks and USB sticks ...
cat: /etc/trkhd: No such file or directory
Seems we didn't find anything yet. Trying CD-drives once more
Trying to find TRK on your CD-drive(s)
Seems we didn't find the TRK medium
Manually enter the device on which TRK can be found (e.g. sda1):

any ideas? *cough* hehe ^^

---

### Post by feeliks83 on 2012-08-29
Trinity REscue Disc is working now too :)
I solved it by creating another partition on the USB stick
first partition NTFS second FAT32
Extracted the whole .ISO on the partition
and boot it with this grub4dos entry

title Trinity Rescue Disc \Mapped and Booted from Partition sdb2
map (hd0,1)+1 (fd0)
map --hook
root (fd0)
chainloader +1
boot I renamed the stick to TRK_3-4 (what didn´t work on the first partition) 					 					

Maybe someone have a tough time with it like me and this helps him [IMG]http://www.wincert.net/forum/public/style_emoticons/default/wink.png[/IMG]

---


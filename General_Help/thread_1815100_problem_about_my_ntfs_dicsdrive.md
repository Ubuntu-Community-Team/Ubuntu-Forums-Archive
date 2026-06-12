---
title: "problem about my ntfs dicsdrive"
date: 2011-07-30
forum: General Help
---

### Post by prozac38 on 2011-07-30
hello 

i used long time win7 and i want to change operation system than installed ubuntu 11.04. (last one)
when i using win7 i got 2 harddrive, first one is my system harddisk, second one is my own photo,movie harddisk which format is NTFS.

i take out the second HDD before ubuntu is installing.
after ubuntu installitation, i take it back my pc and its working (when pc is starting starting screen writes both of hdd s)
but i cant see second hdd when ubuntu s running.

i am pretty new ubuntu user, what will i do to see second HDD documents.

thank you

---

### Post by snoopo71 on 2011-07-30
Hi, if you open gparted, can you see all the hdd?

---

### Post by prozac38 on 2011-07-30
> **snoopo71 said:**
> Hi, if you open gparted, can you see all the hdd?

i installed gparped and see all hdds right now, 
but how can i do second hdd is avalible for %0 lose ?

---

### Post by galvatron408 on 2011-07-30
run "sudo fdisk -l"

look to see where your windows disk is. Let's just say that it is /dev/sdb1
then, you would do something like this...

sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/sdb1 /mnt/windows

then.... ls -l /mnt/windows

---

### Post by cjack2964 on 2011-07-30
Ok, so it is never I good idea to unplug a hard drive before you install ubuntu, but you may just not have the right program available, ubuntu only reads ext2,3,4 drive, so you need a package called ntfs-3g from the software center, or alternatively, this command in terminal

sudo apt-get install ntfs-3g

Open the program once it down,lads and it is pretty straightforward, then you should see the drive mounted on the desktop. 

:) also, if you wish to play all your newly found media I would recommend vlc media player, have a nice day

---

### Post by prozac38 on 2011-07-31
thank you so much for responces
i reinstall ubuntu with 2 hdd drive than got no problem :)

---


---
title: "cannot access ntfs partition after 10.04 upgrade"
date: 2010-04-30
forum: General Help
---

### Post by antel on 2010-04-30
I have a partition on my hard drive that i use for documents. In 9.10 i would just click on places, and then on the partition name. It would ask for my password and i would be able to access the files. I just upgraded to 10.04 and first off i do not see the partition at all. I navigated to filesystem>media and found my partition but i has a gray X on it. I did gksu nautilus and when i access the folder, there is nothing inside. any help is greatly appreciated. thank you

---

### Post by GSF1200S on 2010-04-30
> **antel said:**
> I have a partition on my hard drive that i use for documents. In 9.10 i would just click on places, and then on the partition name. It would ask for my password and i would be able to access the files. I just upgraded to 10.04 and first off i do not see the partition at all. I navigated to filesystem>media and found my partition but i has a gray X on it. I did gksu nautilus and when i access the folder, there is nothing inside. any help is greatly appreciated. thank you

Is the NTFS partition encrypted? I ask because I dont enter a password to enter my NTFS partition, so Im unfamiliar with what you mean by that. Along with the answer to that question, please post the results of:
```
sudo fdisk -l
```
so I can help you.

---

### Post by antel on 2010-04-30
> **GSF1200S said:**
> Is the NTFS partition encrypted? I ask because I dont enter a password to enter my NTFS partition, so Im unfamiliar with what you mean by that. Along with the answer to that question, please post the results of:
```
sudo fdisk -l
```so I can help you.


It's not encrypted. i created it from windows and access it without a password there. But whenever i mounted something on 9.10 it always asked me for my system password.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       54482   437626633+   7  HPFS/NTFS
/dev/sda2           54483       60801    50757367+   f  W95 Ext'd (LBA)
/dev/sda5           54483       60801    50757336    7  HPFS/NTFS

---

### Post by GSF1200S on 2010-04-30
> **antel said:**
> It's not encrypted. i created it from windows and access it without a password there. But whenever i mounted something on 9.10 it always asked me for my system password.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       54482   437626633+   7  HPFS/NTFS
/dev/sda2           54483       60801    50757367+   f  W95 Ext'd (LBA)
/dev/sda5           54483       60801    50757336    7  HPFS/NTFS

To others who may read this thread: If anyone knows something about installing Ubuntu on NTFS partitions, please throw me a link or something- as far as I knew Ubuntu should be installed on a Linux filesystem and this is the second person ive seen who seems to have linux installed in NTFS. I need to learn more about this so I can help others (EXT4 for me though thank you)

To the OP: Im going to assume your windows partition is /dev/sda1 and your linux partition is /dev/sda5. Try:
```
mkdir ~/Desktop/windows
sudo mount /dev/sda1 ~/Desktop/windows
```
and then open the folder on your desktop and see if your windows files are there. **If not**, or it tells you its already mounted, then try to do the following command:
```
sudo mount /dev/sda1 ~/Desktop/windows
```
and once again check that folder. If one of these ways reveals your windows files, get back to me here and we'll add it to your /etc/fstab so it will be available on boot.

---

### Post by antel on 2010-04-30
> **GSF1200S said:**
> To others who may read this thread: If anyone knows something about installing Ubuntu on NTFS partitions, please throw me a link or something- as far as I knew Ubuntu should be installed on a Linux filesystem and this is the second person ive seen who seems to have linux installed in NTFS. I need to learn more about this so I can help others (EXT4 for me though thank you)

To the OP: Im going to assume your windows partition is /dev/sda1 and your linux partition is /dev/sda5. Try:
```
mkdir ~/Desktop/windows
sudo mount /dev/sda1 ~/Desktop/windows
```and then open the folder on your desktop and see if your windows files are there. **If not**, or it tells you its already mounted, then try to do the following command:
```
sudo mount /dev/sda1 ~/Desktop/windows
```and once again check that folder. If one of these ways reveals your windows files, get back to me here and we'll add it to your /etc/fstab so it will be available on boot.
 
Still nothing. i just logged into windows and accessed that partition without a problem. Is there a way to undo the upgrade and downgrade back to 9.10? cause that partition is extremely important and another thing is, 10.04 is actually much slower for me than 9.10 for both booting and starting programs

---

### Post by GSF1200S on 2010-04-30
> **antel said:**
> Still nothing. i just logged into windows and accessed that partition without a problem. Is there a way to undo the upgrade and downgrade back to 9.10? cause that partition is extremely important and another thing is, 10.04 is actually much slower for me than 9.10 for both booting and starting programs

Some of that might be a driver issue pertaining to your display drivers (the slowness). What do you mean by still nothing? Did you go to the folder I had you create? Did the terminal spit out anything that might help us? At least you have a working computer.

Unfortunately, you cannot downgrade- youd have to reinstall Ubuntu 9.10. But, it shouldnt be any slower- I have 9.10 and 10.04 installed, and they are both virtually the same (very fast). Unless gnome has gotten considerably slower since 9.10 was released, I doubt that your problem is just "10.04 is slower" rather than "10.04 is slower because something isnt working"

---

### Post by antel on 2010-04-30
> **GSF1200S said:**
> Some of that might be a driver issue pertaining to your display drivers (the slowness). What do you mean by still nothing? Did you go to the folder I had you create? Did the terminal spit out anything that might help us? At least you have a working computer.

Unfortunately, you cannot downgrade- youd have to reinstall Ubuntu 9.10. But, it shouldnt be any slower- I have 9.10 and 10.04 installed, and they are both virtually the same (very fast). Unless gnome has gotten considerably slower since 9.10 was released, I doubt that your problem is just "10.04 is slower" rather than "10.04 is slower because something isnt working"

The folder had my windows files "host." i am looking for the partition i made. The terminal had nothing at all. Everything was created and mounted without an issue but the created folder contains the "host" contents. I still cant find my document partition. 

The time it takes from powering up to login is the same at 9.10 but after i login in it takes a considerable about of time loading (no icons or panels, just the background image) before i see my panel or icon. Not a  big deal but the only reason i upgrade was to login faster than before.

---

### Post by antel on 2010-04-30
ok i fixed it. you told me to mount sda-1 the partiton was supposed to be sda5. anyway, now its mounted on my desktop but how to i keep it there?

also, how do i delete the other folder we made with the sda1 files in it?

---


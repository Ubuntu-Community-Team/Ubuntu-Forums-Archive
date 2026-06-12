---
title: "Partition creation help"
date: 2010-11-05
forum: General Help
---

### Post by kanishkdudeja on 2010-11-05
Im using ubuntu 10.10 and during installation i chose the option "erase the whole disk and den install"..now i hav 2 partitions sda1 and sda2..sda1 is the default primary boot partition and sda2 is extended..when i tried to clone sda1 through clonezilla it said u will hav to unmount sda1 first..so i thot il hav to make another partition and den unmount sda1 and then will clone an image of sda1 to be saved into the new partition..so now i want to create a new partition without losing all my data..im attaching an image of the gparted screen in case u want to hav a look at my partitions..please tell me how can i create a new partition without losing all my data.

---

### Post by Verbeck on 2010-11-05
sda1 is where ubuntu is installed so whenever you boot ubuntu, sda1 is mounted.

try using gparted from the live cd to resize it (back up critical data first)

---

### Post by kanishkdudeja on 2010-11-05
The option for resizing is not highlighted when i click on sda1.

---

### Post by Quackers on 2010-11-05
In Gparted click on the little arrow to the left of /dev/sda2 please and post another screenshot.
Also are you using Clonezilla Live?

---

### Post by kanishkdudeja on 2010-11-05
yes in using clonezilla live..im attaching the screenshot.

---

### Post by Quackers on 2010-11-05
Thanks. You can't resize sda1 while Ubuntu is booted up. You would need to resize it with GParted Live cd or with the Ubuntu Live cd.

---

### Post by kanishkdudeja on 2010-11-05
How do i do it ? And will all my data be lost ?

---

### Post by Quackers on 2010-11-05
As long as the partition is not mounted there is usually no problem. But, having said that, partition changing does bear a small risk and any important data should be backed up! Always!
If you boot from the Ubuntu Live CD and choose "Try Ubuntu" you can then use Gparted to do what you want. My advice would be to do only one thing at a time. ie resize the partition first. Let that run, then create another partition as a separate task. Gparted can get a bit mixed up if you ask it to do 2 or 3 things at once.

---

### Post by kanishkdudeja on 2010-11-05
okay..thanks a lot..:)

---

### Post by CharlesA on 2010-11-05
> **kanishkdudeja said:**
> How do i do it ? And will all my data be lost ?

Do not mess with partitions without backing yer data up first.

If something goes wrong, you could lose all your data.

---

### Post by kanishkdudeja on 2010-11-05
Yeah il backup all my data..only then il try and resize it..!

---

### Post by Quackers on 2010-11-05
That's good practice :-)

---

### Post by kanishkdudeja on 2010-11-07
ive resized the partition using the ubuntu live cd..and then created a new partition in the new space..but i cnt copy any new files into the new partition..when i right click on it and see the permissions..it says only the root can change permissions and u are not the owner..

ive attached the screenshot..

---

### Post by kanishkdudeja on 2010-11-07
please help soomebody.

---

### Post by Verbeck on 2010-11-07
did you set the drive to auto mount? run the following from a terminal and post the output here

```
cat /etc/fstab
```

---

### Post by kanishkdudeja on 2010-11-07
i dont know. Ive attached the screenshot.

---

### Post by Verbeck on 2010-11-07
doesn't look like it. post the output of **mount**. it should give info on how the device is mounted.(make sure it IS already mounted)

---

### Post by kanishkdudeja on 2010-11-07
attached the output of mount

---

### Post by Verbeck on 2010-11-07
it is rewritable.. try mounting it manually and see whether you can write again

sudo umount /dev/sda3
sudo mkdir /media/storage
sudo mount /dev/sda3 /media/storage

---

### Post by kanishkdudeja on 2010-11-07
no i still cant do it..

isnt there any command like chmod -r 777..

which can make the drive accessible..

i used such a command to make a folder only accessible to root to me as well..

---

### Post by Verbeck on 2010-11-07
you can try sudo chown -R username:usergroup /media/mountpoint to change the permissions for the mount point. but i doubt it would have any effect on the read/write permissions of the drive..

another thing you could do : if the partition doesnt contain anything, try formating it from system>administration>disk utily. check the 'take ownership of the file system'

or someone else might have a solution, so i'd suggest to wait for a little while

---

### Post by kanishkdudeja on 2010-11-07
yeah thnx a lot..its working..

but it doesnt seem to be the correct way..i mean were forcefully taking its ownership..

shouldnt it have happened automatically ?

---

### Post by kanishkdudeja on 2010-11-07
i wrote

sudo chown -R kanishk:kanishk /media/storage

---

### Post by kanishkdudeja on 2010-11-07
i formatted it using the disk utility and checked the option "take ownership of file system"..its working fine now..but now i want to delete storage folder in media..but when i unmount storage it shows the attached screenshot..

---

### Post by Verbeck on 2010-11-07
try restarting the computer. after that, before mounting anything, delete the storage folder

---

### Post by kanishkdudeja on 2010-11-07
yeah it got deleted..:)..thanks

---


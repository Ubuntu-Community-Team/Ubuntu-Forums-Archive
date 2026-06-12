---
title: "How to copy files from Ubuntu hard drive with Live CD?"
date: 2011-03-14
forum: General Help
---

### Post by SirGonzo420 on 2011-03-14
OK, so I'm mostly a linux-idiot but I tried to get an update for a laptop that was running xubuntu. Anyway, it won't boot and instead takes me to a screen where it says "press s to skip mounting, or press m to recover manually" or something like that.

I've pressed S, and then it tells me that it can't find /tmp or something, and I have to turn it off and back on to do anything. Pressing M doesn't help much either... at least not for a mostly-linux-idiot like me.,

I would do a clean install, but there are a few files I absolutely have to have from the hard drive.

Can someone help me recover the files I need from my hard drive to a usb drive while using a Live CD?

---

### Post by oldfred on 2011-03-14
Welcome to the forums.

I think it is saying you have a drive issue. It may not mount anyway from liveCD. But run this to see if it will repair it.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by SirGonzo420 on 2011-03-14
> **oldfred said:**
> Welcome to the forums.

I think it is saying you have a drive issue. It may not mount anyway from liveCD. But run this to see if it will repair it.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

Thanks for the welcome!

Please forgive my density; 

I'm not sure what is meant by "swap off if necessary, change sdb1 to your partition(s)"...

---

### Post by sandman88 on 2011-03-14
I believe by "swap off" he is saying that if it still does not work to turn off the swap partition.

---

### Post by pqwoerituytrueiwoq on 2011-03-14
go into gparted on the cd 
right click the swap partition (if it exist)
click swapoff in the menu
and swap is off

---

### Post by AlanR8 on 2011-03-14
I REALLY don't think this needs to be complicated! Yes a single terminal command will be needed but after that all can be handled with a mouse and a few clicks.

Boot with the live CD and select the option to "Try" Ubuntu to get to the live CD desktop. Find "Terminal" in the menu under accessories and type/copy the following command:

> mount -a

That's done with the terminal!

Go to Nautilus, your file manager, under the places menu, and you'll find the computer's hard disk(s) have been mounted and are accessible. Now plug a memory stick in and copy your essential files.

Job done...simples

---

### Post by SirGonzo420 on 2011-03-14
> **AlanR8 said:**
> I REALLY don't think this needs to be complicated! Yes a single terminal command will be needed but after that all can be handled with a mouse and a few clicks.

Boot with the live CD and select the option to "Try" Ubuntu to get to the live CD desktop. Find "Terminal" in the menu under accessories and type/copy the following command:



That's done with the terminal!

Go to Nautilus, your file manager, under the places menu, and you'll find the computer's hard disk(s) have been mounted and are accessible. Now plug a memory stick in and copy your essential files.

Job done...simples

I tried that, but when I tried the "mount -a" command it said:

"mount: only root can do that"

So I tried "sudo mount -a", and it just went back to "ubuntu@ubuntu:~$".

---

### Post by SirGonzo420 on 2011-03-14
Somehow I was able to mount the hard drive, but some of the files I need have an 'X' on them, and I am unable to move them to my USB drive...

Any idea how I might be able to change permissions or something so I can move all the files I need before reinstalling Ubuntu?

---

### Post by ajgreeny on 2011-03-14
Start nautilus as root with ```
gksu nautilus
``` in terminal and you wil be able to read and write and copy and even delete files as you wish. If they are THEN copied to a fat32 USB drive they will lose all linux permissions, so will no longer suffer with this problem.

PS: The ```
mount -a
``` comand from a live CD would not have helped as it only mounts partitions listed in /etc/fstab.  The live CD fstab would not have  listed your hard disk partitions, so would not have done anything at all.

---

### Post by SirGonzo420 on 2011-03-14
> **ajgreeny said:**
> Start nautilus as root with ```
gksu nautilus
``` in terminal and you wil be able to read and write and copy and even delete files as you wish. If they are THEN copied to a fat32 USB drive they will lose all linux permissions, so will no longer suffer with this problem.

PS: The ```
mount -a
``` comand from a live CD would not have helped as it only mounts partitions listed in /etc/fstab.  The live CD fstab would not have  listed your hard disk partitions, so would not have done anything at all.

I tried "gksu nautilus" and it returned the "ubuntu@ubuntu:~$" thing (please forgive my ignorance), so I tried > mv /mnt/home/myname/Desktop/'My File.pdf' /media/ILOGICIt returned:

> mv: cannot open '/mnt/home/myname/Desktop/My File.pdf' for reading: Permission denied 

Any idea how I can "get permission" to access my own file? lol

---

### Post by ajgreeny on 2011-03-15
Sorry, I have just noticed you're using xubuntu, and if your live CD is also xubuntu, that command will need to be ```
gksudo thunar
```to get the root file manager.  With that open you should be able to copy your files as needed.

Apologies for confusion!

---

### Post by 741Baus on 2011-03-15
To transfer files for back up , I recently hosed my system and needed to get my documents to my backup hard drive , I couldn't do it, permission problems ,even using ```
gksudo nautilus
``` 
I found a solution using a live cd also you must have and internet connection .

Transferring files using live cd with a working internet. 
open terminal

```
sudo apt-get install hfsplus libhfsp0 
```

```
gksudo nautilus(or thunar if using Xbuntu)
```

hope this helps as it worked for me.

---


---
title: "Change drive permission"
date: 2012-06-13
forum: General Help
---

### Post by bill-lancaster on 2012-06-13
I have a second hard drive which I re formatted then created a single partition.

I find that I don't have access to this disk.

Running "ls -l /dev/sdb2" gives brw -rw

My primary hard drive has Owner permission of rwx

How can I make the second drive the same?

Ubuntu 12.04, KDE 4.8.1
Both drives are SATA

---

### Post by satish_j on 2012-06-13
new hard drive formatted to what filetype?

---

### Post by bill-lancaster on 2012-06-13
Type is ext2

---

### Post by Jonny87 on 2012-06-13
Mount the Drive, find out where it's mouted (e.g. /media/MyDrive), then use try the following command;

sudo chown -R *username*:*username* */Drive/Location*

i.e.
```
sudo chown -R jonny:jonny /media/MyDrive
```

Then See if that helps.

---

### Post by bill-lancaster on 2012-06-13
ran "sudo chown -R bill:bill /dev/sdb2", entered password then straight back to bill@bill-Vostro-200:~$.

No change to permissions

---

### Post by jackluu on 2012-06-13
if it is a newly formatted drive, one very simple way is to format the drive again using disk utility choose take ownership of this partition. and you have it :D
i think you should format it with ext4 file type. :)

---

### Post by bill-lancaster on 2012-06-13
btw - there's nothing on the disk so for example, I'd be happy to format is again or whatever.

---

### Post by steeldriver on 2012-06-13
> **bill-lancaster said:**
> ran "sudo chown -R bill:bill /dev/sdb2", entered password then straight back to bill@bill-Vostro-200:~$.

No change to permissions

the problem is you are trying to change permissions on the underlying block device - like Jonny87 says you need to find where it's mounted in the filesystem, and then change the ownership of *that* - if it's not mounted then you need to mount it (with rw permissions, obviously - although iirc that is the default for ext2/3/4)

---

### Post by bill-lancaster on 2012-06-13
I thought " /dev/sdb2" is where its mounted.  If not then how do I find out?

---

### Post by Morbius1 on 2012-06-13
My guess is it's in /media somewhere but to be sure look at the output of this command:
```
mount
```

---

### Post by Jonny87 on 2012-06-13
> **bill-lancaster said:**
> I thought " /dev/sdb2" is where its mounted.  If not then how do I find out?

In Linux things that are under /dev such as /dev/sda, /dev/sdb, /dev/sdb1, /dev/hda etc are referring to devices. But those devices need to be mounted on the Linux Directory for you to be able to access them. The can be mounted any where, even in your home directory. Ubuntu usually mounts device such as Hard Drives and USB Stick in /media/*Device Lable* or /media/*Device ID*.

You could use the following command to see if it is mounted;
```
df -h
```
And look for the line starting with /dev/sdb1 then across on the other side under "Mounted On" you'll see where it's mounted. If it's mounted then readjust the command accordingly (if the path that its mounted on has spaces, the put it in quotations or put use \ i.e. "/media/My Drive" or /media/My\ Drive). If it's not mounted, then try the following;

```
sudo mkdir /media/drive
```
This will create a directory in /media

```
sudo mount /dev/sdb1 /media/drive
```
This should mount the drive under /media/drive so that way you know where it is mounted. You can confirm that with the following;
```
df -h
```

If your sure that it is mounted in the correct location, then proceed with the following (replacing "username" with your own username on your system);
```
sudo chown -R username:username /media/drive
```
This will change the permissions of everything under /media/drive, in this case your Hard Drive.

Or if you have nothing it to loose you could also try formatting it  with the take ownership option as mentioned above. I suggest using ext4 as well (unless you want to access it from windows then in that case use ntfs).

---

### Post by bill-lancaster on 2012-06-17
Jackloo - good idea, re-formatted, re-partitioned, made sure I was the owner this time!

---


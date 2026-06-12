---
title: "Restore unmountable disk"
date: 2011-02-10
forum: General Help
---

### Post by IronF on 2011-02-10
Hi guys,
probably few days ago my computer suddenly get switched off during the system boot and now I cannot mount the partition with ubuntu and ALL MY FILES.
If I try to boot this is the result:
```
[...]
mount:mounting /dev on /root/dev failed: No such file or directory
mount:mounting /sys on /root/sys failed: No such file or directory
mount:mounting /proc on /root/proc failed: No such file or directory
Target filesystem dosen't have /sbin/init.
No init found. Try passing init=bootarg
```
And If I try e2fsck /dev/sda1, it refuse to run stating "Device or resource busy while trying to open /dev/sda. Filesystem mounted or opened exclusively by another program?"
How can I recovery my data at least?

---

### Post by Spencer Reid on 2011-02-10
Bios is probably corrupt. Try re-installing BIOS

---

### Post by 3Miro on 2011-02-10
Try booting a LiveCD. From there you will be able to recover your data and perhaps fix the problem.

---

### Post by IronF on 2011-02-11
> **3Miro said:**
> Try booting a LiveCD. From there you will be able to recover your data and perhaps fix the problem.
I used the LiveCD but I can't mount the partition!

---

### Post by 3Miro on 2011-02-11
Do you get any errors? You can try this:

[http://ubuntuforums.org/showthread.php?t=694301](http://ubuntuforums.org/showthread.php?t=694301)

---

### Post by IronF on 2011-02-11
Now, maybe something is changed, probably in a worst way...:(
Now if I try ```
mount /dev/sda1
``` this is the result```
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
```
I've just tryed ```
sudo mkdir /media/windows
sudo mount /dev/(yourdevice) /media/windows -o force
``` but nothings happened.

---

### Post by 3Miro on 2011-02-11
Try:

```
sudo mkdir /media/oldhdd
sudo mount /dev/sda1 /media/oldhdd
```

Now the trick is to find which one is the right partition. You can do

```
sudo fdisk -l
```

to get a list of all HDD devices and partitions. They will most likely be labeled sda1, ada2, adb1 ....

If this doesn't work, you can try:
```
sudo mkdir /media/oldhdd
sudo mount -o force /dev/sda1 /media/oldhdd
```

---

### Post by IronF on 2011-02-11
First, thank you for your help, and apologize me if I wasn't clear!
I'm gonna try to be clear. This is the situation of my pc, I've 2 hd with ubuntu e windows. Windows is still working(unfortunately)
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004620f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19084   153285632   83  Linux
/dev/sda2           19084       19458     3002369    5  Extended
/dev/sda5           19084       19458     3002368   82  Linux swap / Solaris

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
240 heads, 63 sectors/track, 21274 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f2f6f2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       21273   160823848+   7  HPFS/NTFS

```
I tryed to mount but it doesn't work:
```
ubuntu@ubuntu:~$ sudo mkdir /media/oldhdd
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/oldhdd/


```
I tryed also with force but:
```
ubuntu@ubuntu:~$ sudo mkdir /media/hdd
ubuntu@ubuntu:~$ sudo mount -o force /dev/sda1 /media/oldhdd
mount: mount point /media/oldhdd does not exist

```

---

### Post by IronF on 2011-02-11
> **IronF said:**
> 
I tryed also with force but:
```
ubuntu@ubuntu:~$ sudo mkdir /media/hdd
ubuntu@ubuntu:~$ sudo mount -o force /dev/sda1 /media/oldhdd
mount: mount point /media/oldhdd does not exist

```
ok sorry I've just tryed with
```
ubuntu@ubuntu:~$ sudo mkdir /media/oldhdd
mkdir: cannot create directory `/media/oldhdd': File exists
ubuntu@ubuntu:~$ sudo mount -o force /dev/sda1 /media/oldhdd


```
but it's the same situation: it's working but nothing is happening(I can't use the same terminal any more)

---

### Post by 3Miro on 2011-02-11
That last one should have worked. Read the errors that you get, file already exists and no such file for example.

Once you do the last one, you should have your HDD mounted. Go into Nautilus (Places -> Home) then go up until you reach / and enter /media. You should see a folder oldhdd that has all of your files from the hard-drive.

---

### Post by oldfred on 2011-02-11
One other user recently had the same issue with device busy, so they could not run e2fsck.

They solved it by downloading one of the other small distributions ( forgot which they used) and then they were able to run the e2fsck. For them it may have been just that Ubuntu was in the extended partition and they did not unmount swap and the other distribution did not automatically mount swap, but I still might try it as it cannot hurt.

---

### Post by IronF on 2011-02-12
> **3Miro said:**
> That last one should have worked. Read the errors that you get, file already exists and no such file for example.

Once you do the last one, you should have your HDD mounted. Go into Nautilus (Places -> Home) then go up until you reach / and enter /media. You should see a folder oldhdd that has all of your files from the hard-drive.
No sorry again, I think that I got that error because I had created the same directory twice...
I'm gonna try with another Live-CD distro.

---

### Post by Philio on 2011-02-12
This sounds identical to the problem I had this morning on a brand new SSD drive I had installed last night.

I tried everything above and a few other things but was unable to get the drive to mount at all. As I had little more than a base install I gave up and just nuked the partition table and started over.

Maybe there is something in syslog or dmesg that has some clues?
I read somewhere (after I'd reformatted) that someone had a similar problem and used a different disto live cd to fix, as someone mentioned in this thread too. I think they said it was slackware.

---

### Post by Philio on 2011-02-12
Sorry, my mistake, you want slax not slackware.

There is another thread on it here: [http://ubuntuforums.org/showthread.php?t=1601810](http://ubuntuforums.org/showthread.php?t=1601810)

Bottom of page 2 onwards.

---

### Post by IronF on 2011-02-13
THANK YOU GUYS, I restore my hd with Slax!
Endless Thank you...

---


---
title: "Home Folder"
date: 2006-04-28
forum: General Help
---

### Post by Kakason on 2006-04-28
Hello. I just installed Ubuntu (again) on a different partition. I'm going to format the other Ubuntu on the other partition. What I want to do is like let my Home Folder take the formatted partition. 

Murakami Kakason

---

### Post by Ramses de Norre on 2006-04-28
cd to your home folder and execute this:
```
find . -depth -print0 | cpio --null --sparse -pvd /mountpoint
```
change /mountpoint to a folder you'll save your home temporarly to.
Then format the old disk and mount the partition as /home. cd to the earlier chosen temporarly directory and do ```
find . -depth -print0 | cpio --null --sparse -pvd /home
```
Then rm the temporarly directory.

---

### Post by Kakason on 2006-04-29
[quote=Ramses de Norre]
Then format the old disk and mount the partition as /home. cd to the earlier chosen temporarly directory and do ```
find . -depth -print0 | cpio --null --sparse -pvd /home
``` Then rm the temporarly directory.[/quote]

Sorry but that step didn't quite make sense to me - lemme show the steps then you correct me if there is anything wrong.

1. cd into home folder
2. code in terminal
3. format my old ubuntu partition
4. mount the partition as /home (? I don't quite know how to do that)
5. cd into temporarly home directory
6. type in the code
7. remove the temp home directory

---

### Post by cvmostert on 2006-04-29
I want to do the same... but i dont want to format the second hdd, only mount it as home, or make it my default saving place...

will search around and report bach when i find something... had a tough time getting my wlan to work on dapper beta.. but thanks to all the nice guys on this forum it runs! broadcom... had to set the rate at 11M...

---

### Post by Ramses de Norre on 2006-04-29
The command I gave you will copy over everything from the current directory (the one you cd into) to the directory you define as last argument of the command. So what I told you to do is use that command to create a back up of your home in a directory somewhere on your other hard disk, then create (format) the partition you want /home to be in (@ cvmostert: skip this step), mount the partition as /home and use the command again by cd'ing into the backup directory and defining the directory to copy the files into (the last argument of the command) as /home.

To mount a partition as home: sudo gedit /etc/fstab and add a line like this for the partition: ```
/dev/hda4       /home               ext3    nodev,nosuid 0       2

```
You'll need to change "/dev/hda4" to your device node.

I hope it's clear now.

---

### Post by cvmostert on 2006-04-29
thanx, fstab is what i needed... will see later if it works... after reboot...

---

### Post by Ramses de Norre on 2006-04-29
No reboots needed in linux ;)
You can just umount the partitions which are changed and the do sudo mount -a to mount everything in fstab.

---

### Post by Kakason on 2006-04-29
What partition program did yous guys use? I use gpart but like when I format the partition 1, and then I mount it, there was this folder in it? So I'm like wdh. I got it working but I dont like that folder. Lost and Found.

Murakami Kakason

---

### Post by Ramses de Norre on 2006-04-29
That's normal, your system uses this folder.. it should be in /home and not in /home/user_name so I don't see much harm in it. (deleting wont help, it will reappear on each fsck)

---

### Post by Kakason on 2006-04-29
Whoa, ok. Anyways, Thanks Bro. ( nearly forgot about it ^_^ )

Murakami Kakason

---


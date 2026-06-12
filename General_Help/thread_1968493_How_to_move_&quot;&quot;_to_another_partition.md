---
title: "How to move &quot;/&quot; to another partition"
date: 2012-04-29
forum: General Help
---

### Post by Taak on 2012-04-29
I have not enough space to upgrade to 12.04 :(

I have 3 partitions on the same HDD:

part 1 (mount /) - very small
part 2 (mount /home) - very big
part 3 (swap)

I would like to copy part 1 content to part 2 and tell Ubuntu that it must mount everything from partition 2.

Note that I cannot resize these partitions (they are xfs).

How can I do this?

---

### Post by Irony on 2012-04-29
You can use a simple copy command to back up or move your entire distro or part of a distro. It looks something like this;

```
sudo cp -ax /home/taak/. /media/folder/home/.
sudo cp -ax /. /media/folder/.
```

Of course you will then have to update your fstab and update grub.

I'd recommend you try this command to back up your root folder to an external drive (formatted as xfs) just to get a feel for it, i.e. first create a folder/s in your external drive and try using the command to copy to it.

Once you are familiar with the command then use it to move the contents of your partitions around.

---

### Post by Taak on 2012-04-29
Ok, so I would do something like this:

1) sudo cp -ax / /media/my-partition-2/ (why did you put a dot?)

2) edit /etc/fstab (I will simply change the mount point of "/" to the partition number 2, right?)

3) Auto update grub using: sudo update-grub

Is this right? Should I do something else?

Thank you

---

### Post by coffeecat on 2012-04-29
@Taak, I would advise you to use a live CD to copy the contents of your root (/) partition to partition 2 (your current /home partition). Doing a copy of an OS from within a working OS always leads to problems - I speak from experience. At the very least, if you do the copy from within your working system, when it gets to /home, your /home partition is mounted on your /home folder in /, and may attempt to do an endless recursive copy onto itself. There may be an option with cp to prevent that, but it's quicker and easier to use a live CD and work outside the system. **EDIT**: just realised. You'd need to unmount partition 2 from /home otherwise all your system folders and files would go into /home, but you can't unmount your /home and keep the system running. Use a live CD.

Also when you get to copy partition 1 into partition 2, you need to exclude the empty /home folder. It's possible it will replace the /home folder and all contents in partition 2, and you will lose all your files. I can't remember whether the default with cp is to prompt for an overwrite, but be cautious.
 
> **Taak said:**
> 
2) edit /etc/fstab (I will simply change the mount point of "/" to the partition number 2, right?)

And you would need to remove the line that mounts partition 2 onto /home. You might want to post the contents of fstab and the output of "sudo blkid".

---

### Post by Taak on 2012-04-29
**1)** **fstab**

My blkid is:

```
[...]
/dev/sdc2: UUID="3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4" TYPE="xfs" 
/dev/sdc3: UUID="ae5866bb-cc73-41b3-9b0f-f3817867f426" TYPE="xfs" 
/dev/sdc4: UUID="c2dc6d7b-6984-4fc4-aede-b5876e28ae08" TYPE="swap" 
```

My /etc/fstab says:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd2 during installation
UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 /               xfs     defaults        0       1
# /home was on /dev/sdd3 during installation
UUID=ae5866bb-cc73-41b3-9b0f-f3817867f426 /home           xfs     defaults        0       2
# swap was on /dev/sdd4 during installation
UUID=c2dc6d7b-6984-4fc4-aede-b5876e28ae08 none            swap    sw              0       0
```

I will remove the second line and modify the first one to "0 2", right?


**2)** **Copy using the live CD.**

Ok, I have an old live CD :P I think that I should do something like:

mount /dev/sdc2 /media/source
mount /dev/sdc3 /media/destination
cp -ax /media/source/ /merdia/destination/

Right?


**3) Grub**

Is  "update-grub" the right one command?


Thank you, I'm quite scared :D

---

### Post by coffeecat on 2012-04-29
> **Taak said:**
> 
Thank you, I'm quite scared :D

I don't blame you. The more I think about this, the more hair-raising it becomes! :wink:

> **Taak said:**
> **3) Grub**

Is  "update-grub" the right one command?


Thinking more about grub, you will need much more than that. Running "update-grub" from the live CD won't achieve anything. You need to:

1 - re-install grub to the mbr so that it points to the old /home partition, which will become your root partition.

2 - run update-grub from within the running system, but you can't boot into your running system until you run update-grub. Catch-22! :)

There's a way round this: chroot into your reconstructed system from the live CD to both re-install grub and run update-grub. Have a look at this:

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

I'm a bit busy at the moment, but I'll come back to this in a couple of hours to see if there's anything else I've missed. Or perhaps someone else can add something, perhaps Irony.

To be honest, you might find it quicker, easier and less stressful to backup your data, repartition your drive, and re-install. You could even choose a filesystem easier to work with such as ext4! Out of interest, why did you choose xfs?

---

### Post by Taak on 2012-04-29
I chose xfs because I had to work with large files sorting algorithms (external sorting - see [http://sortbenchmark.org/](http://sortbenchmark.org/)). Xfs is the fatest filesystem managing large files.

By the way, thanks for your help :)

---

### Post by coffeecat on 2012-04-29
OK, a couple more things to take into account:

> **Taak said:**
> **1)** **fstab**

My blkid is:

```
[...]
/dev/sdc2: UUID="3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4" TYPE="xfs" 
/dev/sdc3: UUID="ae5866bb-cc73-41b3-9b0f-f3817867f426" TYPE="xfs" 
/dev/sdc4: UUID="c2dc6d7b-6984-4fc4-aede-b5876e28ae08" TYPE="swap" 
```

My /etc/fstab says:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd2 during installation
UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 /               xfs     defaults        0       1
# /home was on /dev/sdd3 during installation
UUID=ae5866bb-cc73-41b3-9b0f-f3817867f426 /home           xfs     defaults        0       2
# swap was on /dev/sdd4 during installation
UUID=c2dc6d7b-6984-4fc4-aede-b5876e28ae08 none            swap    sw              0       0
```

I will remove the second line and modify the first one to "0 2", right?


Wrong! :wink: You need one line with the sdc3 UUID, but mounted at '/', and "0 1". (When you installed, the current sdc was then sdd.) Your new fstab root line would need to be:

```
UUID=ae5866bb-cc73-41b3-9b0f-f3817867f426 /           xfs     defaults        0       1
```

> **Taak said:**
> **1)** **fstab**

**2)** **Copy using the live CD.**

Ok, I have an old live CD :P I think that I should do something like:

mount /dev/sdc2 /media/source
mount /dev/sdc3 /media/destination
cp -ax /media/source/ /merdia/destination/

Right?
 
Apart from the /media typo in the 3rd line, nearly there. You don't need the -x (one-file-system) option when copying using the live CD. That's for copying from within a system and, as I mentioned before, I don't advise it. Or at least it failed miserably when I tried it a couple of years ago. I prefer "sudo cp -av blah blah". The verbose option gives you feedback - useful, because this can take a long time and you need to know it's still working.

Also - if you are going to mount sdc3 on /media/destination, modify the commands in the grub install/chroot instructions I linked you to.

I think I've caught everything, but can't be 100% sure. I've done similar myself on many occasions, but have always been happy to plough ahead knowing that if I forget something, I'll soon hear about it from error messages and know what to do. Trying to advise someone and anticipate everything you need to do is a whole different ball-game. I'll have another look at this thread in an hour or so.

---

### Post by Taak on 2012-04-29
> **coffeecat said:**
> 
Also - if you are going to mount sdc3 on /media/destination, modify the commands in the grub install/chroot instructions I linked you to.

Ok. Should I replace in every step /mnt with /media/destination, right?

---

### Post by coffeecat on 2012-04-29
> **Taak said:**
> Ok. Should I replace in every step /mnt with /media/destination, right?

It doesn't matter that much. When you are chrooting, it's so much easier to have the partition you will be chrooting into mounted on /mnt. Less to type in! If you mount your destination partition on /mnt that will work fine for the copy, but you'll have to navigate through the filesystem if you want an open nautilus to monitor progress. Mounts in /media and subfolders - a nautilus window opens automatically. Mounts in /mnt - you have to open one yourself. If I remember correctly, that is!

---

### Post by coffeecat on 2012-04-29
@Taak, sorry I promised to come back earlier to have another read-through of the thread, but I have had more distractions in real life than I anticipated. There is one point that's just occurred to me and because I haven't setup a separate home partition for some time (I use a data partition), I can't remember exactly what the situation is.

From the live CD, have a look at the contents of your sdc3 partition, your current home partition. Are your username folder and any other account folders in the root of the partition filesystem, or is there just a single "home" folder which itself contains the account folders? If the latter, then no problem. If the former, then you will have to create a folder called "home" and move the account folders into it. Making sure you don't copy the empty home folder from sdc2 when you do the copy, of course.

---

### Post by Taak on 2012-04-30
I don't remember if there was a home directory, however everything went fine so I assume there was it. ;)

Again, thank you very much! :D

---

### Post by coffeecat on 2012-04-30
Excellent. Good luck with the upgrade!

---


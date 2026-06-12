---
title: "Limited Space"
date: 2010-09-06
forum: General Help
---

### Post by jsmith3257 on 2010-09-06
When I first installed Ubuntu 10.04, I told it to install on the D drive (which had 104 gb).  When I select the data disk, that's where it goes to.  For some reason, though, the space of the rest of the ubuntu is a lot less.  It's telling me I have less than 1gb left of free space.  What's going on?

When I the file system tab, it says 217.5 mb remaining.  I should have the 104 gb remaining instead.

---

### Post by stee1rat on 2010-09-06
What does **df -h** command says to you?
And you can always run gparted to figure out what's going on with your hard drives.

---

### Post by afrowildo on 2010-09-06
Run the disk usage analyser found in **Applications** -> **Accessories**. That will tell you exactly where all your space has gone.

---

### Post by jsmith3257 on 2010-09-06
> **stee1rat said:**
> What does **df -h** command says to you?
And you can always run gparted to figure out what's going on with your hard drives.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   16G  221M  99% /
none                  1.4G  360K  1.4G   1% /dev
none                  1.4G  512K  1.4G   1% /dev/shm
none                  1.4G  204K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw
/dev/sda2             111G   88G   23G  80% /host
/dev/sr0              2.6G  2.6G     0 100% /media/CIV4_COMPLETE
/dev/sda3             107G  2.8G  105G   3% /media/DATA
```

---

### Post by stee1rat on 2010-09-06
Well.. Is there **home** directories in **/media/DATA** and **/**?
If so, you just need to change your home directory to the one in /media/DATA, i guess :)

---

### Post by jsmith3257 on 2010-09-06
> **stee1rat said:**
> Well.. Is there **home** directories in **/media/DATA** and **/**?
If so, you just need to change your home directory to the one in /media/DATA, i guess :)

How do I change my home directory?

---

### Post by stee1rat on 2010-09-06
The one of the ways is to follow this guide: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 
that's what i did.

You don't need to create a partition, 'cause you already have one, you just need to edit /etc/fstab file and put there a line to mount your /dev/sda3 as /home.

---

### Post by stee1rat on 2010-09-06
Actually, i think your ubuntu was installed on wrong partition. As you can see, your root directory (**/**) mounted on 17 Gb partition. If you have just installed it, i think you better reinstall it on the right partition, if not, i think that moving the home directory is the right way. Just check what takes so much space on **/** with **baobab** (Disk Usage Analyzer) application.

---

### Post by jsmith3257 on 2010-09-06
When I tried moving my files, it tried to tell me that 128TB was required.  I'm pretty sure that's not right.

---

### Post by stee1rat on 2010-09-06
How did you tried to do it? What files?

Can you do **ls -lh** on files you're trying to move?

---

### Post by jsmith3257 on 2010-09-06
> **stee1rat said:**
> How did you tried to do it? What files?

Can you do **ls -lh** on files you're trying to move?

I just selected all the files on the file system and dragged them to the d disk.

---

### Post by stee1rat on 2010-09-06
What is D disk? There's no D disks in ubuntu..
Anyway **ls -lh** can say you and me file sizes.
You can also copy files with **cp** command.

---

### Post by stee1rat on 2010-09-06
You can also use **du -sh directory_path** to see the total size of the directory.

---

### Post by jsmith3257 on 2010-09-06
> **stee1rat said:**
> What is D disk? There's no D disks in ubuntu..
Anyway **ls -lh** can say you and me file sizes.
You can also copy files with **cp** command.

My computer originally came with windows vista.  The windows itself was on the C: drive and there was another D disk for data.  I selected the D disk to install Ubuntu on (that and C were the only choices actually).  I don't know why another partition would be created.  I'll check all the other stuff now.

Also, what's the disk usage analyzer program called?

---

### Post by stee1rat on 2010-09-06
It's called baobab, you can press alt+f2 and type baobab + enter

Well, how do you choose disk d in ubuntu? If it is in "Places" then after opening it as a folder it's became mounted in /media directory. And you can check the files and directories sizes there. And the better way to show it on forum is to use a terminal and post here the outputs.

---

### Post by jsmith3257 on 2010-09-06
The reason it was a 17gb partition is because that's the size that was default on the install inside windows option.  I'm reinstalling now and changing it to 30, but is there any way I can change it to its full size?

---

### Post by stee1rat on 2010-09-07
You can use gparted or windows's fdisk or partition magic to remove those two partitions and make it one. But something is telling me there's 2 physical disks. Just make a screenshot of what one of this applications shows to you and post it here.

---

### Post by jsmith3257 on 2010-09-07
> **stee1rat said:**
> You can use gparted or windows's fdisk or partition magic to remove those two partitions and make it one. But something is telling me there's 2 physical disks. Just make a screenshot of what one of this applications shows to you and post it here.

There are (C and D).  Here's my computer on windows:
[img]http://img687.imageshack.us/img687/2287/captureai.jpg[/img]

When I display my computer on ubuntu, it puts those two together as one 250gb drive and the seperate partition of 17gb as another.  I want to install it with it's full 104gb (the data disk).

---


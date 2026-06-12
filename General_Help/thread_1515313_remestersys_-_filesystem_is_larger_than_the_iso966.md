---
title: "remestersys - filesystem is larger than the iso9660 ?"
date: 2010-06-22
forum: General Help
---

### Post by arapaho on 2010-06-22
Remastersys shows message:
"The compressed filesystem is larger than the iso9660 specification allows for a single file. You must try to reduce the amount of data you are backing up and try again."

I wanted to make a system backup. I have root partition - 30GB and home, also 30 GB. Additionally two other partitions that are visible as separate disks. I wanted to save this backup in a partition that has 80 GB of free space. So, why such a problem occurred?
Does remestersys make clone of entire 60 GB - root + home partition + this two other disks or only root and home partitions? I can't see there any option to mark what to backup. 

Does remestersys compress this backup files or makes clone with exact size of backed partitions?

Anyway, give me a tip what to do, please.

---

### Post by jwbrase on 2010-06-22
Remastersys is meant for backing up to a CD or DVD. So it's complaining that even with the entire filesystem compressed, it can't make it small enough to fit within the size limit for a file on a CD/DVD. If you're trying to back up to another hard drive, Remastersys is not the program you want.

---

### Post by philinux on 2010-06-22
> **arapaho said:**
> Remastersys shows message:
"The compressed filesystem is larger than the iso9660 specification allows for a single file. You must try to reduce the amount of data you are backing up and try again."

I wanted to make a system backup. I have root partition - 30GB and home, also 30 GB. Additionally two other partitions that are visible as separate disks. I wanted to save this backup in a partition that has 80 GB of free space. So, why such a problem occurred?
Does remestersys make clone of entire 60 GB - root + home partition + this two other disks or only root and home partitions? I can't see there any option to mark what to backup. 

Does remestersys compress this backup files or makes clone with exact size of backed partitions?

Anyway, give me a tip what to do, please.

Remastersys has a limit of 4gig for the iso.

> limit of 4Gig for any single file on the iso file which is a limitation of the iso9660 spec which means the compressed filesystem must be 4G or less - no workaround.

[http://geekconnection.org/remastersys/info.html](http://geekconnection.org/remastersys/info.html)

---

### Post by arapaho on 2010-06-22
But I have now idea how to do it properly. 
I have:
Working directory=/home/remastersys
and I use the first option:
Backup complete system including user data.

I want to backup to DVD. Why it tells me about size of filesystem?
My file system looks like this:
```
             bl.  1K B        used availavble 
/dev/sda1             28835836   4521908  22849148  17% /
/dev/sda6             30220240  14071284  14613828  50% /home
/dev/sda7             93856616  17268940  71819988  20% /media/
```

I want remastersys to backup only root and home. Do I have to exclude sda7?

---

### Post by philinux on 2010-06-22
Use this.

```
df -h
```

Yes you can exclude folders etc. Use the edit configuration from the remastersys menu.

---

### Post by arapaho on 2010-06-22
Thank you for your help. Finally I succeeded. It appeared that I had a hidden backup file that wasn't visible from Nautilus. I had to use Parted Magic tools to delete it. By the way, I recommend this wonderful piece of emergency kit. 
At least I learned something new: new command and that I can't overload my home partition. :) Remestersys works like a charm.

But I have another question. What if I lose MBR? Do I have to recover the whole system or is it possible to recover only MBR? Can you recommend a solution only for this specific situation? Can it be done with remastersys backup somehow or I need to get to know something else? I'm new to Ubuntu and I didn't tested all options, but I want to know just in case. Does Ubuntu has any tool build in that can help when this situation happen?

---

### Post by philinux on 2010-06-22
> **arapaho said:**
> Thank you for your help. Finally I succeeded. It appeared that I had a hidden backup file that wasn't visible from Nautilus. I had to use Parted Magic tools to delete it. By the way, I recommend this wonderful piece of emergency kit. 
At least I learned something new: new command and that I can't overload my home partition. :) Remestersys works like a charm.

But I have another question. What if I will losse MBR? Do I have to recover the whole system or is it possible to recover only MBR? Can you recommend a solution only for this specific situation? Can it be done with remastersys backup somehow or I need to get to know something else? I'm new to Ubuntu and I didn't tested all options, but I want to know just in case. Does Ubuntu has any tool build in that can help when this situation happen?

It's basically a livecd like any other so it can be used to reinstall grub to the mbr.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by arapaho on 2010-06-22
Rather serious staff. I will have to learn more about it. Thank you for directing me.

---

### Post by philinux on 2010-06-22
> **arapaho said:**
> Rather serious stuff. I will have to learn more about it. Thank you for directing me.

There is another version. Same result.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by hesapotman on 2010-10-19
I figured out what the problem was for me. And frankly, considering I have a Master's degree in Computer Science, I'm a little ashamed I didn't catch this earlier. Here's the deal ...

My PC is configured as dual-boot, so there is a Windows partition as well as Ubuntu. In addition, when I installed Ubuntu, I opted to have the Windows partition mounted in Ubuntu at startup (for fast/easy access).

So the problem was that, when I ran remastersys, my entire Windows partition was being included in the image. Bad.

To fix the problem, I edited my "/etc/fstab" file and commented out the line that mounts my Windows partition at startup. Then I rebooted the computer and ran remastersys. The resulting ISO file was only 1.6 GB ... Everything worked fine.

Anyway, that's how I fixed my specific problem. I hope it helps someone else.

---

### Post by hesapotman on 2010-11-23
OK I just got a PM from an Ubuntu noob asking exactly how I edited the "fstab" file. Since other noobs might want/need this info, I'll just post it here publicly.

First, we want to open the file "/etc/fstab" for editing.

```
sudo gedit /etc/fstab
```

Now we are looking for a line that looks like this:

```
UUID=965EC54A5EC53759 /windows  ntfs  defaults,umask=007,gid=46  0  0
```

**Note that your "UUID" will NOT be the exact same as mine. The dead giveaway that you have the right line is the "/windows" and/or the "ntfs" parts.**

So now that we have identified the line we want, we simply comment it out by inserting a '#' (hash/pound symbol) as the first character on the line. For example ...

```
# UUID=965EC54A5EC53759 /windows  ntfs  defaults,umask=007,gid=46  0  0
```

Now "Save" the file and "Close" the gedit text editor.

At this point, we reboot the computer so that the Windows partition is not loaded at startup.

That should be it!

In order to reverse this later, simply follow the above instructions, but this time REMOVE the hash mark (#) that you used to comment out the Windows partition line.

---

### Post by crl0901 on 2010-11-29
> **jwbrase said:**
> Remastersys is meant for backing up to a CD or DVD. So it's complaining that even with the entire filesystem compressed, it can't make it small enough to fit within the size limit for a file on a CD/DVD. If you're trying to back up to another hard drive, Remastersys is not the program you want.

I'm trying to backup to a mounted share on my Windows Home Server machine.  I was using Remastersys to create ISOs, then copying those ISOs to that share, but now I'm also getting the file size too large error.  I've tried some other backup solutions, like BackInTime, but none work like Remastersys.  Any suggestions on a good backup solution to replace Remastersys?

---

### Post by crl0901 on 2010-11-30
Anyone?  There's got to be a good alternative to Remastersys.

---

### Post by hesapotman on 2011-08-09
> **crl0901 said:**
> Anyone?  There's got to be a good alternative to Remastersys.

Eh, Ubuntu Customization Kit (uck) worked for a while ... then it didn't. I haven't tried it in a LONG time, so maybe it's not "broken" anymore. Couldn't hurt to check it out. Good luck!

---


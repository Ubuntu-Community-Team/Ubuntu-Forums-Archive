---
title: "how much space on the hard drive does the OS use?"
date: 2011-01-27
forum: General Help
---

### Post by Gatorade on 2011-01-27
Windows , Ubuntu , linux Mint etc.?

I did a dual boot installation with windows XP and Mint , and when I was finished I didn't have much space left on the windows partition to install any programs. I thought 20 GB would be enough since I was going to primarily use the Mint partition.

is XP that big ? takes up 20GB?

---

### Post by TeoBigusGeekus on 2011-01-27
```
df -h
```
in terminal to see the space used by all your partitions.

---

### Post by Gatorade on 2011-01-27
ok, I used that code. Now, what does this all mean?

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              94G   66G   23G  75% /
udev                  1.6G  304K  1.6G   1% /dev
none                  1.6G  240K  1.6G   1% /dev/shm
none                  1.6G  296K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw

When I partitioned it I recall partitioning it , 100GB for linux Mint and 20 GB for XP. 

can you tell me what those other 1.6G partitions marked none are for ?

---

### Post by TeoBigusGeekus on 2011-01-27
The other are not real partitions, just linux system folders.
To see all your hds, mount them first (select them from the places menu) and rerun the command.

---

### Post by Gatorade on 2011-01-27
When I double clicked on Computer, I can see the hard drive and the partitions on it. However , when I run that command it give me the same results.

You said mount them by selecting.But when I right click, it says unmount, so its already mounted , correct?

---

### Post by TeoBigusGeekus on 2011-01-27
Sorry, my mistake. The command should be
```
sudo fdisk -l
```
(-L)
I had my mind on another thread...

---

### Post by Gatorade on 2011-01-27
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eb5e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1697    13631121    7  HPFS/NTFS
/dev/sda2            1698       14593   103587120    5  Extended
/dev/sda5            1698       14063    99329863+  83  Linux
/dev/sda6           14064       14593     4257193+  82  Linux swap / Solaris


ok, here's what I got , so what does this mean?

---

### Post by TeoBigusGeekus on 2011-01-27
Sizes are in blocks of 1024bytes, so
Partition 1(sda1): 13631121blocks ~ 13gb for windows (ntfs)
Partition 2(sda2): Extended partition containing:
                   Partition 3(sd3): 99329863blocks ~ 94.7gb for mint
                   Partition 4(sd4): 4257193blocks ~ 4.06gb for swap

The rest of the disk space was lost in the conversion. :P

---

### Post by Gatorade on 2011-01-27
I guess I'll need to make the windows partition larger in the future. After everything was done I really only ended up with a couple of GB free space on the windows partition. I kept running out of space when I tried to install any programs.

I think a 250 GB drive should do the trick when I get a chance to get one.

---

### Post by TeoBigusGeekus on 2011-01-27
Also, your swap is huge (no sexual innuendo implied).
A gig would be enough.

---

### Post by Gatorade on 2011-01-27
do you know how to change that?
I don't remember being asked to set it , when I did the installation it did everything by itself.

---

### Post by TeoBigusGeekus on 2011-01-27
I don't know, I've never needed it anyway.
Whenever you install ubuntu(linux in general), never let the installer do the partitioning for you. In ubuntu's case, choose manual partitioning.
Also, make a separate home partition-it can save you from a lot of trouble in the future.

As for changing the size of swap, google it; I'm sure there must be something out there...

---

### Post by Gatorade on 2011-01-27
yeah, I did manually partition it.I didn't see anything asking about the swap.

What's the home partition for ? backup purposes?

I'll look into the swap thing. I probably won't do anything , though. I'll probably just get a new hard drive.

thanks for the advice.

---

### Post by TeoBigusGeekus on 2011-01-27
The /home partition holds your user settings.
If you have a separate home partition, you can reinstall ubuntu, keeping your old home folder, thus all your settings. That's settings, not programs. But, if after a new install of ubuntu (in which you use your old home folder) you reinstall your favourite programs, you will magically see all your old settings (from pre re-installing, if that makes any sense) reappear.

When you manually partition, you should specify at least 2 things:
/ root partition and swap.
I guess that having not specified it, the installer decided by itself...

---

### Post by Gatorade on 2011-01-27
so , how would I go about making this partition, and how large is recommended?

---

### Post by TeoBigusGeekus on 2011-01-27
What I'd do with a 120gb disk (which is sufficient - don't spend any money on a new one):
34gb for windows (ntfs)
1gb swap
15gb for root partition (mount point:/, format: ext4)
20gb for home partition (mount point:/home, format:ext4)
50gb for shared data partition-torrents, porn, music, movies, photos, etc. (mount point:/media/DATA, format:ntfs)

In this way, you have sufficient space for both win and linux and a fair enough common data partition, to where you can throw stuff from both systems.

---

### Post by Gatorade on 2011-01-27
I'll try that and see if I can get it to work.

I just don't remember it asking me how I wanted it partitioned, all I recall is moving the slider to tell it how big I wanted each partition. I'll look for it when I do it again.

thanks again.

---


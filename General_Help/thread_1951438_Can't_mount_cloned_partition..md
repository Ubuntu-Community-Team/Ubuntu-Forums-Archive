---
title: "Can't mount cloned partition."
date: 2012-04-02
forum: General Help
---

### Post by DOS286 on 2012-04-02
I'm setting up a home server. My plan is to clone the HD once a week and take it off site. My simple solution was to plug in an external, and copy/paste the data partition from the internal to the external with gparted. It was my understanding that gparted uses dd for this function, but I'm not sure.

The system seems to work fine. Quick and easy. The only problem is, I can't mount the duplicated hard drive on the machine that made the copy. I can mount it on any other machine. I believe that there is a conflict between the original partition and the clone, like ubuntu cannot tell the difference between them. They show up as unique in gparted and the Disk Utility, but I cannot mount it. I did change the partition label to something new, but that was not enough. Does gparted copy the UUID when copying a partition? Could this be the problem? Can this be changed later to make the cloned partition unique? If so how?

Any help anyone can give would be appreciated.

---

### Post by Punica on 2012-04-02
Have tried mounting it by using the disk/partition name, rather than the UUID? ie:

mount /dev/sdb1 /mnt/bla

---

### Post by DOS286 on 2012-04-02
I have not. The machine also duals as a media player. It's under the tv and does not have a keyboard just a remote control. I can hook a keyboard up and try that but I would like to have a system where I can just plug in the external drive and have it mount per the ubuntu usual, or at least a mouse solution to mount (e.g. click mount through the Disk Utility). Any way to do this?

---

### Post by Punica on 2012-04-02
I'm unsure if that is possible. And I think you might be using the wrong tool to clone.

Through the commandline there are lots of tools which can do this better and incremental instead of the entire disk, like rsync, this is a lot quicker. 

I dont know of any of such a tool in graphical Ubuntu, but you might be able to find one in the software center. I just looked at 'file backup manager' and it seems to support what you need.

But ofcourse you could also just create a new filesystem on your external drives and copy everything there the usual way.

---

### Post by DOS286 on 2012-04-02
I could be wrong but I think that dd (backend to the gparted copy/past) is much quicker than rsync. Rsync does a file level copy and can be very efficient at keeping files in sync. dd does a block level copy of the entire drive and does not have to look at each individual file property. The way I'm doing it is quite fast, 3 hrs for 1.3 TB. I don't think rsync can beat that. 

To be clear, I'm not backing up files, I'm backing up an entire partition.

---

### Post by Punica on 2012-04-02
> **DOS286 said:**
> I could be wrong but I think that dd (backend to the gparted copy/past) is much quicker than rsync. Rsync does a file level copy and can be very efficient at keeping files in sync. dd does a block level copy of the entire drive and does not have to look at each individual file property. The way I'm doing it is quite fast, 3 hrs for 1.3 TB. I don't think rsync can beat that. 

To be clear, I'm not backing up files, I'm backing up an entire partition.

Than you are right :) Sorry, I did not know that was your target and thought there might've been a more efficient solution, with entire partitions DD is definately the way to go.

Can you type dmesg in the CLI and see if it produces errors when you plug the drive in. or mount it manually in the CLI and see what kind of error it spews?

---

### Post by DOS286 on 2012-04-02
I'm not near the machine at the moment. I can try that later and report the results.

---

### Post by sudodus on 2012-04-02
> **DOS286 said:**
> I'm setting up a home server. My plan is to clone the HD once a week and take it off site. My simple solution was to plug in an external, and copy/paste the data partition from the internal to the external with gparted. It was my understanding that gparted uses dd for this function, but I'm not sure.

The system seems to work fine. Quick and easy. The only problem is, I can't mount the duplicated hard drive on the machine that made the copy. I can mount it on any other machine. I believe that there is a conflict between the original partition and the clone, like ubuntu cannot tell the difference between them. They show up as unique in gparted and the Disk Utility, but I cannot mount it. I did change the partition label to something new, but that was not enough. Does gparted copy the UUID when copying a partition? Could this be the problem? Can this be changed later to make the cloned partition unique? If so how?

Any help anyone can give would be appreciated.
I think you have succeeded to clone the HD. The drive info is cloned including the partition table with UUIDs.

Do you want to mount it on the same computer at the same time as the internal system because you want to recover single files or folders?

You should restore from a cloned drive without mounting it (reversing the cloning process), or simply replace the original drive. I have only tried to mount two USB drives with the same UUIDs, but it might work to change the labels with gparted, and then mount it using the label to identify the drive.

From ```
man mount
``````
       -L label
              Mount the partition that has the specified label. 
```Maybe a better solution for you is to use [FONT=Courier New][SIZE=3]rsync[/SIZE][/FONT] for the backup as suggested by *Punica*.

Or to mount the cloned drive without any manipulation in another computer and recover files from it using rsync via the LAN (rsync is using ssh by default, so run sshd in at least one computer).

Have a look at the following link
[https://wiki.ubuntu.com/BasicSecurity#Backups](https://wiki.ubuntu.com/BasicSecurity#Backups)

*Edit: dd is faster than rsync if you copy everything on a full partition, but rsync is much faster if you are making an incremental backup (only copying what is new or has changed). But for fast cloning or imaging I use Clonezilla, which uses Partclone and it is faster than dd, because it is only copying the file data, not empty space.*

---

### Post by DOS286 on 2012-04-02
Yep. I want to restore files and folders back to the original. 

I've considered using rsync and I might switch in the future. For now, I'm still setting up the system and there are many large media files added on a daily basis. My gut feeling was that cloning the partition would be faster than inspecting and copying each file.

I'll give clonezilla a look. 

If I switch to rsync, I don't want to start over from an empty new partition. That first sync will take forever. Is there any way to edit the UUID and keep the data so it will mount like normal?

---

### Post by sudodus on 2012-04-02
> **DOS286 said:**
> ... Is there any way to edit the UUID and keep the data so it will mount like normal?

Yes, the following link helped me do it
[http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html](http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html)

But then you might get problems if you want to clone back or replace the old drive, but as long as you 'only' use it to get single files or groups of files back it should be OK.

---

### Post by DOS286 on 2012-04-10
Thanks! Worked a champ!

---

### Post by sudodus on 2012-04-11
> **DOS286 said:**
> Thanks! Worked a champ!
I'm glad you made it. Please click on [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page and mark this thread as SOLVED :KS

---

### Post by callmemahavir on 2012-04-11
Please refer the URL....

[http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

---


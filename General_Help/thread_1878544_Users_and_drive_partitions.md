---
title: "Users and drive partitions"
date: 2011-11-10
forum: General Help
---

### Post by StarStrider on 2011-11-10
I have Win7 (I'm on a 64-bit machine) installed parallel to Ubuntu and it's my primary OS. Recently it's having issues and while the techs figure it out, I installed Ubuntu so I can actually do things (it was okay-ed).

My problem is that this is a multi-user computer, so while my account is the administrator, I set up a standard account for the other users. On my account I can access the Win7 partition of the drive, where essentially all my files are currently. However, the standard user account cannot access that partition, which will be a problem since their files are also on the windows partition.

Short of copying files over, is there a way to change this? I already tried setting that account as another administrator, but that didn't have any affect.

---

### Post by dcstar on 2011-11-10
> **StarStrider said:**
> I have Win7 (I'm on a 64-bit machine) installed parallel to Ubuntu and it's my primary OS. Recently it's having issues and while the techs figure it out, I installed Ubuntu so I can actually do things (it was okay-ed).

My problem is that this is a multi-user computer, so while my account is the administrator, I set up a standard account for the other users. On my account I can access the Win7 partition of the drive, where essentially all my files are currently. However, the standard user account cannot access that partition, which will be a problem since their files are also on the windows partition.

Short of copying files over, is there a way to change this? I already tried setting that account as another administrator, but that didn't have any affect.

Use the **pysdm** tool to set up the Windows partition to be mounted at bootup with appropriate permissions for all users.

Do this at the start to create the mount point:
```
sudo mkdir /mnt/windows
sudo chmod 777 /mnt/windows
```
Do **not** try to mount it in /media.

---

### Post by StarStrider on 2011-11-10
> **dcstar said:**
> Use the **pysdm** tool to set up the Windows partition to be mounted at bootup with appropriate permissions for all users.

Do this at the start to create the mount point:
```
sudo mkdir /mnt/windows
sudo chmod 777 /mnt/windows
```
Do **not** try to mount it in /media.


I think I'm linux-challenged. =(  Okay, so I got pysdm installed. When I run it, it only gives me 1 partition listed under my drive. I didn't know what to do after that.

I thought it was just me being unfamiliar, so I looked up pysdm to get some tutorials and ran across [this article]("https://help.ubuntu.com/community/AutomaticallyMountPartitions"). Just to familiarize myself with my drive and partitions I used the sudo fdisk -l command in terminal to pull up the list, which shows 7 partitions. The last partition "sda7" was the only one that had shown in pysdm, but terminal's list showed it as being a Linux swap / Solaris system, so that's obviously not the one I want anyway.

So now I'm just more confused. =/

I tried to read through the instructions the article gave for manually editing the filesystem, but I don't understand enough of it to try anything.

---

### Post by StarStrider on 2011-11-10
Okay, sorry about the extra post, but I think I solved some of my problem (mostly my lack of grasp).

I installed GParted Partition Editor, which shows:

[IMG]http://i26.photobucket.com/albums/c102/ThoraoftheNord/RandomShite/Screenshotat2011-11-10083604.png[/IMG]

I want /dev/sda3 to be mountable by all users at the mount location /media/Gateway, though, yes, I understand that I should NOT mount /media.

So, what do I do?

---

### Post by proxx1850 on 2011-11-10
One could just throw it in fstab or am I missing something here ?

---

### Post by StarStrider on 2011-11-10
> **proxx1850 said:**
> One could just throw it in fstab or am I missing something here ?

Haha, I'm sure I could. I'm just not sure I understand what I'm doing within fstab commands. *total newbie*

I was trying to follow [this article]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") earlier, I'm just not familiar enough with Linux to understand everything.

Like, do I need to do the "preparation" section with:

```
ls /media/gateway
sudo mkdir media/gateway
```

Or can I just start with this part:

```
gksu gedit /etc/fstab
```

Then:

```
/dev/sda3   /media/gateway   vfat   user,fmask=0111,dmask=0000   0   0
```

And I'd be done? Or is there more to it? (Or something incorrect?)

---

### Post by proxx1850 on 2011-11-10
The *mistake* would be the vfat , that should be ntfs iirc.
Iam a bit rusty on this, dont take my word for it :)

I understand you a noob, but the best practice would be to use  UUID.
You can find the UUID of your drive in gparted.

But your on the right track here :)

---

### Post by oldfred on 2011-11-10
Mounting Windows for all users is not really recommended. In fact no user should be writing into the Windows partition as standard pratice. Windows does not like lots of writes and will eventually complain. Much better to create a separate shared data partition that is NTFS. Linux shows all the files & folders that Windows hides to prevent you from accidentally moving or deleting. Everything is exposed, so all users need to really understand Windows systems if you are letting them delete anything.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Your format is ntfs so do not use vfat. Permissions are just the opposite of normal where normal is 777 for full permissions, 000 is full permissions. Always run sudo mount -a after editing fstab to make sure you have edited it correctly. If it just returns it is ok, otherwise it gives errors that you need to correct before rebooting.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)


Examples:
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

sudo mkdir /mnt/WinXP
UUID=DA9056C19056A3B3 /mnt/WinXP ntfs defaults,nls=utf8,umask=227,gid=46 0 0
Note: the WinXP line will allow all local login users to read but not write to the partition. If you want to prevent all access then change the umask value to: umask=777. That will prevent all access - except for root.
sudo mount -a

---

### Post by StarStrider on 2011-11-10
Thank you, oldfred.

So, what you're saying is that I should ideally have 3 partitions on my drive: Win7 OS, Data files, and Ubuntu OS. Right?

I mostly needed the access to the sda/gateway partition to read files. I see what you mean about writing to the partition, though. I'll have to think of another solution, I guess. Ideally, especially since I'm currently having problems with my Windows7 installation as it is, I should really do a drive wipe and clean install for everything, and set things up so I have the OS's in separate partitions from the data files. UGH. That sounds like so much work XD

---

### Post by oldfred on 2011-11-10
NTFS really likes 30% free space to work well. (Linux likes free space too but not quite as much). But you have used 340GB of 616GB. You can shrink your main Windows c: drive and make a d: drive. You may have to do a conversion in more than one step as Windows 7 is installed in 30GB as a minimum normally so you must have a lot of data?

IF you shrink sda3, then move extended to include the new unallocated, you then can create a new logical NTFS data partition.

Use Windows to shrink the c: partition, but use gparted for everything else as Windows does not rewrite extended partitions correctly on changes all the time.

---

### Post by StarStrider on 2011-11-10
> **oldfred said:**
> NTFS really likes 30% free space to work well. (Linux likes free space too but not quite as much). But you have used 340GB of 616GB. You can shrink your main Windows c: drive and make a d: drive. You may have to do a conversion in more than one step as Windows 7 is installed in 30GB as a minimum normally so you must have a lot of data?

Haha, yeah I do. I'm a photographer, so I have a ton of hi-res photos and large catalogs. I only have like 30% of my photos on the drive; I use an external for actual storage and cycle what I'm working on to the computer. Plus I do a fair bit of gaming and such. XD

I've actually been thinking for a while that it would be nice to get a new internal for just my photos, so maybe I'll look into things sooner. That way I could transfer all files to the new drive, do a clean install to solve my Win7 problem and then set up a better partition plan with Ubuntu. We'll see.

Thanks for the help!

---


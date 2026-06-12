---
title: "/home Partition Permissions"
date: 2011-02-09
forum: General Help
---

### Post by EMABrad on 2011-02-09
I just expanded my /home partition again, and it dawned on me that I have a problem.  /home is on a partition of it's own, but I sense I screwed something up when I freshly installed 10.10.

See, the partition is set to mount at "/home", and that's it.  What this means is that I have all of the files and folders within the partition, but also it shows "brad", which is MY /home folder, which has my default download location and all of that in it.  I'd like to synchronize the whole situation a little better, because this means that I essentially have two "/home"s..  This problem wasn't urgent until I expanded the partition to add another 40GB onto it, and I'd like to put that memory to good use, but, unfortunately, I don't have write permissions to it by default.

Essentially, there are two problems I'd like to solve, one of which is more important than the other:

1. Acquire write permission to the /home partition.  This is the more important, because this entails my actual ability to utilize my computer to its fullest extent.
2. Hopefully merge /home and /home/brad so that I can have just one place to search in if I'm looking for something I downloaded.

My fstab file is as follows, given that it's probably relevant:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7040869a-3a4a-47a6-aee6-c51750c0cc96 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=bbe591fa-edfb-445f-9ab0-92a549b3934b /home           ext3    nodev,nosuid        0       2
# /windows was on /dev/sda1 during installation
UUID=4DC187E122287488 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=af492c66-71e5-44b5-a95b-57102369af1c none            swap    sw              0       0
```

Thanks in advance!

---

### Post by dcstar on 2011-02-09
> **EMABrad said:**
> I just expanded my /home partition again, and it dawned on me that I have a problem.  /home is on a partition of it's own, but I sense I screwed something up when I freshly installed 10.10.

See, the partition is set to mount at "/home", and that's it.
.........

There is - and can only ever be - one /home.

If you have changed the previous /home partition then the UUID will have changed. Update the fstab file to use the new UUID.

---

### Post by EMABrad on 2011-02-09
What do you mean if I "changed the previous /home partition"?  And how does the UUID change?

And I'm assuming the UUID is the "address" of the hard drive in the computer.  Is that correct?

---

### Post by mcduck on 2011-02-09
UUID is an unique identifier number given to any partition when it's formatted or edited. So it't snot really like an address to the hard drive, more like it's name, allowing it to be identified regrdless of what computer you plug it into.

You said you just expanded your /home partiiton. Taht means that it now has a new UUID, so you need to edit the /etc/fstab file so it has correct UUID for your home partition. Otherwise the system can't recognize the partition, it's still looking for one with the *old* UUID.

To list the UUID's for all your partitions you can run "blkid" in a terminal.

(what comes to having "brad" directory inside /home, that's how it's supposed to be. /home is not your user's personal home directory, it's where *every user's* home directories are located. So you are not supposed to be able to write into /home, only into /home/brad. And if you put /home on separate partitioon, all it's contents, including /home/brad, will be on that partition.)

---

### Post by coffeecat on 2011-02-09
> **EMABrad said:**
> See, the partition is set to mount at "/home", and that's it.  What this means is that I have all of the files and folders within the partition, but also it shows "brad", which is MY /home folder, which has my default download location and all of that in it.  I'd like to synchronize the whole situation a little better, because this means that I essentially have two "/home"s..  This problem wasn't urgent until I expanded the partition to add another 40GB onto it, and I'd like to put that memory to good use, but, unfortunately, I don't have write permissions to it by default.

If I'm reading you correctly, I think you are a little confused. If sda2 is your home partition (according to your fstab) and is mounted to the /home directory in your root partition sda5 (according to your fstab), then you should have nothing in sda2 apart from the brad folder for your account and any other folders for other accounts. All your files and folders should be inside the brad folder, not in the root (highest level directory) of the partition.

The reason you can't write directly to the partition is that it is owned by the root account, which is as it should be. That doesn't matter because the brad folder and all contents are owned by you, and you can write to the brad folder and any sub-folders.

What I don't understand from your account is that if your home partition is being mounted according to your fstab, then the only way of seeing what is in the partition is by navigating to /home in your filesystem. You should not write directly to /home whether it is a mounted partition or whether it is just a directory in the root partition when you don't have a separate home partition - only to /home/brad.

As far as blkid's are concerned, if you merely enlarged a ext3/4 partition, the blkid will not change. But if you created a new, larger partition for your home partition then that would have a new blkid. If you want to check the blkid's of your partitions, then use:

```
sudo blkid
```Perhaps you could post the output of that so that we can see if it corresponds to your fstab.

**EDIT**:

> **mcduck said:**
> You said you just expanded your /home partiiton. Taht means that it now has a new UUID

The several times I have resized an ext3/4 partition the blkid has not changed. Is there any circumstance when this might occur, apart from creating a new partition?

---

### Post by piquat on 2011-02-09
.

---

### Post by EMABrad on 2011-02-09
The UUID that returns from blkid is actually the same one that's in fstab.  If it changes every time the partition is formatted or edited, I guess it just edited fstab automatically.

See, the biggest problem, honestly, is that I'm pretty much strapped for space on this computer, so I need to make sure that, when something's downloaded or something along those lines, it's going into that separate partition, rather than the partition that my installation is on.

So does this mean that everything is actually in line?

And what about my inability to change the contents of /home?  Is that just a natural consequence of how everything's configured?  Can it be helped, or do I just have to move everything from /home into /home/brad?

---

### Post by EMABrad on 2011-02-09
I see.  Well, in that case, I guess I should just move the contents of /home into /home/brad while logged in as root.  This way, I have complete control over these files while not logged in as root.  Is that correct?

---

### Post by coffeecat on 2011-02-10
> **EMABrad said:**
> I see.  Well, in that case, I guess I should just move the contents of /home into /home/brad while logged in as root.  This way, I have complete control over these files while not logged in as root.  Is that correct?

I don't know. How did the files in /home get there in the first place? Who are they owned by, root or yourself? If you copy them as root you may emd up with files in /home/brad owned by root. And what do you mean 'logged in as root'? I hope you are not logging in to a GUI as root. That is a sure way of mangling your system if you are not 101% sure of what you are doing. The Ubuntu security model doesn't allow logging in as root - for a very good reason.

---

### Post by piquat on 2011-02-10
> **coffeecat said:**
> How did the files in /home get there in the first place?

I deleted a post up there and maybe I should have left it.

This question and the replies to the thread make me think he's done something you guys aren't getting, I could be wrong.

The way I take it:

He HAD a partition mounted in /home in an OLD INSTALL.  He reinstalled without telling the installer to mount the old home folder/partition so it created a new one... /home/brad.

Afterwards, he mounted this partition at home which spewed all the files in his old home partition all over the current /home.  Also in this /home is his /brad folder which is the REAL HOME CREATED BY THE INSTALLER.

Now he's wondering if he can take all those files that are strewn about in /home and move them to /home/brad.

Am I way off base on this OP?  If I am, sorry for the confusion.  Really trying to eliminate confusion here...

---

### Post by oldfred on 2011-02-10
If you need to reset permissions and ownership.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

---

### Post by EMABrad on 2011-02-10
That's kind of what I figured I should do.  Just move the stuff from /home into /home/brad (given that I'm the only user on the computer) and change the permissions so that I can access that without being root.  And, when I meant "logged into root", I meant using sudo.  Sorry.

But thanks for the help!

---


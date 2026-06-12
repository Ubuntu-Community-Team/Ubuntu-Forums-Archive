---
title: "Taking Ownership of New Partition"
date: 2010-02-10
forum: General Help
---

### Post by neu5eeCh on 2010-02-10
I've been trying to follow the instructions on a [previous thread]("http://ubuntuforums.org/showthread.php?t=563990") and am hesitating. I need just a little more help:

The previous writer gave instructions for editing fstab. He said to enter something like the following line in fstab:

/dev/hdb1 /media/harddrive ext3 defaults,errors=remount-ro,users,user_xattr,user 0 0

My partition is: /dev/sda7.
I created a folder in media: /media/8g
The file system is: ext2  (Do I need the "defults" instruction? What does this do?)
errors=remount-ro (I think I understand this)
users (Does this mean group?)
user_xattr (What does this do? Do I alter this?)
user (This is my own username?)
0 0 (Dump and Pass? Can these remain unchanged? What do these do?)

He also said, after this was all done, to enter the command: sudo mount /media/[my new partition]

Since it's already mounted? What does this command accomplish?

---

### Post by Claus7 on 2010-02-10
Hello,

where in the first place is that partition located?
If it is an external hdd the only thing you have to do is unmounting it and then changing the ownership to you, yet this has to do on how you did the partitioning in the first place.

A df -h command would be very helpful pointing which partition you want to change ownership and also the command: ls -l /media/  

In order to change the ownership of a partition you have to unmount it first (sudo umount - notice without n) and then change it by using the commands chgrp and chown. In order to use this disk you have to mount it anew (unplug it and plug it back).

Regards!

---

### Post by neu5eeCh on 2010-02-10
Thanks Claus. The partition is a logical partition. Just created it. 

I unmounted it. I created a directory in Media named 8g. I mounted the drive using [sudo mount /dev/hda7 /media/8g]. Then I changed the ownership of this directory [/media/8g] to my username and group. 

That last thing I'm trying to do is edit FSTAB so that the drive will be mounted automatically when I boot. I'm not sure what's necessary at this point. I [found some instructions]("https://help.ubuntu.com/community/InstallingANewHardDrive") that offer the following edit:

 /dev/sdb1    /media/mynewdrive   ext3    defaults     0        2

I can change 2 to 0, since I don't need to check the file system every time I mount it.

I suppose the last question is this: Can I leave the options as [default], or do I need to spell out ownership and permissions? (Like what was recommended in the first comment?) In other words, if I use the FSTAB edit immediately above, will that be enough to grant me read/write permissions (if I'm not logged in as supervisor or administrator).

---

### Post by Claus7 on 2010-02-10
Hello,

judging from the hd**a** this is the first hdd of your system. So reading this:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

what you should do is:
/dev/hda7 /media/8g ext3 defaults 0 0

would do the trick as:
defaults = rw, suid, dev, exec, auto, nouser, and async

rw= both read and write
auto= mounted automatically

Regards!

---

### Post by neu5eeCh on 2010-02-10
Thank you Claus! I've just been reading another site: 
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

I think it contains much the same information. My partition type is ext2. 

In your example, you use defaults. But according to my reading (and I may be wrong) defaults includes the [COLOR=Red]**nouser**[/COLOR] option. Wouldn't that prevent me from mounting the partition unless I was root? Shouldn't I modify the defaults command thusly:

/dev/sda7       /media/8g   ext2    [COLOR=DarkRed][COLOR=Black]defaults,errors=remount-ro,[/COLOR]**[COLOR=Red]user[/COLOR]**[/COLOR]    0     0 

This is how I've written it so far.

---

### Post by oldfred on 2010-02-10
this was my entry for my data directory. I had to create directories first.

# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

I mounted it this was so I would not see it in nautilus. I link to all the folders for access.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

### Post by neu5eeCh on 2010-02-10
I'm starting to get peeved.

I've changed permissions on the partition both via the command line *and* gui and Ubuntu **still** insists that only root can access it. What **don't** I get?

---

### Post by neu5eeCh on 2010-02-10
I rebooted with the following entry in FSTAB.

/dev/sda7       /media/8g   ext2 defaults,errors=remount-ro,users,user 0     0 

The partition was mounted on reboot, but I still had no ownership. I've come to a dead-end. I've followed all the instructions I could find in the forums (or at least I think I did) and nothing is working. I don't know what else to try unless someone helps?

**[EDIT: It works! It looks like I have to reassign permissions to each and every folder. Is there a way, as in windows, to apply cascading permissions?]**

---

### Post by Claus7 on 2010-02-10
Hello,

how about:
> /dev/sda7 /media/8g ext2 errors=remount-ro,users,user 0 0

Reboot and let us know.

If the thing you say is working then if you want to change permissions of the folders then you have to do:
e.g. change permission of folder test and its contents then I type chmod 755 ./test

edit: I would also try the option users,uid=1000,gid=100, which is clear that it will give permissions to a user with specific id

edit2: what I told you before is to remove defaults as that way the root has permissions on the mounting...

Regards!

PS: You are so close so avoid frustration!

---

### Post by neu5eeCh on 2010-02-10
Thanks Claus! It's working, although the drive now appears twice under the Gnome Menu Option Places. The first instance does nothing if I click on it. The second instance opens the partition in Nautilus. I'm not sure this is worth fussing over, but it may have something to do with the way I set up FSTAB?

Here is the "successful" edit of FSTAB :

/dev/sda7       /media/8g   ext2 defaults,errors=remount-ro,users,user 0     0    

I included "defaults" because, according to [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=283131"), users by itself "automatically implies noexec, nosuid,nodev unless overridden."

I'm not sure I'm right, but by including "defaults" first, my thought is that this will override the nodev, noexec options? But I don't know. I haven't tried executing anything from this partition and probably won't. However, I can Read & Write, so I think I've done *something* right.

**[**By the way, my initial confusion as to permissions was caused by the fact that I had initially copied files into the partition as **root**. So, no matter what permissions I assigned the partition, I still couldn't access the files contained therein (although I could at least open the partition and **Read/Write** the rest of it.)**]**

---


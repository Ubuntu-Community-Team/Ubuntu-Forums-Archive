---
title: "move my /usr directory help please."
date: 2010-06-16
forum: General Help
---

### Post by Cool Javelin on 2010-06-16
I have 2 hard disks, one is full and I would like to move my /usr directory from sda1 to sdb1.

I tried the following..

[B]sudo mkdir /driveb
sudo mount /sdb1 /driveb
cd /driveb
sudo mkdir /usr
sudo cp -b --copy-contents -r /usr /driveb/usr
sudo mv /usr /usr1
/usr1/bin/sudo mkdir /usr[/B]

at this point, I get a little lost:

**/usr1/bin/sudo mount /sdb1/usr /usr**
*mount: special device /sdb1/usr does not exist*

I don't fully understand the difference between a directory and a mount point and I may be treating them wrong.

I would like /usr to point to sdb.

is it possible, or should I try to change my path instead and ignore this problem?

Thanks for you help,
Mark.

---

### Post by yeleek on 2010-06-16
Tried this?
[http://ubuntuforums.org/showthread.php?t=235222](http://ubuntuforums.org/showthread.php?t=235222)

---

### Post by xifer on 2010-06-16
> **Cool Javelin said:**
> I have 2 hard disks, one is full and I would like to move my /usr directory from sda1 to sdb1.
[...]

at this point, I get a little lost:

**/usr1/bin/sudo mount /sdb1/usr /usr**
*mount: special device /sdb1/usr does not exist*

I don't fully understand the difference between a directory and a mount point and I may be treating them wrong.

I would like /usr to point to sdb.

Thanks for you help,
Mark.

You are nearly there.  First thing tho is you should be doing this in single user mode else running processes may have problems - so boot into the recovery console.  

you don't need to mount your new directory /sdb1/usr as the partition /sdb1 is already mounted.  Else you wouldn't have been able to copy /usr on there.
you don't need /usr1 either.  just run commands from /sdb1/usr
the last step you need is to delete the original /usr directory and create a symbolic link so programs can find your new location.  n.b. this uses recursive remove - WHICH CAN BE DANGEROUS SO BE VERY CAREFUL - 

```

rm -r /usr
ln -s /usr /sdb1/usr


```

---

### Post by delcypher on 2010-06-16
A mount point is a folder you choose to mount a filesystem in.

In your commands it should be /dev/sdb1 NOT /sdb1.

Make sure the drive you're moving sdb1 to supports unix file permissions. Your cp command should really be

```
cp -pr /usr /driveb/usr
```

so that you preserve file permissions and timestamps.

Your last command ```
/usr1/bin/sudo mount /sdb1/usr /usr
```

does not make any sense because you cannot access the internal folders of a block device (in this case /dev/sdb1) without mounting it.

Assuming that /dev/sdb1 is correctly mounted at /driveb then you can use something called bind mounts to mount part of a filesystem somewhere else. You can do this using the following command.

```
sudo mount --bind /driveb/usr /usr
```

To achieve what you want here is the general sequence of commands that I would run.
```

sudo -i # now we're root
cd / #make sure we're in the root directory
mkdir /driveb
mount /dev/sdb1 /driveb #mount device /dev/sdb1 at mount point /driveb
cp -pr /usr /driveb #recursively copy /usr into /driveb
PATH=$PATH:/driveb/usr #add the copy of /usr to path to make typing commands easier for now.
fuser -vm /usr #This will show you what is using /usr directory, be aware that some of these running applications may cause the move to fail. I advise doing the move in recovery mode.
mv /usr /usr.old #move the old /usr directory to a temporary location
mount --bind /driveb/usr /usr #bind mount the usr folder in /driveb to mount point /usr
rm -rf /usr-old #remove the old /usr-old directory

```

You'll want to add the /driveb/ mount and then the bind mount to your /etc/fstab so your system works when you reboot. You'd add something like this:
```

/dev/sdb1 /driveb ext3 defaults 0 0
/driveb/usr /usr none bind 0 0

```

Hope this helps.

---

### Post by Cool Javelin on 2010-06-17
Thanks for all the help, this is a wonderful community.

In order of replies,
----------------
yeleek, Thanks for the link, I did go look and while it looked like it might do what I wanted, it seems a little incomplete.
----------------
xifer, Great point on going to single user mode, I totally forgot about that. My guess is it would be OK not to as there would be only a very short time between me renaming the /usr directory (to a backup) and mounting the new one, but still, better safe then sorry.

for now (in case I totally hose this) I copied the files to /driveb/usr then simply renamed my old /usr to /usr1 (I like delcypher's idea (below) and should have used /usr.old)

I guess my cp command was wrong too.

When it is all working, I will remove the original /usr (now /usr1) directory as the intent is to free up disk space.

I see you choose to use ln to make a link to the new place. How will this play out during automatically mounting the file systems during boot?

I made a mistake in my original post and called the new dir /sdb1/usr, but I think it is really called /driveb/usr, and I need to make an entry in my fstab to mount the /dev/sdb1 on /driveb

As soon as I changed the name (since the new directory wasn't mounted yet) sudo quit working as it is in /usr/bin. I had to force a manual path to there as I needed it. (I guess I could have temporally added /usr1/bin manually to the path.)


--------------
delcypher: This is a great instruction. I'm sure it took more then just a few minutes to do this, thanks for taking your time.

This all worked as advertised, and I also added to my /etc/fstab:

```

UUID=BunchOfHexStuff   /driveb   ext2   noatime,relatime 0 2
/driveb/usr   /usr     auto   --bind 0  0
```

and OMG, it worked.

[COLOR="Red"]EDIT: OK, so it didn't work as well as I liked.
When I reboot, /driveb gets mounted, but /usr doesn't. I will play with it a little to try to make it automatic.
[/COLOR]

One question about performance now.

Since I have the file system mounted as /driveb, then another line binding /usr to /driveb/usr, when I refer to /usr is it now a 2 step process for Linux?

WIll this impact performance? (my guess is it won't be noticable, but theoritical.)

Is there a way to mount sdb1/driveb/usr to /usr directly in one step to eliminate the indirect step for the system?

Thanks lots.
Mark.

---

### Post by xifer on 2010-06-19
> **Cool Javelin said:**
> Thanks for all the help, this is a wonderful community.

In order of replies,

I see you choose to use ln to make a link to the new place. How will this play out during automatically mounting the file systems during boot?


The kernel will mount all the filesystems available before anything else needs to access /usr.  

> 
When I reboot, /driveb gets mounted, but /usr doesn't. I will play with it a little to try to make it automatic.


I think you need an extra script to run the mount --bind command probably in the run level directory /etc/rc3.d but i may be wrong

> 
One question about performance now.

Since I have the file system mounted as /driveb, then another line binding /usr to /driveb/usr, when I refer to /usr is it now a 2 step process for Linux?

WIll this impact performance? (my guess is it won't be noticable, but theoritical.)

Is there a way to mount sdb1/driveb/usr to /usr directly in one step to eliminate the indirect step for the system?

Thanks lots.
Mark.

Not a 2 step system, but bind mount works much like a symbolic link with no performance impact.

What you could have done was split your disk and create a disk partition for /usr only and not have to worry about links and bind mounts.  Might make backup strategy etc simpler.

---

### Post by Cool Javelin on 2010-06-21
OK, I solved the problem by changing my thinking a little.

I created 2 partitions on my sdb drive and did the following (this is from memory and may be imperfect. Also, use sudo when necessary. Also did in single user mode.)

```
mkdir /driveb
mkdir /scratch
mount /dev/sdb1 /driveb
mount /dev/sdb2 /scratch
cp -pr /usr/*.* /driveb    #this put all my /usr stuff in the topmost directory, not under driveb like /driveb/usr
mv /usr /usr.old
(changed my fstab to have the following...)
UUID=BunchOfHexStuff   /usr   ext2   noatime,relatime 0 2
UUID=BunchMoreHexStuff   /scratch ext2 noatime,relatime 0 2
reboot
rm -fr /usr.old

```

It works great, thanks for all your help.

Mark.

---

### Post by xifer on 2010-06-21
glad you got it sorted.  But just to throw a cat among the pigeons - why are you using ext2 filesystems and not ext4 on new partitions?

---

### Post by Cool Javelin on 2010-06-21
Speed, xifer, mostly.

I read somewhere ext3 has a little more overhead, and I didn't know about ext4 until you mentioned it. I can only assume it is even less efficient still.

They may have some features I don't, but the machine I am using is VERY slooooowwwww and ext2 works for me. I have even gone to the extent to turn off some system logging to help with performance.

Thx.

---


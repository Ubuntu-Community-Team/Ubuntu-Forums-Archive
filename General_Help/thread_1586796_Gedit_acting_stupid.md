---
title: "Gedit acting stupid"
date: 2010-10-02
forum: General Help
---

### Post by Donnie Love on 2010-10-02
I'm having a problem with Gedit
I keep getting this message:
 
"The file [filename] changed on disk."
 
Why does it keep saying this? And the everytime I save a document I get this:
 
"The file [filename] has been modified since reading it."
 
Why does it keep doing that and how can I make it stop?
 
Thanks. :0>

---

### Post by lisati on 2010-10-02
That error message usually happens when another program or process makes changes to a file while you have it open with gedit.

---

### Post by Donnie Love on 2010-10-02
Nothing else is using the files. How do I make it stop doing that?

---

### Post by WorMzy on 2010-10-02
Something must be. It only displays that message if the "last modified" datestamp on the file changes to something other than what it was when the file was last read by gedit.

Unless you have a defective installation of gedit (in which case reinstalling it may help), there's nothing you can do about it. Post a bug report on launchpad about it.

---

### Post by Donnie Love on 2010-10-02
Possibly the file browser? Could it be interfering with it?

---

### Post by WorMzy on 2010-10-02
I doubt it, I've never seen nautilus modify files before.

Does it happen for every file, or just a few specific ones?

---

### Post by Donnie Love on 2010-10-04
All of them I think.

---

### Post by WorMzy on 2010-10-04
Which filesystem is your partition formatted as?

---

### Post by Crazedpsyc on 2010-10-04
try running the following:
```

lsof | grep [I]yourfile
[/I]
```where yourfile is the name of your file of course

EDIT: Actually, that probably wont help, sorry

---

### Post by Donnie Love on 2010-10-27
> **WorMzy said:**
> Post a bug report on launchpad about it.
 
Forgive my ignorance, but I don't know how to do that. I don't know what "launchpad" is.
 
> **WorMzy said:**
> Which filesystem is your partition formatted as?
 
Umm... :-s I don't know what that means either. Sorry, I'm not a tech guy.
 
I use a few different computers. Mine at home is Ubuntu, the ones at work and school are Windows, but I use gedit on all three, and all versions are doing the same thing. (It just started recently, in fact.) It's becoming tiresome, not to mention cutting into my productivity to have to click "Cancel" and "Save Anyway" every time I want to save my work, and I save often.

---

### Post by WorMzy on 2010-10-27
Launchpad is a place where you can report bugs (amongst other things), gedit's launchpad page is here: [https://bugs.launchpad.net/ubuntu/+source/gedit](https://bugs.launchpad.net/ubuntu/+source/gedit)

You can report the bug by clicking the "report a bug" link near the top right of the page.


If you don't know what filesystem you're using, open a terminal and run
```
mount
```

It'll give you a list of all the mounted filesystems and their type, like this:
```
proc on /proc type **proc** (rw,relatime)
sys on /sys type **sysfs** (rw,relatime)
udev on /dev type **devtmpfs** (rw,nosuid,relatime,size=10240k,nr_inodes=215952,mode=755)
/dev/sdc9 on / type **ext4** (rw,commit=0)
devpts on /dev/pts type **devpts** (rw)
shm on /dev/shm type **tmpfs** (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type **fusectl** (rw)
/dev/sda1 on /media/Terastore type **fuseblk** (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
gvfs-fuse-daemon on /home/wormzy/.gvfs type **fuse.gvfs-fuse-daemon** (rw,nosuid,nodev,user=wormzy)
/dev/sdb5 on /media/Work type **ext3** (rw,nosuid,nodev,uhelper=udisks)

```

---

### Post by Donnie Love on 2010-10-27
Cool, thanks.

---


---
title: "Having a problem controlling a partition"
date: 2011-01-09
forum: General Help
---

### Post by CP2 on 2011-01-09
I created a partition with Gparted. Problem is I can't do anything inside of it. It says I don't have permissions. The owner is root. So I do a few commands to try and get me access to it.  

sudo chown -R 777 /dev/sda9

sudo chmod -R 777 /dev/sda9

sudo chown u+w /dev/sda9

And I don't get an error back, but none of them seem to work. So can any of you help me get access to this partition?  I have formatted it again and I still don't have access. I'm sure it has nothing to do witht he TYPE of filesystem I used right?  I used Ext3.

---

### Post by lithopsian on 2011-01-09
Is it mounted?

---

### Post by perspectoff on 2011-01-09
Nowadays you can work with partitions (including owners and permissions) easily using Nautilus (in Ubuntu) or Dolphin (in Kubuntu).

You can work as root by starting one of the two file managers:

 sudo nautilus

or

 sudo dolphin

This allows you to mount and unmount partitions easily, examine the ownership and permissions, and change them as needed, all from the GUI.

It will save a lot of time and stress over learning all the command lines to accomplish the same things.

---

### Post by dino99 on 2011-01-09
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Verbeck on 2011-01-09
mount /dev/sda9 and run
```
sudo chown -R $USER:$USER **/path/to/mountoint**
```

(replace /path/to/mountoint with where you mounted it)

---

### Post by CP2 on 2011-01-09
> **perspectoff said:**
> Nowadays you can work with partitions (including owners and permissions) easily using Nautilus (in Ubuntu) or Dolphin (in Kubuntu).

You can work as root by starting one of the two file managers:

 sudo nautilus

or

 sudo dolphin

This allows you to mount and unmount partitions easily, examine the ownership and permissions, and change them as needed, all from the GUI.

It will save a lot of time and stress over learning all the command lines to accomplish the same things.

The sudo nautilus worked for me. Thanks. Didn't know that that program was.

---

### Post by srs5694 on 2011-01-09
A caution about "sudo nautilus" and similar commands to run nautilus as root: If you start using the file manager in this way, you're likely to end up with an increasing number of files in your home directory, or in other directories you should be accessing as a normal user, owned as root. This will create more need to use this workaround (if it's the only one you know), which will spiral out of control. This is bad because you should not be doing anything as root that's not absolutely necessary. The Linux root user has extraordinary power, and many Linux programs' safety and security features are built on the assumption that they will *not* be run as root most of the time. Thus, you can easily get yourself into real trouble by running nautilus as root.

Another problem with doing this is that if you move files to the trash as root using nautilus, those files will end up in root's trash can, so you won't know that they're still on the disk and consuming space from your own desktop. If you "delete" very many or very big files in this way, you can therefore end up running out of disk space and not know why. This problem is easily corrected, but it can be perplexing.

Of course, if you *only* use nautilus to check and change permissions of files or mount points, as perspectoff recommended, it's not so dangerous. Even so, knowing the command-line command, as Verbeck suggested, and running it alone as root poses less risk of accidentally doing something wrong.

In sum, I strongly advise against running nautilus as root except under very limited conditions. Instead, do as Verbeck suggested, and if that doesn't have the desired effect, post back with more details.

In Linux, it's almost always better to learn what's going on than to rely on the quick fix that you don't understand. Quick fixes that you don't understand can work, but they often lead to problems down the road.

One more point: You should almost never change the partition device IDs' (/dev/sda*) permissions. There are ways to mount and unmount these partitions as a normal user, and the GNOME desktop environment normally does this automatically. Chances are your problem was with permissions at the filesystem level, meaning that the proper solution is likely to be what Verbeck suggested. The changes to the permissions you implemented will be undone when you reboot next, so I recommend doing so soon if you haven't done so already, just to be on the safe side.

---

### Post by CP2 on 2011-01-09
Wow, thanks for the heads up on this srs5694. I'll be sure to use Nautilus in a limited fashion.

---


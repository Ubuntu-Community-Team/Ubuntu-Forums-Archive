---
title: "Those annoying file system checks"
date: 2010-05-19
forum: General Help
---

### Post by Redsandro on 2010-05-19
Hi, 

I have my Media Center running Ubuntu 10.04, and it's annoying to have that *"Your disk drives are being checked for errors"* message every so often. And ofcourse, as Murphy's law states, it usually happens when I'm in a hurry to quickly watch something. :P

Ofcourse, I can press 'C' (cancel) all the time. But I guess Ubuntu set up this file check interval for a reason, right?

I was wondering if it's save to change the interval so it's less often. Or is it easy to configure the check to occur at SHUTDOWN? That's when most people don't care what the computer does anymore.

Also, although it's a pretty fresh install, any Ubuntu on my machine has never ever ever ever worked flawlessly and neither does this one. More often then not, on shutdown, the computer doesn't shut down but just sits there with a black screen or with the ubuntu logo. So I just power it off. Does this scenario make it unwise to tone down on the number of file checks?

---

### Post by blazemore on 2010-05-19
If you want to FORCE no checks, edit your /etc/fstab file
```
sudo gedit /etc/fstab
```

At the end of each line where it says 0 1  or 0 2, change the last digit to a 0. Save and close

---

### Post by philinux on 2010-05-19
sudo tune2fs -l /dev/sdXX
Show current setup

sudo tune2fs -c 50 /dev/sdXX
Changes it to every 50 boots. You can use a timescale like monthly, see man page

sudo touch /forcefsck

---

### Post by leneflower on 2010-05-19
also, tune2fs is your friend:
[FONT=Courier New]tune2fs -i *interval-between-checks*[/FONT] lets you specify the number of days between two checks.
[FONT=Courier New]tune2fs -c *max-mount-counts*[/FONT] lets you specify how often to mount between checks.

---

### Post by blazemore on 2010-05-19
> **philinux said:**
> sudo tune2fs -l /dev/sdXX
Show current setup

sudo tune2fs -c 50 /dev/sdXX
Changes it to every 50 boots. You can use a timescale like monthly, see man page

sudo touch /forcefsck

Do this one; not mine.

---

### Post by srs5694 on 2010-05-19
The philosophy behind the periodic forced checks is that problems can creep in slowly and unnoticed. The forced checks are a feature of the ext2/3/4 filesystems; they aren't enforced on other Linux filesystems. (I'm not sure about Btrfs, though.) Thus, a more radical option to get rid of the forced checks is to switch to ReiserFS, XFS, or JFS. This might be practical on a new install or when you're copying the system to a new hard disk, but such a change would be extremely awkward when you have no such plans, since you'd need to back up, create a new filesystem, and restore.

---

### Post by Zill on 2010-05-19
> **srs5694 said:**
> The philosophy behind the periodic forced checks is that problems can creep in slowly and unnoticed. The forced checks are a feature of the ext2/3/4 filesystems; they aren't enforced on other Linux filesystems. (I'm not sure about Btrfs, though.) Thus, a more radical option to get rid of the forced checks is to switch to ReiserFS, XFS, or JFS. This might be practical on a new install or when you're copying the system to a new hard disk, but such a change would be extremely awkward when you have no such plans, since you'd need to back up, create a new filesystem, and restore.
+1 for ReiserFS - It has been a rock-solid filesystem for me for several years with no forced checks and *no* cryptic error messages or mysterious "lost&found" files - it just works. :-)

---

### Post by John Bean on 2010-05-19
At least the check takes a sensible amount of time since the recent updates. It now takes only as many seconds as it did minutes with the original release of Lucid.

---

### Post by Redsandro on 2010-05-24
Thanks! I forgot to subscribe, so I thought no one replied yet.

So if I get this correctly, there are two intervals for checks working at the same time:

After x days
After y mounts

I think/hope I can safely crank them up a little bit but not too far.

Since ext is the default system choice and many other tools (in other OSses) support it, I'm not ready to move to something different like ReiserFS. I'm used to a motorcycle, don't want to change to a car. :P

---

### Post by CharlesA on 2010-05-24
I just set mine to check every 30 days. I don't think it records how many times it has been mounted.

---

### Post by jerome1232 on 2010-05-24
I was going to be helpful but since you've been helped I'll be incredibly unhelpful and tell you to stop rebooting so much. :P

---


---
title: "Help! Hard Drive mounts read-only! Can't write to it."
date: 2009-10-14
forum: General Help
---

### Post by bobdobbs on 2009-10-14
Hi guys. I'm in a real fix.

My main drive, which includes the root partition is mounting read only.
I can't seem to do anything about it.

Now, just about every time it boots, I have to manually run fsck. And, if it passes that and starts up, then I can't do anything, because I can't write to the drive.


What can I do about this?
(I'm in a bit of a tizz over this. This is a major disruption, and I don't know what to do)

---

### Post by scouser73 on 2009-10-14
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by StuartN on 2009-10-14
> **bobdobbs said:**
> What can I do about this?

If you look at /etc/fstab there should be **errors=remount-ro** as an option on your hard drive, meaning remount read-only if there is an error. (Do not alter this setting). If a hardware disk error has forced a read-only remount, then you need to run fsck to clear the error status.

You could force a filesystem check at the next reboot with
```
sudo touch /forcefsck
```
or immediately with
```
sudo shutdown -rF now
```

---

### Post by Bucky Ball on 2009-10-14
> **scouser73 said:**
> **1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

+1

Couldn't have said it better myself. ;-)

---

### Post by bobdobbs on 2009-10-21
> **StuartN said:**
> If you look at /etc/fstab there should be **errors=remount-ro** as an option on your hard drive, meaning remount read-only if there is an error. (Do not alter this setting). If a hardware disk error has forced a read-only remount, then you need to run fsck to clear the error status.


The drive has been consistently passing fsck checks without having errors, and yet still failing to mount as writable.

My solution in the end was to remove the read-only option.

I fear that if I change back, then I won't be able to use the drive.

---

### Post by falconindy on 2009-10-21
If there are errors on the drive causing it to mount as r/o, mounting it as r/w may only exacerbate the issue.

When you run fsck, does a full check of the drive occur? How are you executing it?

Personally, I'd make an image of the drive before doing anything else.

---


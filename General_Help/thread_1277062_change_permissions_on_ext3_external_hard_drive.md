---
title: "change permissions on ext3 external hard drive"
date: 2009-09-27
forum: General Help
---

### Post by pythonscript on 2009-09-27
I just bought a 1 TB WD external hard drive, and because I'm going to be using it exclusively with my Linux systems, I formatted it as ext3. However, I can't write to it. I don't want it mounted automatically, because I'm using it as a removable usb drive. 

It mounts automatically, but I can only write to it as root. How can I change its file permissions to allow all users to write to it? I don't want to have to use "gksudo nautilus" every time; that's a pain and a security risk I don't want to make. Thanks!

---

### Post by skatinjj on 2009-09-27
[this]("http://www.linfo.org/etc_fstab.html") is about the file fstab which you can use to do what you want

[this]("https://help.ubuntu.com/community/FilePermissions") is an article all about permissons

---

### Post by pythonscript on 2009-09-27
> **skatinjj said:**
> [this]("http://www.linfo.org/etc_fstab.html") is about the file fstab which you can use to do what you want

Will /etc/fstab allow me to automatically mount the drive for all users *but not at boot time?* This drive will never be attached to my computer at boot, and according to the first article

> Filesystems that are described in /etc/fstab are typically mounted when the computer is booted...

---

### Post by Diabolis on 2009-09-27
No worries, if you have a fstab entry and the HD is not connected it will just pass it and keep going through the other lines. However, you can add the **noauto** option to the entry so it won't try to mount the drive at boot up.

---

### Post by pythonscript on 2009-09-28
I added this to /etc/fstab

```
UUID="d1afc604-9bc4-4aa5-a085-27a2367b350c /media/MyBook noauto,rw,user,relatime    0    2
```

but when I insert the drive, I still can only write to it as sudo. How can I change this? I can't run gksudo nautilus *every time I want to write to the device*. Thanks!

---

### Post by pythonscript on 2009-09-28
Can anyone help me with this?! I'm desperate to get this working so I can actually back up data to this drive! I changed my /etc/fstab to this:

> UUID="d1afc604-9bc4-4aa5-a085-27a2367b350c /media/MyBook ext3 auto,rw,user,relatime    0    2I didn't want to use auto, because the drive won't be attached to my computer on boot, but I really need help getting this to work! I have an external NTFS hard drive that works fine, without any /etc/fstab configuration. I would have thought the Linux file system would work better *with Linux* than the Microsoft file system.

When I execute ```
sudo mount -a
``` I get the error message > mount: special device UUID="d1afc604-9bc4-4aa5-a085-27a2367b350c does not exist


I'd really appreciate any help! I need to get this working!

---

### Post by Diabolis on 2009-09-28
> **pythonscript said:**
> 
but when I insert the drive, I still can only write to it as sudo. How can I change this? I can't run gksudo nautilus *every time I want to write to the device*. Thanks!

You have to change the permissions of the mount point, /media/MyBook, with the **chmod** command.

If its not going to be always attached, then don't write a fstab entry. Just plug and unplug as if it were a small USB flash drive and it should be auto-detected and auto-mounted.

---

### Post by pythonscript on 2009-09-28
> **Diabolis said:**
> You have to change the permissions of the mount point, /media/MyBook, with the **chmod** command.

If its not going to be always attached, then don't write a fstab entry. Just plug and unplug as if it were a small USB flash drive and it should be auto-detected and auto-mounted.

Ok, I ran

```
sudo chmod 777 /media/MyBook/
```

but now when I insert the drive, it doesn't even show up on the desktop. What's happening here? Did I apply the wrong permissions?

---

### Post by pythonscript on 2009-09-28
The drive won't mount automatically in ubuntu anymore! Can anyone please tell me how I can fix this?

---

### Post by Diabolis on 2009-09-28
List the contents of the foler like this:
```
ls -l /media/MyBook
```
To verify that is not mounted and that the permissions are right.

---

### Post by scouser73 on 2009-09-29
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

[COLOR="Red"]_**Change Hard Drive Permissions**_[/COLOR]

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by pythonscript on 2009-09-29
scouser73, that worked perfectly. Thank you so much!

---

### Post by evilbuntu on 2009-11-18
okay i found this thread in search for my problem.....

I tried chmod and right clicking as root but everytime I change the permissions in the menu (GUI menu) they stick for about 5 seconds then go right back to default.

problem is with my ftp. I have permissions to enter my external but my ftp users cant which stink because this is where i store all my files


thanks in advance

---

### Post by pythonscript on 2009-11-18
You're having a different problem; please post a new thread. Don't post your question on a thread dealing with an (in essence) unrelated problem.

---

### Post by evilbuntu on 2009-11-18
okay my fault, i may have made it look like something else. the problem is with my external hard drive. I cant set any permissions on it.

it just so ironically happens that my external is my ftp share. I narrowed it down to be something of what this thread is speaking of, setting the permissions on the drive.

I have in fact posted 3 threads on the topic, which have had MANY views but no replies.

you guys seemed to know a bit more about permissions than I so i thought in hopes one of you might have a bit of advice, but I found another reason for the problem i may have with my external, so after work i am going to try it and hope for the best. wasn't high jacking a thread, just looking for answers.

---

### Post by pythonscript on 2009-11-19
Then what do you mean about them "sticking for a few seconds?" It sounds stupid, but are you clicking Apply Permissions to Enclosed Files? Also, make sure that however you're mounting the drive, you're not mounting it as root-only. For example, if you're going to be mounting it every time you boot (as in, the drive is permanently connected) you could just add a line to /etc/fstab.

---


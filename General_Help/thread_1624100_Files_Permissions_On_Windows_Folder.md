---
title: "Files Permissions On Windows Folder"
date: 2010-11-17
forum: General Help
---

### Post by demonboy on 2010-11-17
Hi,

I've just read that I can't change the file permissions of files and folders if they are sitting in what was my old Windows D:\ drive. Is this correct? If so what is the work-around?

My problem is lack of space. I don't want to have to cut and paste that entire D:\ drive's contents over to a recognised Ubuntu folder. I had in my mind that this D drive would continue to be my data dumping ground, to which I need read/write access to.

Any pointers?

---

### Post by Lancro on 2010-11-17
Install the NTFS configuration tool (ntfs-config), from the repositories, and config it so you can write it.

---

### Post by sikander3786 on 2010-11-17
Did you mount the drive in fstab?

You can use the NTFS config tool as mentioned in above post to automate the process.

Or post the output of,

```
cat /etc/fstab
```

```
sudo blkid
```

---

### Post by oldfred on 2010-11-17
Some more info:

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by demonboy on 2010-11-17
OK, sounds easy enough. Turns out I have NTFS Configuration Tool already installed, but where the hell do I find it in my menu? Does it have a GUI? Is this the same as Configuration Editor in Applications/System Tools?

Thanks for that link, Oldfred. That's a very useful step-by-step guide.

---

### Post by sikander3786 on 2010-11-17
It should be under System > Administraion > NTFS-Config Tool.

---

### Post by demonboy on 2010-11-17
OK I hadn't installed it - at least it didn't look like I had. I thought I had so I installed it again and it now appears in my menu. However when I click it a tab on the bottom flashes "Starting Administrativ..." and then disappears. Is there a GUI or do I now have to put something in Terminal?

---

### Post by sikander3786 on 2010-11-17
> **demonboy said:**
> OK I hadn't installed it - at least it didn't look like I had. I thought I had so I installed it again and it now appears in my menu. However when I click it a tab on the bottom flashes "Starting Administrativ..." and then disappears. Is there a GUI or do I now have to put something in Terminal?
Are you running 10.10? It doesn't seem to open on my Maverick as well and I haven't tried to solve it as I don't need it.

---

### Post by demonboy on 2010-11-17
Yep, 10.10.

Looks like I'll be following oldfred's guide instead then. Thanks for the help and links.

---


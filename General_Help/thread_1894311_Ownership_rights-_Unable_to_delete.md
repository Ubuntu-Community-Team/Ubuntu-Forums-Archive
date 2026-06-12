---
title: "Ownership rights- Unable to delete"
date: 2011-12-12
forum: General Help
---

### Post by raghav.venky on 2011-12-12
I have a partition with NTFS system. It does not have any operating system, just data. 
The problem is i'm not able to delete or cut any file in that drive using Ubuntu. I am able to copy. How should I get the ownership?

---

### Post by spiky001 on 2011-12-12
Have you tried ```
sudo rm -v /what/ever/file
```

---

### Post by raghav.venky on 2011-12-12
Cannot delete : Read-only file system

---

### Post by spiky001 on 2011-12-12
why not chown the dir and then chmod permissions

---

### Post by WorMzy on 2011-12-12
You can't chown anything on an NTFS partition, NTFS doesn't support UNIX file permissions.

Sounds to me like you don't have ntfs-3g installed. Install it with:

```
sudo apt-get install ntfs-3g
```

Then unmount and remount the filesystem using udisks or a file manager.

---

### Post by raghav.venky on 2011-12-12
Noob here :D
Please explain.

---

### Post by WorMzy on 2011-12-12
What didn't you understand?

---

### Post by spiky001 on 2011-12-12
sorry follow WorMzy post to install nt-fs - 3g

---

### Post by raghav.venky on 2011-12-12
it says already installed

---

### Post by WorMzy on 2011-12-12
Okay, how did you mount the filesystem?

---

### Post by raghav.venky on 2011-12-12
I used PYSDM to automatically mount it. But then it had some problems so I uninstalled it. But the partition still mounts automatically.

---

### Post by WorMzy on 2011-12-12
Never heard of it. Chances are it made changes to your /etc/fstab file though. Can you post the contents of that file here, surrounding the output with [CODE[COLOR="Black"]][[/COLOR]/CODE] tags, please.

---

### Post by raghav.venky on 2011-12-12
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid         0  0  
# / was on /dev/sda3 during installation
UUID=878d4eba-b09d-4c69-b06d-5c162b20b280  /            ext4  errors=remount-ro           0  1  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,ro,umask=000  0  0  

```

---

### Post by WorMzy on 2011-12-12
> **raghav.venky said:**
> ```
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,ro,umask=000  0  0  

```

There's your problem. Remove that line from the file.

```
gksudo gedit /etc/fstab
```

Don't change anything else though.

---

### Post by raghav.venky on 2011-12-13
Are you sure that deleting the last line is not risky?
I'm just asking because I read that fstab must be carefully handled.

---

### Post by mcduck on 2011-12-13
> **raghav.venky said:**
> Are you sure that deleting the last line is not risky?
I'm just asking because I read that fstab must be carefully handled.

No, it's not risky. But if you want to play it safe you can of course make a backup of the current file, or instead of removing that line just comment it out by adding a # to the beginning of the line.

Anyway, your problems is indeed in that line, it's setting the partition to mount as read-only (which prevents even root user from writing to it).

You could alternatively try keeping the line in fstab, but remowing the "ro" from the options.

---

### Post by raghav.venky on 2011-12-13
I changed the settings to 'defaults' and it solved the problem. Thanks!

---


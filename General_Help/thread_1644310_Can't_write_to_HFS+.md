---
title: "Can't write to HFS+"
date: 2010-12-13
forum: General Help
---

### Post by Ryupower on 2010-12-13
First of all: 
yes, I did some research. But still, it doesn't work.

I'm trying to get write access to my HFS+ Mac partition. I tried getting the partition to give me permission, but I'm not an expert at chmod. Here's what I did:

```

@ubuntu:~$ chmod a+rwx '/media/Macintosh HD'
chmod: changing permissions of `/media/Macintosh HD': Read-only file system
```

Still doesn't want to read or write even with root access.

---

### Post by nothingspecial on 2010-12-13
You have to disable journaling to get linux to mount hfs+ read write.

---

### Post by Ryupower on 2010-12-13
is there any way to get rid of the linux journaling thing via ubuntu? (I've been looking for the mac os x CD with no avail, and I'm using rEFIt.)

---


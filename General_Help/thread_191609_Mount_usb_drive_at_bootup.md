---
title: "Mount usb drive at bootup"
date: 2006-06-07
forum: General Help
---

### Post by michaeljb2005 on 2006-06-07
I know how to edit fstab to mount drives at startup but I was wondering if someone might give me the appropriate line to add to fstab to mount sdb5 (a usb mass storage drive) to home/mike/storage.  The way I would do it would be:

/dev/sdb5       /home/mike/storage          ext3    defaults        0       2

Does that look correct?

---

### Post by mlind on 2006-06-07
What is the filesystem of USB drive ? is it ext3?

I'd create a new mount point on /media (or /mnt), say /media/storage
and add a fstab entry

```

/dev/sdb5       /media/storage     ext3    defaults      0    2

```

for ntfs share Ubuntu installer seem to have created entry
```

/dev/hda5       /media/share     ntfs    ro,nls=utf8,umask=007,gid=46 0       1

```

---

### Post by michaeljb2005 on 2006-06-07
[QUOTE=mlind]What is the filesystem of USB drive ? is it ext3?

I'd create a new mount point on /media (or /mnt), say /media/storage
and add a fstab entry

```

/dev/sdb5       /media/storage     ext3    defaults      0    2

```

for ntfs share Ubuntu installer seem to have created entry
```

/dev/hda5       /media/share     ntfs    ro,nls=utf8,umask=007,gid=46 0       1

```[/QUOTE]

yes it's ext3, I have a specific preference to have to it mounted to the directory I specified.  Thanks for the advice :).

PS if I do mount it to /media/storage how do I make it writable for a user?

edit:  I figured it out.  Thanks.

---


---
title: "Looking for some programs..."
date: 2011-02-18
forum: General Help
---

### Post by LinUxaliVe on 2011-02-18
Hello.

There was a simple mounting program I used to use in a Linux, and It had a tiny gui. Only one partition at a time was shown in the center, and it had left/right arrows on both sides of the listed partition. It used a green/red scheme to show whether the drive was mounted.

Anyone know the name of the program?

Also, is there some type of program that would let me create a temporary ram drive ***after boot***?

I need to siphon off about 512MB/1GB, and create a temp drive formatted as ext3/ext4.

---

### Post by Asmodai on 2011-02-18
As for creating a ramdisk, I just use the following:
```
mkdir /tmp/ramdisk
sudo mount -t tmpfs -o size=900M tmpfs /tmp/ramdisk
```

---


---
title: "Grub prompt at startup"
date: 2010-09-09
forum: General Help
---

### Post by stevedes on 2010-09-09
I use wubi 10.04 installed on my xp drive. the other day my pc froze while surfing the internet. I used the following key [combination]("http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html")
to reboot my pc (this is the first time I'm trying it), but when I selected ubuntu, I don't get the grub boot menu, on the other hand, I get a little welcome message to the grub prompt and "grub>"
How do I fix this and boot into Ubuntu?

---

### Post by bcbc on 2010-09-09
You could try booting from a live CD, and mounting the root.disk or running fsck on it if it won't mount. If the worst comes to the worst you can extract all your data from it as well. See [here]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?").

It's also usually possible to manually boot a wubi install from a grub prompt (not the grub rescue prompt).
To do this you need to know what partition the root.disk is on.
If you don't have a cd and want to try this, post back the results of 
"ls" (small LS)
and for each output of the above (excluding the (hdX) format)
"ls (hdX,Y)/ubuntu/"

---

### Post by stevedes on 2010-09-10
```
grub> ls
(hd0) (hd0,1) (hd0,5)  (fd0)

```
for

```
grub> ls (hd0,1)/ubuntu/
```
I got the directory listing for my C:\Ubuntu directory
so I guess its located at (hd0,1).

---

### Post by bcbc on 2010-09-10
> **stevedes said:**
> ```
grub> ls
(hd0) (hd0,1) (hd0,5)  (fd0)

```
for

```
grub> ls (hd0,1)/ubuntu/
```
I got the directory listing for my C:\Ubuntu directory
so I guess its located at (hd0,1).

You could try:
```
configfile (hd0,1)/ubuntu/winboot/wubildr.cfg
```

If that fails, to manually boot wubi from grub prompt:
```
set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

If they both fail then you'll need a live CD to try and loop mount and/or fsck your root.disk and confirm that it's still good. At that point there may be some other things to try or perhaps just recover important data.

---

### Post by stevedes on 2010-09-11
Both fail.

for
```
grub> loopback loop0 /ubuntu/disks/root.disk
error: fixup signature not match
```So I booted into my 10.04 livecd
```

ubuntu@ubuntu:~$ sudo fsck /media/EA7C486A7C48341B/ubuntu/disks/root.disk 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Input/output error while trying to open /media/EA7C486A7C48341B/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~s$
```Is the disk corrupted?

Oh and
```
ubunut@ubuntu:~$ sudo mount -o loop root.disk /media/root/
root.disk: Input/output error
```

---

### Post by bcbc on 2010-09-11
Doesn't look good - run chkdsk from windows (my computer, right click on the drive, properties, tools, check for errors(automatically fix). If it's your windows partition it will have to reboot to do it.
When it finishes, look for a FOUND.000 directory (hidden) under c:\ as the root.disk (if corrupted) sometimes gets recovered to there. You will have to move it back to \ubuntu\disks in that case. Then try again.

It's about the only thing you can try at this point.

---

### Post by stevedes on 2010-09-12
Ok I fixed the problem

Basically, it was a FS error on my C:\ Partition, non windows systems couldn't read the file (ubuntu live couldn't even report the file size) , but the file could be read from windows (I have an image reader to retrieve data)..so I coped root.disk over to my d:\ drive and copied it back over the original and then it booted fine.....

---


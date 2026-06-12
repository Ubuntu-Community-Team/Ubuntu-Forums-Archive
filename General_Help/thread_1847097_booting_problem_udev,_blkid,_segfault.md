---
title: "booting problem udev, blkid, segfault"
date: 2011-09-20
forum: General Help
---

### Post by hamjo on 2011-09-20
Hi there,

I've read some posts on ubuntuforums about problem related to this problem :

```
/sbin/blkid -o udev -p /dev/sda1 unexpected exit with status 0x000b
```in addition and after all I have a line with this :

```
intel ips 0000:00:if.6: failed to get i915 symbols, graphicsturbo disabled
Root filesystem check failed
```Now,

I'm using Tangostudio. It's a french distro very clean and light for musicians and other soundmakers based on Lucid.

I'm  running kernel 2.6.39-4 on a HP elitebook laptop. Unfortunately with a Poulsbo graphic card, but everything worked, with this kernel, fine for now.

In fstab I have only UUIDs for booting.

I have a double boot with Win7.
I have not installed any program on windows neither linux.

One day, in the morning, when the sun was shining, I had this error.
Tangostudio told me that a big error occurred.
"What error ??!!! What are you talking about?? Yesterday everything was fine."

I have a normal sata2 disk drive, no usb or flash for booting.
If i try blkid, I have a segfault error.

I won't become mad, because it must be a reason. No doubt on this. But which one ?

Thank you for reading and leading me into a "no re-installing world" :p

---

### Post by hamjo on 2011-09-26
up.
Any idea or a way to find something ?
thanks

---

### Post by hamjo on 2011-09-28
Well,

Yesterday I had the choice not to mount some partition and other choices (type S if I don't want to mount, M to do manual recovery and so on..) ... Guess what..Linux has booted.

But, I haven't access to my C:\ partition. Now I remember that I have defragmented the C: the day before this all this mess happened.
Now it works..I don't know kernel operation enough to tell why, but it's ok now.

---


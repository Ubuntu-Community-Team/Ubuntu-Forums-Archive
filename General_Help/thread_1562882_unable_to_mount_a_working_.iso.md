---
title: "unable to mount a working .iso"
date: 2010-08-28
forum: General Help
---

### Post by taamir on 2010-08-28
Hi, I have an iso file - works on windows XP.
But I cant mount it on ubuntu.

I tried using all iso programs, and theres seems to be a type mismatch.

When I tried:
```
file image.iso
```

I got:
```
image.iso: data
```

and not iso.

What can I do?

---

### Post by zpletan on 2010-08-28
Have you tried checking the MD5SUM?

---

### Post by lmarmisa on 2010-08-28
Try this command:

```

sudo mount -t iso9660 -o loop image.iso /mnt

```The image should be mounted in the /mnt directory.

---

### Post by taamir on 2010-08-28
after sudo mount -t iso9660 -o loop image.iso /mnt
I get the same error :

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

How do I check MD5SUM - is it check sum for the image?
I KNOW the image is 100%.

---

### Post by lmarmisa on 2010-08-28
I agree with zpletan. Check the md5sum in both iso files.

You can use HashTab for XP. This is a fine tool:

[http://beeblebrox.org/](http://beeblebrox.org/)
[http://my.malloc.us/evilseph/2008/01/04/curious-findings-hashtab/](http://my.malloc.us/evilseph/2008/01/04/curious-findings-hashtab/)

The command for Linux is md5sum.

---

### Post by taamir on 2010-08-28
The original image came from linux. (download).
So if its working on XP it should work on ubuntu.

if its still important to check MD5SUM, please give me the command.

I tried 


```
md5sum image.iso
```

---

### Post by akoskm on 2010-08-28
> **taamir said:**
> The original image came from linux. (download).
So if its working on XP it should work on ubuntu.

if its still important to check MD5SUM, please give me the command.

I tried 


```
md5sum image.iso
```

I'll also post a mount command but with different options, creat an isoTmp directory in your ~ and run:
```

sudo mount -o loop <test>.iso ~/isoTmp/

```.
Replace the <test> with the actual filename.
Hope this help.

---

### Post by lmarmisa on 2010-08-28
> **taamir said:**
> The original image came from linux. (download).
So if its working on XP it should work on ubuntu.

if its still important to check MD5SUM, please give me the command.

I tried 


```
md5sum image.iso
```

Your command is right. You should compare this result with the md5sum of the iso XP file.

BTW, you say that the iso image was downloaded. Is it available in a public server in Internet?.

---

### Post by taamir on 2010-08-28
akoskm Thanks allot - this solved my problem - apperantly linux CAN do anything :).

---

### Post by akoskm on 2010-08-28
> **taamir said:**
> akoskm Thanks allot - this solved my problem - apperantly linux CAN do anything :).

I think so! :)
You are welcome.

---


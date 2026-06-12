---
title: "dd gives an Input/output error--please help"
date: 2010-04-24
forum: General Help
---

### Post by TheAlien on 2010-04-24
I'm verifying a burned CD, that has been burned from an iso by Brasero, by using a dd command. But it returns an error.

```

$ dd if=/dev/scd0 bs=2048 | head -c 116955136 | md5sum -
ffa90f7054258f499200b6810c771506  -[COLOR=Red]
dd: reading `/dev/scd0': Input/output error[/COLOR]
57108+0 records in
57108+0 records out
116957184 bytes (117 MB) copied, 61.8771 s, 1.9 MB/s

```This is the GParted Live CD by the way, and the strange thing is that the MD5 is actually correct.

I've heard that this error can happen on commercial copy protected disks, but this is a standard CD-R disk.

Do anyone know what's going on here?

---

### Post by dcstar on 2010-04-25
> **TheAlien said:**
> I'm verifying a burned CD, that has been burned from an iso by Brasero, by using a dd command. But it returns an error.

```

$ dd if=/dev/scd0 bs=2048 | head -c 116955136 | md5sum -
ffa90f7054258f499200b6810c771506  -[COLOR=Red]
dd: reading `/dev/scd0': Input/output error[/COLOR]
57108+0 records in
57108+0 records out
116957184 bytes (117 MB) copied, 61.8771 s, 1.9 MB/s

```This is the GParted Live CD by the way, and the strange thing is that the MD5 is actually correct.

I've heard that this error can happen on commercial copy protected disks, but this is a standard CD-R disk.

Do anyone know what's going on here?

You are trying to read the whole CD when it obviously stops at a certain point (57108 2048 byte sectors).

Use the dd command correctly and stop it trying to read past this point.

---

### Post by asmoore82 on 2010-04-25
> **dcstar said:**
> You are trying to read the whole CD when it obviously stops at a certain point (57108 2048 byte sectors).

Use the dd command correctly and stop it trying to read past this point.

In other words...
```
dd bs=2048 **count=57108** if=/dev/scd0 | md5sum
```

Without "count," dd reads until it can't read anymore - producing the error;
but as long as the md5sum matches, it's all good.

---

### Post by dcstar on 2010-04-25
> **asmoore82 said:**
> In other words...
```
dd bs=2048 **count=57108** if=/dev/scd0 | md5sum
```

Without "count," dd reads until it can't read anymore - producing the error;
but as long as the md5sum matches, it's all good.

I was hoping that the OP would be forced to actually read the dd man page and actually learn something, but now it has been served up on a platter.....

---

### Post by TheAlien on 2010-04-25
Thank you all for helping me! It works now, even with sha1deep and sha256deep.

Dcstar, I'm taking your criticism seriously, and I'll try to use the man pages more in the future! :)

---


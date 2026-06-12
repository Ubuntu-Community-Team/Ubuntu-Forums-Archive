---
title: "Urgent help - No init found. Try passing init=bootarg"
date: 2011-01-27
forum: General Help
---

### Post by Mr. ViC on 2011-01-27
So I booted today on my 10.10 ubuntu and this error poped up:

```
[       4.144576] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default settings
[       4.286258] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default settings
[       4.362465] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default settings
```

I cannot use any other option on GRUB menu, anything!

I've read some stuff, I have booted with the live CD, oppened terminal and ran:

```
sudo fsck /dev/sda1
```But the error pops up:

```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```The hdd is unmounted, I'm stuck here! And I have an important exam tomorrow and really need my laptop working ! :confused:

Some help, please? What can I do?

---

### Post by Mr. ViC on 2011-01-27
Bumping... Please, anyone give me some ideas on how to solve this one, I really have a very important exam tomorrow and I can't do it without my laptop. :( I'm getting desperate for answers...

---

### Post by Escoba on 2011-01-27
Have you unmounted /dev/sda1 with "umount"? Try that

---


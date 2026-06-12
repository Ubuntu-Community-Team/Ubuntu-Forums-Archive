---
title: "Restore Grub2 on encrypted partition"
date: 2011-06-10
forum: General Help
---

### Post by serlex on 2011-06-10
Hey

I had to reinstall Windows, which has obviously overwritten my lovely Ubuntu Natty

I would like restore grub2, however failling to do so

I'm running:

```
sudo mount /dev/sda1 /mnt/boot
sudo cryptsetup luksOpen /dev/sda5 crypt1
Enter LUKS passphrase:
key slot 0 unlocked.
Command successful.

```

However
```
sudo pvscan
 No matching physical volumes found

```

Please help

---

### Post by Herman on 2011-06-11
```
sudo grub-setup -d /mnt/boot/grub -m /mnt/boot/grub/device.map /dev/sda
```

---

### Post by serlex on 2011-06-12
Thank you for the reply, with your command I get

```
cannot stat /mnt/boot/grub/boot.img
```

/boot is mounted, however boot.img is a mess (characters of shapes)

---

### Post by serlex on 2011-06-12
Been an absolute nob! all fixed. It would help to type your command correctly!!!

---

### Post by Herman on 2011-06-12
> It would help to type your command correctly!!!Oh, I'm sorry. What's wrong with it? I tried to tailor it to my interpretation of your situation. I am looking at it and I still can't see my mistake. Maybe I need  another coffee.

---

### Post by serlex on 2011-06-13
All good, what I meant was that it would if I typed your command correctly.

Thank you

---

### Post by Herman on 2011-06-13
Oh, good, okay, you're welcome. 

Regards, Herman :)

---


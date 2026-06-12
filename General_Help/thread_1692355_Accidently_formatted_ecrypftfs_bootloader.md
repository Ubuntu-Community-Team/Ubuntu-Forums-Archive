---
title: "Accidently formatted ecrypftfs bootloader"
date: 2011-02-21
forum: General Help
---

### Post by mshenrick on 2011-02-21
I have whole disk encryption (and home) on my maverick machine

I wanted some more swap space for my computer as i was editing images. i plugged in my memory stick, fdisk -l to find it was /dev/sd**c**

and stupidly typed

```

sudo umount /dev/sd**a**1
sudo mkswap /dev/sd**a**1
sudo swapon -p 99999 /dev/sd**a**1

```

](*,)
then went "oh sh--" and cut the power to prevent anything from being written.

I rebooted, and sure enough

```
Grub Error
Unknown Filesystem
```

My data is still intact i believe, apart from the small partition i formatted, and I have backed up. but to save hassle, can I restore the decryption bootloader thingy?

---

### Post by mshenrick on 2011-02-21
on the upside I was planning to reinstall over this half term (english 1 week school holiday) but I didn't mean for my computer to self destruct (well, I destructed it)

---

### Post by mshenrick on 2011-02-21
also, I know how to use testdisk. Is this a good idea or will it worsen the problem?

---


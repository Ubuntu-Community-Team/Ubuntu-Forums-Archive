---
title: "Install Grub!"
date: 2009-12-21
forum: General Help
---

### Post by juanmafreelance on 2009-12-21
Hi!

I have a big problem. I have Windows XP and Xubuntu.

Today, I start my computer and the grub is not show!!

My computer show a characters rare and colours.

I start my live cd with xubuntu, and I need to configure the GRUB!

In /boot/grub/ dont exists menu.lst!!

I need help!!

Thanks you!

---

### Post by Puck7 on 2009-12-21
Which version of xubuntu are you running?

---

### Post by Leppie on 2009-12-21
could you post the output of:
```
$sudo fdisk -l
```

---

### Post by juanmafreelance on 2009-12-21
> **Puck7 said:**
> Which version of xubuntu are you running?

Xubuntu 9.10 (Karmic Koala)

---

### Post by juanmafreelance on 2009-12-21
> **Leppie said:**
> could you post the output of:
```
$sudo fdisk -l
```

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3837    30820671    7  HPFS/NTFS
/dev/sda2            3838        4864     8249377+   5  Extendida
/dev/sda5            3838        4814     7847721   83  Linux
/dev/sda6            4815        4864      401593+  82  Linux swap / Solaris

---

### Post by Leppie on 2009-12-21
try the following:
```
$sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

and reboot

---

### Post by Puck7 on 2009-12-21
> **juanmafreelance said:**
> Xubuntu 9.10 (Karmic Koala)

Here is how you can restore your Grub:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by juanmafreelance on 2009-12-21
> **Leppie said:**
> try the following:
```
$sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```and reboot


Oh Thanks you!! The grub shows now!!

---

### Post by juanmafreelance on 2009-12-21
> **Puck7 said:**
> Here is how you can restore your Grub:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Thanks you!
I followed the steps that Leppie writed and the grub works now!

---

### Post by Leppie on 2009-12-21
you're welcome
glad it worked out :)

---


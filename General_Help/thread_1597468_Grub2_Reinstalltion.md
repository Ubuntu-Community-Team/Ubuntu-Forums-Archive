---
title: "Grub2 Reinstalltion"
date: 2010-10-15
forum: General Help
---

### Post by FinalShot on 2010-10-15
I've reinstalled Grub2 multiple times before, but Ubuntu was on /dev/sda1, now it is not. Here is my partition table:

/dev/sda1 - 105GB - Windows
/dev/sda2 - 200GB - Extended
/dev/sda5 - 110GB - Media
/dev/sda6 -   15GB - Linux ( NOT including /home )
/dev/sda7 -     4GB - Swap
/dev/sda8 -   80GB - /home for linux

I forgot I had a new partition table and ended up mounting sda1 and installing it there, now whenever I boot, I get some grub terminal.

How can I reinstall Grub2 with the above partition table? Oh and did I break my windows installation from installing Grub2 on sda1?

---

### Post by VMC on 2010-10-15
All you did was install a boot loader (grub) on the MBR. Your Windows partition should not be effected.

What command did you use, something of this order:

sudo grub-install /dev/sda

Not sure how you got to a linux prompt, but you can follow these [**_instructions_**]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202").

---

### Post by FinalShot on 2010-10-15
These are the commands I used.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by VMC on 2010-10-15
> **FinalShot said:**
> These are the commands I used.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Just go back and mount **sda6** instead of sda1

---

### Post by FinalShot on 2010-10-15
All good now, thanks.

---


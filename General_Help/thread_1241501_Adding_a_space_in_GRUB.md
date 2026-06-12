---
title: "Adding a space in GRUB"
date: 2009-08-16
forum: General Help
---

### Post by Nate Shoffner on 2009-08-16
Is there any way to add a space, as in a break in between menu choices?

Example:

Choice 1

Choice 2


Thanks. :)

---

### Post by kiridude on 2009-08-16
try using startupmanager. Go to synaptic and install first.

---

### Post by Nate Shoffner on 2009-08-16
An error came up when installing:

E: linux-image-2.6.30.4-ultimate: subprocess post-installation script returned error exit status 2

---

### Post by Nate Shoffner on 2009-08-16
Ugh....must be from when I tried to upgrade the kernel earlier....I guess I have to figure out how to remove it.

---

### Post by kiridude on 2009-08-16
not sure what that error is, but try the following and see if it helps:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install startupmanager
```

---

### Post by mcduck on 2009-08-16
Just edit the menu.lst file and add Title-line followed by root.

```
title    ---------
root
```

I'm not sure if you can leave the tile completely empty to get just empty space, but it might work just fine..

---

### Post by Harper45 on 2009-08-16
Windows Vista Home Premium | Windows XP Home | Ubuntu Linux (Jaunty)
CPU: AMD ATHLON X2 7550 2.5 GHz | RAM: 3GB DDR2 SDRAM | Graphics: NVIDIA GeForce 6150SE | Sound: Realtek ALC 888S | Board: Asus M2N68-LA | HD: WD 320 GB SATA

---

### Post by DeMus on 2009-08-16
> **Harper45 said:**
> Windows Vista Home Premium | Windows XP Home | Ubuntu Linux (Jaunty)
CPU: AMD ATHLON X2 7550 2.5 GHz | RAM: 3GB DDR2 SDRAM | Graphics: NVIDIA GeForce 6150SE | Sound: Realtek ALC 888S | Board: Asus M2N68-LA | HD: WD 320 GB SATA

So? What's your point?

---

### Post by Nate Shoffner on 2009-08-17
> **Harper45 said:**
> Windows Vista Home Premium | Windows XP Home | Ubuntu Linux (Jaunty)
CPU: AMD ATHLON X2 7550 2.5 GHz | RAM: 3GB DDR2 SDRAM | Graphics: NVIDIA GeForce 6150SE | Sound: Realtek ALC 888S | Board: Asus M2N68-LA | HD: WD 320 GB SATA

Not sure what that was for....
Anyway, I tried startupmanager, great little program, sadly it didn't help me with the spaces.  :(

I guess I can do what mduck said and use:

```

title    ---------
root

```

---


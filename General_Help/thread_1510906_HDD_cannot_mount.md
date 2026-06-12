---
title: "HDD cannot mount"
date: 2010-06-16
forum: General Help
---

### Post by nemiux on 2010-06-16
When I try to open one of my HDD partitions, I get an error, like shown in the image I attached. I have Windows XP, and Ubuntu installed into Windows. All the other HDD's work. What can I do to fix it.

Thank you again :)

---

### Post by nemiux on 2010-06-16
Oh, i forgot to mension, Much is the name of the partition

---

### Post by Linux_junkie on 2010-06-16
I'm guessing your trying to mount it using Gnome! Have you tried to mount it using the disk utility in the system -> administration menu?

---

### Post by thebigob on 2010-06-16
if it is an ntfs volume try:

```

sudo mount -t ntfs /dev/disk/by-label/Much /mnt

```

or if it is ext


```

sudo mount -t ext3 /dev/disk/by-label/Much /mnt

```

---

### Post by nemiux on 2010-06-16
I've entered the NTFS command and now I don't see it in "places" or either Computer. How do I access it?

P.S. I don't know was I trying to mount it with gnome, i just went Places-->Computer--> Much

---

### Post by thebigob on 2010-06-16
if you open places -> computer -> /mnt

you should see the contents there interesting you can mount it from the cli and not in gnome.

This is a workaround so you can access the files not sure how to fix it in the gui though im afraid

---

### Post by nemiux on 2010-06-16
> **thebigob said:**
> if you open places -> computer -> /mnt

you should see the contents there interesting you can mount it from the cli and not in gnome.

This is a workaround so you can access the files not sure how to fix it in the gui though im afraid

Sorry, I don't understand. I went to Computer, and if I delete everything in address bar and enter /mnt, the folder is empty. What is cli, and what command should I use to mount it so it would work, then?

---

### Post by nemiux on 2010-06-16
Oh, now I see it. However, I want to ask one more thing. What would be the command to unmount again?

---


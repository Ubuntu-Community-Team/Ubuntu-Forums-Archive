---
title: "Mount help"
date: 2009-08-06
forum: General Help
---

### Post by Dara Javaherian on 2009-08-06
Hi, I need to access files on my Windows partition so I have to use this command:

```

sudo mount -t ntfs /dev/sda1 /mnt/win

```

Unfortunately, I have to use this command every time I start Ubuntu. I added it to "startup applications" but that doesn't seem to work. 

Does anyone know how to overcome this?

Thanks ;)

---

### Post by merlinus on 2009-08-06
You will need to add an entry for it in /etc/fstab.

/dev/sda1 /mnt/win ntfs defaults,locale=en_US.utf8 0 0

If you want an icon for it to appear on your desktop, then create the mountpoint in /media

And of course change locale if you are not in US.

---

### Post by Dara Javaherian on 2009-08-06
> **merlinus said:**
> You will need to add an entry for it in /etc/fstab.

/dev/sda1 /mnt/win ntfs defaults,locale=en_US.utf8 0 0

If you want an icon for it to appear on your desktop, then create the mountpoint in /media

And of course change locale if you are not in US.

Hmm this is what I get:

```
sudo: /dev/sda1: command not found
```

P.S. How do I get an Irish locale?

---

### Post by merlinus on 2009-08-06
To edit file:

```
gksudo gedit /etc/fstab
```I do not know about the Irish locale statement.

Maybe:

en_UK

shudder....

---

### Post by martinbaselier on 2009-08-06
You need to add that line to /etc/fstab
sudo gedit /etc/fstab

---

### Post by merlinus on 2009-08-06
@martin

Best to use gksudo for graphical apps.

---

### Post by Dara Javaherian on 2009-08-06
Wow guys. I just realised how noobish I am :P Thanks btw it worked like a charm!

---


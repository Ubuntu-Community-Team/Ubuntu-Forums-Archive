---
title: "path to cdrom in 11.10"
date: 2011-11-29
forum: General Help
---

### Post by aeronutt on 2011-11-29
In previous versions, --device /dev/cdrom was the right path to cdrom when I was ripping music with command line rippers (ripit, for example). But, in 11.10, I can't find the right path. Here's what I know:

- mouse over the CD symbol in nautilus and it shows "cdda://sr0/"
- "df" shows no cdrom
- "sudo mount" shows no cdrom
- there's no cdrom at /mnt or /media

But the system sees the CD, and I can play it with Banshee.

How do I find the path to the cdrom to use with command line rippers?

---

### Post by aeronutt on 2011-11-29
Ok, found it, it's /dev/sr0
This is the kind of thing that is just a PIA.

---


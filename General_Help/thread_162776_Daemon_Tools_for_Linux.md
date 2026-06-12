---
title: "Daemon Tools for Linux?"
date: 2006-04-19
forum: General Help
---

### Post by danakatheone on 2006-04-19
Is there a daemon tools-type program for mounting CDs and DVDs for Ubuntu?

---

### Post by krusbjorn on 2006-04-19
No need. You can mount them out of the box, with a command like:

sudo mount -t iso9660 -o ro,loop /path/to/file/dvd.iso /path/to/mountpoint/

---

### Post by danakatheone on 2006-04-19
so it would be like:
sudo mount -t iso9660 -o ro,loop ~/Desktop/asdf.iso /media/cdrom2

right?

And, what if it's not an .iso?

---

### Post by krusbjorn on 2006-04-19
The command should work for at least .img-files too. If you have a bin/cue image, bchunk can easily convert it to .iso

sudo apt-get install bchunk
man bchunk

---

### Post by danakatheone on 2006-04-19
what about mds and mdf

---

### Post by stoeptegel on 2006-04-19
[QUOTE=danakatheone]so it would be like:
sudo mount -t iso9660 -o ro,loop ~/Desktop/asdf.iso /media/cdrom2

right?

And, what if it's not an .iso?[/QUOTE]

```
sudo mount file.iso /media/iso/ -t iso9660 -o loop
```

You need to make the mountpoint (in this example /media/iso) first
```
sudo mkdir /media/iso
```

For img the same applies
sudo mount file.img /media/iso/ -t iso9660 -o loop
Other formats are problem since they are proprietary

EDIT
I was a little late, sry...

---

### Post by danakatheone on 2006-04-19
Thank you.

---

### Post by krusbjorn on 2006-04-19
[QUOTE=danakatheone]what about mds and mdf[/QUOTE]

A quick search in the forums revealed this: [http://mdf2iso.berlios.de/](http://mdf2iso.berlios.de/) (debs available)

Edit: Actually, mdf2iso is in the repos: "sudo apt-get install mdf2iso".

---


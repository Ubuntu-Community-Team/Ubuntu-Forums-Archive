---
title: "Any Virtual Cd Drives on Ubuntu?"
date: 2006-06-14
forum: General Help
---

### Post by eighthate on 2006-06-14
Any1 Know if there is any virtual cd drivers on linux?

---

### Post by eqisow on 2006-06-14
```
sudo mount -o loop filename.iso /media/cdrom0
```

Just make sure you don't already have a CD-ROM mounted.

If you want to avoid conflicts with your existing drives, do the following:

```
sudo mkdir /media/iso
```

Then you can mount with:

```
sudo mount -o loop filename.iso /media/iso
```

Edit: The mounted iso won't autoplay or be treated like a normal CD, but you can still navigate to the directory and run the CD contents. For Wine, you can use winecfg to add /media/iso as a CD-ROM drive.

---

### Post by eighthate on 2006-06-14
[QUOTE=eqisow]```
sudo mount -o loop filename.iso /media/cdrom0
```

Just make sure you don't already have a CD-ROM mounted.

If you want to avoid conflicts with your existing drives, do the following:

```
sudo mkdir /media/iso
```

Then you can mount with:

```
sudo mount -o loop filename.iso /media/iso
```[/QUOTE]


thanks again for answering :p

---

### Post by eighthate on 2006-06-14
Anything for .bin and .cue?

---

### Post by eqisow on 2006-06-14
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+CD-IMAGES]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+CD-IMAGES")

Check section 5 of that.

Edit: cdemu homepage: [http://cdemu.sourceforge.net/]("http://cdemu.sourceforge.net/")

---


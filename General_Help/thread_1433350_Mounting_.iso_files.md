---
title: "Mounting .iso files"
date: 2010-03-18
forum: General Help
---

### Post by Mr Nemo on 2010-03-18
How can I mount an iso file so i can use it like a cd? I've tried a few programs that were suppose to do this, but they don't seem to work so well.

---

### Post by Megafag on 2010-03-18
> **Mr Nemo said:**
> How can I mount an iso file so i can use it like a cd? I've tried a few programs that were suppose to do this, but they don't seem to work so well.

What do you need to do that for?
just curiously.

---

### Post by srs5694 on 2010-03-18
At a command prompt:

```

sudo mount -o loop foo.iso /media/cdrom

```

Change the image filename and mount point to suit your needs.

---

### Post by Mr Nemo on 2010-03-18
Basically I want to mount psx games so I don't have to burn them. Truthfully this should have been "How can I run an iso in psx" thread. I always seem to have problems with psx emulators on ubuntu. No matter how many tutorials I read or how much advice I am given I can never get any of the emulators to work.

---

### Post by Mr Nemo on 2010-03-19
I keep getting an error that says I need to specify the filesystem type (which is ext4) but I don't know where to put that.

---

### Post by nmaster on 2010-03-19
> **Mr Nemo said:**
> I keep getting an error that says I need to specify the filesystem type (which is ext4) but I don't know where to put that.

You need to specify the filesystem of the image file... which probably isn't ext4.

to find out the filesystem do this:
```
file TheFile.iso
```this will tell the filesystem, but you could probably try doing this since you already know its an iso:
```
sudo mount TheFile.iso /path/to/mount/point -t iso9660 -o loop
```

to unmount:
```
sudo umount /path/to/mount/point
```

---

### Post by srs5694 on 2010-03-19
Linux *should* be able to autodetect the filesystem type. I don't know much about PSX or PSX emulation, so I could be way off base here, but my suspicion is that these might not be standard ISO-9660 images. Many emulators don't actually mount the CDs they use. Try running the emulator on a real physical disc. While the emulator is running, type "df" in a text-mode shell and look for an entry for that disc. If you don't see it, then the emulator is accessing the CD-ROM drive directly, without mounting it. If so, then you'll need to look for an option in your emulator software to tell it where to find the device file. Chances are there'll be an option to redirect the emulator to load a file directly rather than use the real hardware device -- but as I say, I don't know much about PSX emulators specifically, so I can't provide more specific advice.

---

### Post by Mr Nemo on 2010-03-19
sudo mount 'myfile.iso' /media/cdrom -t iso9660 -o loop

I did that.

I go this.

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I checked the file type it came up as data.

---

### Post by gadolinio on 2010-03-19
This is what works for me:

mount -t iso9660 imagename.iso /mnt -o loop

/mnt should be wherever you want it to be mounted.

---

### Post by nmaster on 2010-03-19
> **gadolinio said:**
> This is what works for me:

mount -t iso9660 imagename.iso /mnt -o loop

/mnt should be wherever you want it to be mounted.


the problem that the OP is having doesn't have to do with the command syntax i gave him

---

### Post by nmaster on 2010-03-19
> **Mr Nemo said:**
> sudo mount 'myfile.iso' /media/cdrom -t iso9660 -o loop

I did that.

I go this.

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I checked the file type it came up as data.

post the output of "file theFile.iso".  for example, 
```

$ file Entourage_s2_d1.iso 
Entourage_s2_d1.iso: UDF filesystem data (version 1.5) 'ENTOURAGE_DISC1       
```does it really just say "data"?

---

### Post by Mr Nemo on 2010-03-19
I received the same error message. I was trying to mount it to /media/cdrom. Could that be the problem?

---

### Post by Mr Nemo on 2010-03-19
Yup all it says is data. Do I have a bad file?

EDIT: Probably should show you what I got

```

file CastleVania\ Symphony\ of\ the\ night.iso 
CastleVania Symphony of the night.iso: data

```I dont even want to play the game anymore. I just want to figure out how to mount these files.

Edit # 2: I opened the iso in archive manager and it tells me the file is not in ISO 9660 format.

---

### Post by gadolinio on 2010-03-19
> **Mr Nemo said:**
> 
Edit # 2: I opened the iso in archive manager and it tells me the file is not in ISO 9660 format.

Ooops...  Can archive manager extract the iso's content anyway? So that you create a new iso with those files... just wondering...

---

### Post by srs5694 on 2010-03-19
Mr. Nemo, I think you missed my last post in this thread. Please go back and read it.

---

### Post by nmaster on 2010-03-20
> **Mr Nemo said:**
> Yup all it says is data. Do I have a bad file?

EDIT: Probably should show you what I got

```

file CastleVania\ Symphony\ of\ the\ night.iso 
CastleVania Symphony of the night.iso: data

```.


You can't mount raw data.  It needs to a be a filesystem.  What happens if you try to open the file?

```
gnome-open thing.iso
```
Or maybe just open if from Nautilus.

---


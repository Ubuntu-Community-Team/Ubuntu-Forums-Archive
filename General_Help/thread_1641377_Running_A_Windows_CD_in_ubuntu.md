---
title: "Running A Windows CD in ubuntu"
date: 2010-12-08
forum: General Help
---

### Post by laus_deo on 2010-12-08
I'm trying to run a CD, which worked fine on Windows, on Ubuntu. I have wine installed, and even tried to execute the file that the instructions said to execute(Setup.exe) if the auto run feature doesn't work, but Ubuntu wouldn't let me. So I tried to make it executable, but I couldn't because it is on a read only CD. Does anyone know how to fix this? I don't know how to access the CD drive from the terminal, so that might work. All help appreciated.

---

### Post by owiknowi on 2010-12-09
If I understand correctly: you want to run a ms w application under ubuntu?
Install wine, maybe then it will work (for 'how to' type wine in the input box on the right top of this page).

---

### Post by john77eipe on 2010-12-09
I think 
```

parted -l

```

should list all mountable devices. If you find an entry like /dev/hda (this might differ)
you can mount it using the command
```

sudo mount /dev/hda /media/cdrom

```
if the cdrom folder doesn't exist create it.
To unmount
```

sudo umount /media/cdrom

```

---

### Post by laus_deo on 2010-12-09
Yeah I have wine, but when I try to execute the file with it it says

> The file '/media/Dec 01 2009/Setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

and when I try to make the file executable, it says it's on a read only disk, so I can't do anything.

---

### Post by owiknowi on 2010-12-09
> **laus_deo said:**
> Yeah I have wine, but when I try to execute the file with it it says



and when I try to make the file executable, it says it's on a read only disk, so I can't do anything.

my experience with wine isn't all that great...
but it's also possible there's something wrong with your cd (original, not damaged, does it work under ms wx, etc?).

if possible copy it's content to your hard drive and burn a new copy at lowest speed.

---

### Post by drewsus on 2010-12-09
could you tell us WHAT your CD is?
Are you doing this from in terminal or right click and selecting WINE?
Right-click -> WINE seems to work for me regardless of it being executable.

---

### Post by laus_deo on 2010-12-09
Yeah, I was right clicking and using wine. But copying it into a new folder let me execute it and install the program. Now can I just stick a disk in there and drag it? Or is there some other procedure I should go through?

---

### Post by TheAnachron on 2010-12-09
[This dude]("http://ubuntuforums.org/showpost.php?p=10217730&postcount=3") already answered it.

---

### Post by laus_deo on 2010-12-10
Oh oops, this is probably a stupid question, but where/how do I make the media/cdrom? I don't know how to get into media to make it? or how to make it just from the home directory in the terminal.

---

### Post by owiknowi on 2010-12-10
> **laus_deo said:**
> Oh oops, this is probably a stupid question, but where/how do I make the media/cdrom? I don't know how to get into media to make it? or how to make it just from the home directory in the terminal.

Don't know if I understand your question,

If you insert a CD Ubuntu normally mounts it automatically in media/ as cdrom.
You don't have to manually add anything there as far as I know.

In File Management Preferences, tab Media, you can set how your OS should handle external media.

---


---
title: "hangs when copying pics from camera via usb"
date: 2011-12-13
forum: General Help
---

### Post by kurja on 2011-12-13
I'm running ubuntu lucid, and just ran into this problem: I plugged my camera to the usb port, selected my recent picture files and dragged them to a newly made folder on the hard drive. The first few copied over as usual, but then the whole copy process somehow froze - it just stopped working, even the memory card activity indication led on the camera went out. A blank pop-up window came up, apparently it was supposed to contain the progress indication of the ongoing copying task. It wouldn't close by clicking on the "x" on the upper corner. I rebooted and tried again, same thing happened. Then I tried copying files one by one, and it worked but was *very* slow (the actual transfer/copying, not just the by-hand process). I tried with another camera and memory card with different picture files on it, and it behaved the same.
 
Any ideas what could be at fault?

---

### Post by TeoBigusGeekus on 2011-12-13
Have you tried with another usb cable and/or another usb slot?

---

### Post by kurja on 2011-12-13
> **TeoBigusGeekus said:**
> Have you tried with another usb cable and/or another usb slot?

As a matter of fact, no. As it happens I have only one cable that fits these cameras.. I do have a card reader that uses a different plug though, I'll give that a try to see if it's any different.

---

### Post by kurja on 2011-12-13
> **TeoBigusGeekus said:**
> Have you tried with another usb cable and/or another usb slot?

yup, it exhibits the exact same symptoms with the card reader. Also when I try to make backups to an external hdd, connected to another usb port with yet another cable.

---

### Post by TeoBigusGeekus on 2011-12-13
Hmm...
Try doing it from command line:
```
cd /media/whereever_your_card_is_mounted
cd ./path_to_photos
cp image.ext /path/to/save/the/images/
```

---

### Post by kurja on 2011-12-13
> **TeoBigusGeekus said:**
> Hmm...
Try doing it from command line:
```
cd /media/whereever_your_card_is_mounted
cd ./path_to_photos
cp image.ext /path/to/save/the/images/
```

I'll give that a try. But doesn't the gui invoke these same commands when I drag and drop files?

---

### Post by kurja on 2011-12-13
> **TeoBigusGeekus said:**
> Hmm...
Try doing it from command line:
```
cd /media/whereever_your_card_is_mounted
cd ./path_to_photos
cp image.ext /path/to/save/the/images/
```

Okay, that works.

And now I have another question too... which is that I have folders named "**'11**" and such and for some reason I can't get to them with the cd command. If I type ```
cd '
``` and then hit tab I get nothing, as if there were no folders with a name beginning with '. I can see them with ```
ls
``` though. I also have folder names with spaces in them, but I wasn't able to copy files to/from them with the "cp" command (even if I copy-pasted the path from one cli window to another to eliminate typos), I just got a message saying that "xx is not a folder" - where xx is the part of the folder name *after *the space.

---

### Post by TeoBigusGeekus on 2011-12-13
Put their names in quotes, ie.
```
cd "Folder with spaces in its name"
```

---

### Post by kurja on 2011-12-13
> **TeoBigusGeekus said:**
> Put their names in quotes, ie.
```
cd "Folder with spaces in its name"
```

Thanks. Any ideas on what to do about the copying problem? I'd really rather not use cli for every copying operation.

---

### Post by TeoBigusGeekus on 2011-12-13
It could be a nautilus hiccup. Install bleachbit and do a cleanup; this will erase any possible conflicting thumbnails, cache, etc.
In general, you'd better use a lighter file manager, like Thunar for example.

---

### Post by kurja on 2011-12-13
> **TeoBigusGeekus said:**
> It could be a nautilus hiccup. Install bleachbit and do a cleanup; this will erase any possible conflicting thumbnails, cache, etc.
In general, you'd better use a lighter file manager, like Thunar for example.

That actually helped! Things copy normally to and from the external hdd, there's still something "iffy" about getting the photos off the memory cards but it could be the cards themselves.

---

### Post by TeoBigusGeekus on 2011-12-13
Copy everything valuable from the cards and format them.

---

### Post by kurja on 2011-12-13
> **TeoBigusGeekus said:**
> Copy everything valuable from the cards and format them.

way ahead of you. I'll update to this thread when I've shot something on them and tried again.

---

### Post by TeoBigusGeekus on 2011-12-13
> **kurja said:**
> way ahead of you. I'll update to this thread when I've shot something on them and tried again.

I have witnessed something similar before with my phone card.
For some reason it used to be mounted read only by my phone and by my system.
I sudo-copied everything important to the hd, formatted it, moved back the data and it was as good as new.

---

### Post by kurja on 2011-12-22
I've tried again now, and discovered that the problem persists when copying files via usb to that particular hard drive - but not when copying files to another hard drive! No problem whatsoever copying +500MB to a folder on my desktop, but try copying to another internal hdd either from that folder, or from an usb-connected flash media, and it'll work for a short while and then nautilus hangs. The weird thing is that I can copy two or three files at a time without a hiccup, but choose more than that at a time and it'll just freeze.

Disk issue? Should I try disk checking tools, what's recommended?

---

### Post by kurja on 2011-12-29
I ran a disk fix utility ```
buy new hdd
``` all seems to be in order now. Thanks for all the help :)

---


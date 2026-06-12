---
title: "Delete Everything?"
date: 2010-10-11
forum: General Help
---

### Post by chocodum on 2010-10-11
Is there a way to delete everything using the terminal so it's possible to re-download Ubuntu? 

I have a corrupted version of Ubuntu, it seems like my computer crashed while I was upgrading it. Now I don't have a properly functioning GNOME desktop, and the trash, workspace, task icons, window viewer and desktop viewer buttons are all corrupted.

It seems like the live CD version takes those files from the corrupted version inside my computer and uses them, so I can't properly run Install without the system freezing. 

Thanks in advance.

---

### Post by corrytonapple on 2010-10-11
It sounds like your GNOME desktop is corrupted. You will have to do this from the terminal. If you can, boot in to the Corrupted Ubuntu desktop, then Go to the terminal (**Applications>Accessories>Terminal**). Then type:
```

sudo aptitude-get purge ubuntu-desktop

```That will remove the Ubuntu desktop. So when that is done, you will just have a CLI (CLI-Command Line Interface). Then type:
```

sudo aptitude-get install ubuntu-desktop

```That will put the GUI (GUI-Graphical User Interface) back on Ubuntu. Restart and you should have a problem free GUI.

---

### Post by chocodum on 2010-10-11
Okay! Thakies to you! (^&#9675;^) Imma go try it now!

---

### Post by WorMzy on 2010-10-11
> **corrytonapple said:**
> apitude-get

Wow. That's a new one to me.

Possibly you meant

```
sudo apt-get purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
```

or 

```
sudo aptitude purge ubuntu-desktop
sudo aptitude install ubuntu-desktop
```

?

---

### Post by chocodum on 2010-10-11
What if I can't get to any terminal? What do I do then?

---

### Post by cgroza on 2010-10-11
You will be dropped to a shell after you remove ubuntu-desktop.

---

### Post by corrytonapple on 2010-10-11
> **chocodum said:**
> What if I can't get to any terminal? What do I do then?
Well, I am not positive, but you could try the same command from the Live CD you have. Is your live CD a CD-R, CD-RW, or USB Flash Drive? Is the whole drive dedicated to Ubuntu?

---

### Post by AoSteve on 2010-10-11
If you can get to a command line; those two commands will work as mentioned before.   I'm not sure which loader you have, but I had some problems after a recent upgrade to 10.10 and had to do something similar with the default login screen.

The purge and install are basically a full reinstall and it will take a bit.  Purge will release all of the files and settings (if I'm correct here) and installing it will refresh gnome completely.   

I'd first run a "sudo apt-get update" though to make sure the entire repo's list is up to date.   I've had issues in the past with kde and the similar lol

---


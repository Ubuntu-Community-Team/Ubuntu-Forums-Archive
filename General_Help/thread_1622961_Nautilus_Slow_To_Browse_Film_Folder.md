---
title: "Nautilus Slow To Browse Film Folder"
date: 2010-11-16
forum: General Help
---

### Post by demonboy on 2010-11-16
Hi,

I've been chopping and changing my films folders and I've been finding Nautilus really slow to scroll. It takes a while to build the contents list and then it's jumpy whilst scrolling through the list.

I mention that it has a problem with the film folder because I imagine it is trying to build a thumbnail for each entry. Is this correct?

How can I speed Nautilus up? It is far slower than Windows explorer, and I don't like that!

---

### Post by gradinaruvasile on 2010-11-16
> I mention that it has a problem with the film folder because I imagine it is trying to build a thumbnail for each entry. Is this correct?

Yes. What is the question?

You can turn off thumbnailing.

---

### Post by demonboy on 2010-11-16
I love the way you answer my question, then ask what the question is ;)

Thanks for the tip. I've found the option under Preferences and it's made a big difference.

---

### Post by sharath.puranik on 2010-11-16
> **demonboy said:**
> Hi,

I've been chopping and changing my films folders and I've been finding Nautilus really slow to scroll. It takes a while to build the contents list and then it's jumpy whilst scrolling through the list.

I mention that it has a problem with the film folder because I imagine it is trying to build a thumbnail for each entry. Is this correct?

How can I speed Nautilus up? It is far slower than Windows explorer, and I don't like that!

Is it a Windows drive? Windows drives can sometimes be slow to access when used in Linux due to differences in filesystems.

---

### Post by demonboy on 2010-11-16
No, it's not a Windows folder.

---

### Post by mirearts KING SUNNY on 2010-11-16
If your drive is an NTFS (Windows) partition type, then check for errors in Windows, then defragment it. In Ubuntu, clear all your previous thumbnails by:

1. Got to Applications>Utilities>Ubuntu Tweak
2. Browse the 'system' option and select clear thumbnails (explore a little)

---

### Post by demonboy on 2010-11-16
Thanks for the Tweak tip.

Still a bit clunky but I will now defrag the disk in Windows.

---

### Post by VanillaMozilla on 2010-12-10
If you have Assistive Technologies, that can completely cripple Nautilus.  System > Preferences.  You need to log off before changes take effect.

Also, image and text previews, etc. can slow it up somewhat.  See Preview tab on Nautilus Preferences menu.

---

### Post by demonboy on 2010-12-11
Thanks for the tips. I cheated in the end though:

I was running 10.10 as a test whilst dual-booting Windows that had got really clogged up and fragmented. No matter how much I defragged the hard drive was quite stuffed. In the end I reformatted my hard drive, installed XP sp3 and gave it 50Gb, and then 10.10 giving it 90Gb. I now only use XP for offline graphic and audio work, so it barely gets used. Ubuntu, meanwhile, now runs like a peach without the problems I was getting with Nautilus.

---

### Post by Krytarik on 2010-12-11
I've just today found a way to only turn off thumbnailing for specific files, in my case also only videos. I really like to have thumbnails on image-files.

in terminal:
```
gconf-editor
```
then browse to:
/desktop/gnome/thumbnailers

and uncheck "enable" in the respective file-type-folders

AVI    = "video@x-msvideo"
MPEG    = "video@mpeg"
FLV    = "video@x-flv"

To get the filetype for a particular file, right-click on it, then click on "Properties".

---


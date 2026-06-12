---
title: "Create an iso image in ubuntu 10.04"
date: 2010-05-27
forum: General Help
---

### Post by bgrohe on 2010-05-27
I want to create an ISO file in brasero but it only lets me create a cue. What should I do

---

### Post by Serpher on 2010-05-27
Just right click on the ISO file, and select "Write to disc"

---

### Post by bgrohe on 2010-05-27
I don't mean to wright an iso file to a disk, I want to make an disk image from a folder on my computer

---

### Post by Serpher on 2010-05-27
Sorry misread your question. Is this so it can later be burnt to a disc? Or do you just want some kind of file you can mount with that folder in it?

---

### Post by bgrohe on 2010-05-27
I want to mount it, my friends (windows) computer crashed and she wants me to get her music off her ipod. the drm music won't work with the media converter (gstreamer) so I wanted to burn it to a disc image and then mount it and rip it to eliminate the drms so I can give it back to her.

---

### Post by linuxman94 on 2010-05-27
Brasero is for dealing with CD's so it won't work with the iPod.

---

### Post by bgrohe on 2010-05-27
I am not directly trying to put it on the ipod, I want to strip the drms, and I think ripping it from a cd would do that also I already have the songs in a folder on my computer

---

### Post by gadolinio on 2010-05-27
Copy the files to your computer. Then open brasero, and add those files to the project. Then click burn, and as CD recorder or CD-to-which-burn-files select "image file brasero.iso". That way you can create a file called "brasero.iso" in your home/user folder.

---

### Post by amp3030 on 2010-07-11
> **bgrohe said:**
> I want to create an ISO file in brasero but it only lets me create a cue. What should I do
I had the same problem and I've found the answer. Open brasero and select 'Disk Copy'. Then set the 'Select a disc to write to' to 'Image file'. You see that the default is 'brasero.toc' but you can change the type easily to other formats by clicking 'Properties'. choose your desired type from 'Cdrdro image', 'CUE' and 'ISO9660 image' at the bottom of the dialog, which ask about 'Disc image type'.



Hope it helps.

---


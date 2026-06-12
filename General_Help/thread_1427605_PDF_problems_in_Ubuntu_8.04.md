---
title: "PDF problems in Ubuntu 8.04"
date: 2010-03-11
forum: General Help
---

### Post by Hans Otterson on 2010-03-11
I'm running 8.04 Hardy Heron, which came with the Evince reader. Problem is, the files I'm looking at are somewhat corrupted in Evince (big blocks of gray over the images/text). I've looked at the files before on a Windows machine with Acrobat, and they were fine.

So I did some research and installed KPDF. Yes! The files are corruption-free. However, I can't for the life of me figure out how to print them out correctly! They're landscape-formatted, and I set the KPDF printer settings to landscape, and it still prints them out in portrait format and truncates the images. What the hell? Can anyone offer me help, either with KPDF or Evince? Thanks!

---

### Post by sybille on 2010-03-12
One idea:
In your Home folder, look for a hidden folder named ".cups".

(To view hidden files and folders in Nautilus, the Gnome file manager, press Control + H or select View -> Show Hidden Files.)

If you find a folder named ".cups", look inside it for a text file named "lpoptions". If it exists, rename it.

I don't know which application creates this folder and file, but if it exists in your home folder, the settings it contains will override the settings you choose in your applications.

See: [http://ubuntuforums.org/showthread.php?t=1335789](http://ubuntuforums.org/showthread.php?t=1335789)

---


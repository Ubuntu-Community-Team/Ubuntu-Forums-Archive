---
title: "Copying files with sudo?"
date: 2009-09-01
forum: General Help
---

### Post by g0lem on 2009-09-01
I downloaded some truetype fonts. I'd like to put them in a directory that will let Open office use them. I tried to use file manager to copy the .tff files from /home/eric to /usr/share/fonts/truetype/freefont. It told me I didn't have the right permissions. I tried the command line. It doesn't seem to know the command "copy" What command do I use? and is this the correct way to install truetype fonts in Open Office? Thanks for your help!

---

### Post by P4man on 2009-09-01
"cp" is the command to copy, use that with sudo in a terminal.

Another way is installing "nautilus-gksu". that lets you open a folder as root in the file browser (right click, open as administrator). To install
>  sudo apt-get install nautilus-gksu 

---


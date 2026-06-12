---
title: "Terminal Command to specify target location for ftp &quot;get&quot;"
date: 2012-08-28
forum: General Help
---

### Post by ultrabunter on 2012-08-28
Hi,

I'm connected to my ftp server (unix) by using the gnome-terminal: 

When I use for example: 
ftp> get image1.jpg

How can I tell where this file is stored on my local machine?

What is the command if I want "image1.jpg" to show up on the Desktop of my local machine?

Thank you in advance for your help!

---

### Post by Cheesemill on 2012-08-28
You need to use the lcd (local change directory) command, for example:
```
ftp> lcd ~/Desktop
Local directory now /home/rob/Desktop
```
If you don't use lcd first then ftp defaults to saving files in your home directory.

---


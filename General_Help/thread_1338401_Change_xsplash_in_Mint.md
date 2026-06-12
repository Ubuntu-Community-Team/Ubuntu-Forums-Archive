---
title: "Change xsplash in Mint?"
date: 2009-11-26
forum: General Help
---

### Post by ninjapirate89 on 2009-11-26
Okay so I made a backup of /usr/share/images/xsplash and then copied my wallpaper into the directory and renamed to match the previous entries. Restarted and no change. So I opened all the images in GIMP and resized all of them to match the filenames. Still no luck. Then I opened them all up in GIMP again and lowered the quality so that they were approximately the same size as the defaults. And it still won't work. I don't get any xsplash at all, just a black screen. Any ideas?

Edit -> Forgot to mention this is Linux Mint 8 Helena RC1.

---

### Post by raktarok on 2009-11-26
It should have worked the first time, without any use of GIMP. I don't know what is wrong(did you check the permissions or owners?), but you can achieve the same thing by using the python script I have attached. It copies the current wallpaper to the xsplash directory and makes the gdm and xsplash match with your current wallpaper. You can even add it in your list of startup applications, and everytime you change the wallpaper, the daemon will change the xsplash for you. Handy script to have, I think. 

You can test if the xsplash changed succesfully by doing a **sudo xsplash** from the terminal. 

And here's a screenshot of my current xsplash, nice isn't it?

---

### Post by ninjapirate89 on 2009-11-26
Thanks! That worked. I just don't understand why it didn't work the manual way....oh well.

Edit -> Very nice btw. :D 
This is what I have set for mine. [http://mi9.com/datawallpapers/data/22/2151/Horsehead-Nebula-1-1024x768/horsehead-nebula_1024x768.jpg](http://mi9.com/datawallpapers/data/22/2151/Horsehead-Nebula-1-1024x768/horsehead-nebula_1024x768.jpg)

---

### Post by airtonix on 2010-01-07
I created this lua script for nautilus-scripts so you can right click on an image and : 

1. make a copy of the current xsplash folder in the current folder.
2. have imagemagick create various sizes
3. move them to the xsplash folder as root.

[http://ubuntuforums.org/attachment.php?attachmentid=142807&stc=1&d=1262898590](http://ubuntuforums.org/attachment.php?attachmentid=142807&stc=1&d=1262898590)

---


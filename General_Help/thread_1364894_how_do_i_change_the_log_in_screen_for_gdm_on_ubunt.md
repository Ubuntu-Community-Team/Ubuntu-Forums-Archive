---
title: "how do i change the log in screen for gdm on ubuntu 9.10"
date: 2009-12-26
forum: General Help
---

### Post by willdistel on 2009-12-26
hi I've been trying to install a new log in theme for linux ubuntu. I then installed kubuntu into my ubuntu install. I can run one of two shells for my install (kdm or gdm, gdm is set to default). I want to install a new theme in gdm, how would I go about doing this?

---

### Post by skarychinezeguie on 2010-01-19
i too would like to know how to change the screens during startup and shutdown and logout. I'm good with gimp and photoshop so editing them wouldn't be a problem. is that how you would go about it? if so, where are the files.

---

### Post by skarychinezeguie on 2010-02-18
OK FOLKS!!! idk about themeing the login screen, but i figured out how to change the wallpaper. I'm gonna give a couple tips here.

Ubuntu 9.10

tip 1: making a root browser window launcher
-right click the desktop and select "create launcher"
-name it whatever
-describe it however
-command: gksudo nautilus
-so now any time you need root access (ONLY IF YOU KNOW WHAT YOU'RE DOING) you can get it quickly

tip 3: Locate login picture
-first find a picture you want, set the size of the image to 2560x1600 using gimp or whatever you prefer
-save the picture to your desktop as "bg_2560x1600.jpg"
-click your root launcher and enter your password
-in your new browser window, navigate to /usr/share/images/xsplash

tip 4: CYA-cover your a**
-BACKUP THE IMAGES/XSPLASH FOLDER!!!
-NO SERIOUSLY
-PUT IT ON A THUMB DRIVE, EXTERNAL HD, CD, SECOND PARTITION, WHATEVER

tip 5: Replace background
-copy the image from your desktop to the images/xsplash folder and replace the original

-restart
-enjoy

tip 6:custom ubuntu logos and throbbers
-inside that same folder, you'll see several logos and throbbers
-simply copy them to your desktop
-edit
-copy back and replace

*I attached the wallpaper i made and used for my login. feel free to use it, or your own.

---


---
title: "log in pic"
date: 2010-03-14
forum: General Help
---

### Post by manji_kun on 2010-03-14
heres a simple question for you guys =D

im getting tired of looking at the same log in screen, is there any way i can change the picture of the screen to something else? (like, not wallpaper)

---

### Post by hhh on 2010-03-14
What do mean "like, not wallpaper"?

Anyway, are you on Karmic? If so...
[https://launchpad.net/gdm2setup/](https://launchpad.net/gdm2setup/)

Screenshots here...
[http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

HTH

---

### Post by manji_kun on 2010-03-14
no, im on ubuntu v9.10 right now, and what i mean "like not wallpaper" is having a separate image than your wallpaper.

---

### Post by Groucho Marxist on 2010-03-14
> **manji_kun said:**
> heres a simple question for you guys =D

im getting tired of looking at the same log in screen, is there any way i can change the picture of the screen to something else? (like, not wallpaper)

> **Groucho Marxist said:**
> Absolutely :) Although, I will only go into editing the log in screen for now, as I am also discovering how to alter my boot menu or "bootsplash" theme.

1.) I found my original Ubuntu login screen image in the following location: 
/usr/share/images/xsplash

2.) You are going to be looking for a file with the following name: bg_2560x1600.jpg
Make a back up of the file (such as copying the exact image into your Pictures folder just in case something does not work). 

3.) Take any desired jpg image (in my case, Gotham City) from your images folder and
open up GIMP to resize it to the original bg_2560x1600.jpg image size.

4.) Save your new image to the desktop (or any where else that is memorable) with the name bg_2560x1600.jpg
Do NOT save this new image in the same area that you placed the back up to the original.

4.) Place your newly re-named image into the following location:  /usr/share/images/xsplash

5.) It will say that you cannot place the image, as you do not have permission to alter the folder's content.
Open up Terminal and type the following command without brackets around your name: sudo chown [YOUR NAME]:[YOUR NAME] /usr/share/images/xsplash/bg_2560x1600.jpg

6.) You now have permission to change the file. Paste your new image in the folder. It will ask if you would like to replace the older image with your new one; select yes.

7.) You will now have a custom log in screen :)

Is this what you mean? :)

---

### Post by hhh on 2010-03-15
Ubuntu 9.10 is Karmic, and the link I gave allows you to set any picture ad the login background.

Hope That Helps

---

### Post by manji_kun on 2010-03-15
>  					Originally Posted by **Groucho Marxist** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8606741#post8606741") 				
 				[I]Absolutely :smile: Although, I will only go into editing the log in screen for now, as I am also discovering how to alter my boot menu or "bootsplash" theme.

1.) I found my original Ubuntu login screen image in the following location: 
/usr/share/images/xsplash

2.) You are going to be looking for a file with the following name: bg_2560x1600.jpg
Make a back up of the file (such as copying the exact image into your Pictures folder just in case something does not work). 

3.) Take any desired jpg image (in my case, Gotham City) from your images folder and
open up GIMP to resize it to the original bg_2560x1600.jpg image size.

4.) Save your new image to the desktop (or any where else that is memorable) with the name bg_2560x1600.jpg
Do NOT save this new image in the same area that you placed the back up to the original.

4.) Place your newly re-named image into the following location:  /usr/share/images/xsplash

5.) It will say that you cannot place the image, as you do not have permission to alter the folder's content.
Open up Terminal and type the following command without brackets around your name: sudo chown [YOUR NAME]:[YOUR NAME] /usr/share/images/xsplash/bg_2560x1600.jpg

6.) You now have permission to change the file. Paste your new image in the folder. It will ask if you would like to replace the older image with your new one; select yes.

7.) You will now have a custom log in screen :smile:[/I]
 			 		 	 	 Is this what you mean? :smile:


that was exactly what i meant =D 

thank you both so much for your help, i like changing the looks and feel of everything, so right now im still giddy like a school girl over changing the login screen XD

---


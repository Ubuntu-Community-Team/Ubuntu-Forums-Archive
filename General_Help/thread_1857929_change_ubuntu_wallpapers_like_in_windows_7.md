---
title: "change ubuntu wallpapers like in windows 7?"
date: 2011-10-11
forum: General Help
---

### Post by anton706 on 2011-10-11
there is an option in windows 7 to automatically get random images from bing and set them as a wallpaper is there a way to do it in ubuntu 11.04?

Also,when I try to submit this question in ubuntu stack exhchange it say "It does not meet our quality standards" what I did wrong?

---

### Post by jazzon on 2011-10-11
> **anton706 said:**
> Also,when I try to submit this question in ubuntu stack exhchange it say "It does not meet our quality standards" what I did wrong?
Just a guess here, but question too short?  (Implys not enough detail...)


 Fetch and set could be done with an automated script using wget, but im not sure how to do bash scripting.

---

### Post by onla on 2011-10-11
There are many cool things available over the internet for automatic wallpaper changing.
Simply google it to find it out. Some of the sources  are:

[http://www.technixupdate.com/web-wallpaper-downloader-download-images-and-set-them-as-desktop-background/](http://www.technixupdate.com/web-wallpaper-downloader-download-images-and-set-them-as-desktop-background/)

[http://johnsadventures.com/software/backgroundswitcher/](http://johnsadventures.com/software/backgroundswitcher/)

[http://maketecheasier.com/wally-a-cross-platform-wallpaper-changer/2009/12/09](http://maketecheasier.com/wally-a-cross-platform-wallpaper-changer/2009/12/09)

[http://ubuntugenius.wordpress.com/2009/08/26/automatic-wallpaper-changer-for-ubuntu/](http://ubuntugenius.wordpress.com/2009/08/26/automatic-wallpaper-changer-for-ubuntu/)

---

### Post by vishrut_n_shah on 2011-10-11
You can use wally a good s/w for changing wallpaper in ubuntu.
 
**[COLOR=black]Guideline for installing & using wally[/COLOR]**
[COLOR=#009933][/COLOR] 
[COLOR=#009933]**rose4linux**.wordpress.com/category/ubutnu-10-10/[/COLOR]
[COLOR=#009933][/COLOR] 
[COLOR=#009933][/COLOR]

---

### Post by anton706 on 2011-10-11
Most of these are for windows and wally dosnt work on ubuntu 11.04 is there any other suggestions?

---

### Post by Frogs Hair on 2011-10-11
Take a look at DesktopNova in the software center .

---

### Post by hwttdz on 2011-10-11
I'd just set your wallpaper to something like gnome_wallpaper.jpg, and then just put something like

wget -O gnome_wallpaper_temp.jpg [http://www.random_background.com/somestuff.jpg](http://www.random_background.com/somestuff.jpg)
mv gnome_wallpaper_temp.jpg gnome_wallpaper.jpg

in your cronjob.  So the only issue is getting a source of random images.

---

### Post by grahammechanical on 2011-10-11
Stack exchange and its Ubuntu section called Ask Ubuntu is not a forum. You must only ask questions that can be given a complete or definitive answer. And it is one question at a time. You must not ask questions that have already been answered. Duplicate questions are not allowed. Ask Ubuntu is not a place for discussion or giving opinions. Nor, is a place for saying, try this or try that and see if it works.

Take the question that you have asked here.

> is there a way to do it in ubuntu 11.04?

There answer to that is either yes or no. End of question!

How do I do this or that is a different type of question that might get answers that could be part of a Knowledge Base on Ubuntu.

I like both these Ubuntu forums and Ask Ubuntu. Here I can have a guess. There I just might come up with the correct answer.

Regards.

---

### Post by anton706 on 2011-10-11
> **hwttdz said:**
> I'd just set your wallpaper to something like gnome_wallpaper.jpg, and then just put something like

wget -O gnome_wallpaper_temp.jpg [http://www.random_background.com/somestuff.jpg](http://www.random_background.com/somestuff.jpg)
mv gnome_wallpaper_temp.jpg gnome_wallpaper.jpg

in your cronjob.  So the only issue is getting a source of random images.

to use it I just need to run that in the terminal once or every time I want to change the wallpaper?

---

### Post by stinkeye on 2011-10-11
> **anton706 said:**
> to use it I just need to run that in the terminal once or every time I want to change the wallpaper?
That's just an example of how to get a web image and set it as your wallpaper.


If you just want to use your own wallpapers use wallch.
Download the [**_[COLOR="DarkRed"]32bit Deb File for 11.04.[/COLOR]_**]("https://launchpad.net/~wallch/+archive/wallch-gnome2/+files/wallch_2.1-0ubuntu3_i386.deb")
Click on the deb file to install.

Click on the dash at the top left and enter "wallch".
Drag the wallch icon to the unity launcher.
Open wallch choose a folder where your wallpapers are.
Set your preferences and start.

You can also choose the live earth wallpaper in the launchers right click menu.

---


---
title: "Stopping Nautilus from drawing desktop"
date: 2011-11-14
forum: General Help
---

### Post by jabema on 2011-11-14
How do I stop Nautilus from drawing to the desktop?  I have downloaded and installed gconf-editor but Nautilus does not show up under the apps drop down.  I know I can launch nautilus from the command line with 'nautilus --no-desktop', but I'd prefer a way to permanently disable this function if possible

Thanks for any suggestions

---

### Post by Copper Bezel on 2011-11-14
What's your Ubuntu version, and how much of Gnome do you have installed? If you're using 11.10, there's a switch for file management on the desktop in gnome-tweak-tool, and a separate one in *dconf*-editor under org>gnome>desktop>background to toggle whether or not Gnome draws the desktop image at all. I don't have LXDE installed, but disabling that dconf key might work.

---

### Post by jabema on 2011-11-14
I'm using Lubuntu 11.10, I really don't use Nautilus for anything more than setting up my ssh bookmarks.  Pcman is my main file manager.

Nautilus is the only gnome application I have installed manually.  Not sure how many applications came with this setup.  I run in the openbox session, so gnome eye candy shouldn't be an issue.  

Is the gnome tweak an app I need to download?

---

### Post by Rodney9 on 2011-11-14
> **jabema said:**
> I'm using Lubuntu 11.10, I really don't use Nautilus for anything more than setting up my ssh bookmarks.  Pcman is my main file manager.

Nautilus is the only gnome application I have installed manually.  Not sure how many applications came with this setup.  I run in the openbox session, so gnome eye candy shouldn't be an issue.  

Is the gnome tweak an app I need to download?

Nautilus is for Gnome, it will not work very well in Lubuntu as it use LXDE and Openbox.

I doubt gnome-tweak-tool would work.

[URL="http://ubuntuforums.org/showthread.php?t=1880394&highlight=lubuntu"]After Installing Lubuntu
Guide (Things to do & Apps to Install[/URL]

I suggest you put a link to this post in the [Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755")
where other Lubuntu users will see it and may be able to help.

The [Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755") also has lots of tips, how-to's, screencasts and other 
info purely on Lubuntu

Rodney

---

### Post by Elfy on 2011-11-14
Try nautilus --no-desktop

---


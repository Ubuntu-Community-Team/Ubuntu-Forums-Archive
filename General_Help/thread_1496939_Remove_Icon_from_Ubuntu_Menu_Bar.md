---
title: "Remove Icon from Ubuntu Menu Bar"
date: 2010-05-29
forum: General Help
---

### Post by Takkak on 2010-05-29
Does anyone know how ? Just something I've been trying to figure out for the past week. Thanks in advance.

---

### Post by Sin@Sin-Sacrifice on 2010-05-29
Right click it and select "Remove From Panel" or kill the process. You can also stop processes from running at boot in System/Preferences/Startup Applications.

---

### Post by Takkak on 2010-05-29
I meant the Ubuntu icon on the 'Menu Bar' applet. I should have clarified.

---

### Post by Sin@Sin-Sacrifice on 2010-05-29
Change the icon in /usr/share/icons

---

### Post by Takkak on 2010-05-29
To remove it, would I just delete it ?

---

### Post by drs305 on 2010-05-30
> **Takkak said:**
> To remove it, would I just delete it ?

I am assuming you are trying to remove the "Ubuntu" logo from the top panel menu bar. Deleting the icon will just leave a missing icon symbol in it's place. 

Disclaimer: The following is a long-winded post about the Menu bar icon. There may be a really easy, one terminal command method of doing what you want. I've played with gconf-editor and it appears to have custom icon settings but I could neither get them to work consistently nor do exactly what you probably want (eliminate the icon entirely and remove the space it occupies). But if you have been looking for a week, here's at least something. ;-)

The bottom line is that what follows will allow you to either replace the icon, or make it transparent so you won't see it (but the space it occupies will still be there). Perhaps the information here can help you in your quest or will prompt someone else to give you an easy solution.

The icon used is in, as stated in a previous post, one of the /usr/share/icons folders. *On my Lucid install*, it is called "start-here.svg". If your system uses a different icon, you should be able to see a thumbnail of it once you find the correct folder to explore.

To find the specific file, you need to look in the correct theme folder. If different, replace "start-here.svg" with the correct name.

You can find all the "start-here.svg" icons in /usr/share/icons with this command:
```
sudo find /usr/share/icons/ -type f -name "start-here.svg"
```

Part 1: Finding the correct menu bar icon:

You can find the specific icon set *you* are using in two ways:

1, Find the theme you are using in System, Preferences, Appearance, Theme tab.  It is the one highlighted. Click on Customize, then select the "Icon" tab to see which /usr/share/icons folder your icons are stored. In my case, I am using "Ubuntu-Mono-Light" so the icons used are in /usr/share/icons/Ubuntu-Mono-Light.

2. Run this command:
```
gconf-editor /desktop/gnome/interface/icon_theme
``` 
Note note the entry value. It's in lower case, but still gives you the name of the theme.

Having found the theme icon folder, go to the apps/24 folder to find the "start-here.svg" file your menu bar is using. (Note it may be in another folder if you are not using a different size - 16, 22, etc). Open a browser as root since you will probably be renaming system files (gksu nautilus /usr/share/icons/....)

Part 2: Changing the icon.
You can change the displayed icon by renaming *start-here.svg* to something else. Next copy the icon you would like to use into this folder and rename it "start-here.svg". You can use a png file and rename the extension to ".svg" and it should work.

I tried making a 1x1 pixel icon but unfortunately the space reserved for the icon remains the default size and I could not find a setting that would change only *this* icon's size. You can hide the icon completely by making it transparent (in GIMP via the Layer, Transparency, Color to Alpha option). Now you will see nothing but the space for the icon is still there although you may not see it if the panel background is set to None.

---


---
title: "help with ubuntu 10.4 LTS"
date: 2010-05-24
forum: General Help
---

### Post by riverwhy on 2010-05-24
i've just upgraded to 10.4 LTS

first thing i notice is that if i leave the computer long enough for the screensaver to come on, when i want to start work again it requires the user password. It never used to do that and its a nuisance. There is no option to remember it that i can see either. How do i stop it asking for a password every time?

secondly, i want some thing like the "my computer" facility. I tried setting up an icon using gsconfig - the icon is now on the desktop" - it says "browse all local & remote disks connected to this computer". When i click on it i get an icon saying file system. When i open that i get quite a lot of folders displayed. But what i'm trying to locate is the USB memory stick i have plugged in.. i can't find it..   

i also tried setting it up as recommended on a site i found, by right clicking the top left icon on the desktop to get into edit menus. But i dont get that option, or the help option. i just get:
about
remove from panel
move
lock to panel

any ideas anyone??

---

### Post by Chesamo on 2010-05-24
> **riverwhy said:**
> first thing i notice is that if i leave the computer long enough for the screensaver to come on, when i want to start work again it requires the user password. It never used to do that and its a nuisance. There is no option to remember it that i can see either. How do i stop it asking for a password every time?
[http://www.shicho.net/lamp/?p=115](http://www.shicho.net/lamp/?p=115)
> **riverwhy said:**
> secondly, i want some thing like the "my computer" facility. I tried setting up an icon using gsconfig - the icon is now on the desktop" - it says "browse all local & remote disks connected to this computer". When i click on it i get an icon saying file system. When i open that i get quite a lot of folders displayed. But what i'm trying to locate is the USB memory stick i have plugged in.. i can't find it..
If your USB stick is plugged in, it should appear on your Desktop if Automount is turned on. If it's not, and you have tried all of the USB ports (or you know they work), try [this](https://help.ubuntu.com/community/Mount/USB).

What you're asking for *technically* doesn't exist in Ubuntu.  You can get to something like it by running ```
nautilus computer:///
``` in the Terminal. You can also create a Launcher on the Desktop to run that command (the icon is located at /usr/share/icons/Human/48x48/devices/computer.png).
> **riverwhy said:**
> i also tried setting it up as recommended on a site i found, by right clicking the top left icon on the desktop to get into edit menus. But i dont get that option, or the help option. i just get:
about
remove from panel
move
lock to panel
You don't right-click to get it. Go to System > Preferences > Main Menu. That's what you're looking for.

---

### Post by riverwhy on 2010-05-24
many thanks for that.. all sorted now..  one more thing though..  is there any way that text files created in ubuntu open office can be proceesed on a PC using MS word, or are they totally incompatible? I don't mind losing formatting/font stuff, but it would be useful if i can retain the text

---

### Post by cryptotheslow on 2010-05-24
In open office writer you can use the File > Save As option to save the document in MS Word format - there is a dropdown to select from down near the Save button.

---

### Post by riverwhy on 2010-05-24
ah yes.. thanks.. didnt notice there were further drop down options off screen! D'oh!

now though i have another problem.. trying to copy a saved document to my usb stick. I click on copy on the document, but when i open "my computer" and right click on, or open the usb stick icon, there is no option to paste anything into it? if i try to save directly to the usb stick using "file/save as" in open office, i can't locate the USB stick in the drop down menu at the side

---


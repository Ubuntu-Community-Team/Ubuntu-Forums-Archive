---
title: "Editing Icon Themes"
date: 2010-09-23
forum: General Help
---

### Post by Cpierce on 2010-09-23
If I download and install an icon theme in 10.04, but for certain applications would prefer the "default" icon, how would I change that ? I noticed that if the theme doesn't have a "custom" icon for a program, then it does use the default one.

---

### Post by searchfgold6789 on 2010-09-23
sudo update-alternatives --config whatever-program-you-use-for-icon-themes

---

### Post by Cpierce on 2010-09-24
I am a little confused. Would I put the actual icon theme name at the end of the command, or the name of the theme installer ? If it is the theme installer, I don't know the name, it would be whatever is default for 10.04

Appreciate the help

---

### Post by Cpierce on 2010-09-25
Kindly Bump

---

### Post by 101011010010 on 2010-09-25
Hello.
The default theme installer should be "gnome-appearance-properties". Try,> sudo update-alternatives --config gnome-appearance-propertiesYou could also replace the theme icon with a copy of the default icon that you want.

---

### Post by Cpierce on 2010-09-26
This what I get when I do that command"


chuck@chuck-laptop:~$ sudo update-alternatives --config gnome-appearance-properties
[sudo] password for chuck: 
update-alternatives: error: no alternatives for gnome-appearance-properties.
chuck@chuck-laptop:~$ 


I did install Gtk-ChTheme. But I get this again:


chuck@chuck-laptop:~$ sudo update-alternatives --config Gtk-ChTheme
[sudo] password for chuck: 
update-alternatives: error: no alternatives for Gtk-ChTheme.
chuck@chuck-laptop:~$ 

How would I change theme icon directly ?

Help!

---

### Post by Ultra_Man on 2010-09-26
What you want is to add an application icon to an icon theme that you use? Then go to the icon theme's folder and add the icon in the right category. Make sure the name of the icon is the name of the application.

---

### Post by Cpierce on 2010-09-28
I was able to change the icons, so thank you everyone. I am marking this solved.

---


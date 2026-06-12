---
title: "Libre office fails to start"
date: 2011-06-29
forum: General Help
---

### Post by tropdoug on 2011-06-29
Libre Office apps will  not start from the unity panel. When clicked the splash screen appears, disappears and nothing else happens. 

From the terminal ```
gnome-terminal -e libreoffice write
``` opens and works normally.

Same with the other apps in office. Anyone know the fix please?

---

### Post by nzjethro on 2011-06-30
Have you done any folder/file changes recently? It could be that you've broken the link to the launch script. Have you tried removing the launcher then re-adding it?

---

### Post by tropdoug on 2011-06-30
Nope, this is a brand new installation last night. Still trying to figure out how Unity works too. How do you remove and replace a launcher in Unity? The same thing is also happening with Grsync started from the apps drop down from the thingy i the top left of the screen. 

Does anyone know how to see what apps you have open or is the little arrows the only way? Unity is a challenge!

---

### Post by nzjethro on 2011-06-30
Check out [this thread.]("http://ubuntuforums.org/showthread.php?t=1775402") It seems to offer some workarounds to get LO launchers working properly (i.e. opening tho programme) with 11.04.

As for Unity customisation, I have to refrain from commenting. I'm sticking  with 10.10 until EOL, and even then I use Xfce over Gnome.

---

### Post by tropdoug on 2011-07-02
Thanks for that -- tried the suggestions but did not work for me. 

Seems odd that a major change in office app and in desktops would not have been severely tested to ensure compatibility before release, but it seems from the number of people experiencing this problem that it was. 

Any one else got any ideas please?

---

### Post by tropdoug on 2011-07-09
Bump!

---

### Post by tropdoug on 2011-07-12
OK got a fix. For anyone else experiencing this. In your home folder click ctrl > h to show hidden files, rename the .Libreoffice to something else, and then click one of your office icons in the panel and a new (clean) instance of the settings folder is created. 

When I did this suddenly all my Office apps started working perfectly from the panel. I don't know why for certain, but perhaps after an initial Natty install the Libreoffice settings folder is corrupted. Once you are happy delete the old settings folder

---

### Post by grahammechanical on 2011-07-12
I had no trouble when I upgraded from 10.10 to 11.04. Openoffice was gone and Libreoffice was there with icons in the launcher. And the settings from Openoffice had been migrated in Libreoffice. So, my recent documents list was still the same. I have noticed one thing that might point in the right direction - the .openoffice folder is still there. I wonder if somehow the programs get a bit confused with the two folders present. Libreoffice is still using a lot of Openoffice libraries and dictionaries. It may be that some bits of Libreoffice are pointing to .openoffice and other bits point to .libreoffice.

But as I say, I have had no issues. could it be the difference between an update and a fresh install?

Regards

---


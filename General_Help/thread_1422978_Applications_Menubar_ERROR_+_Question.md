---
title: "Applications Menubar ERROR + Question"
date: 2010-03-06
forum: General Help
---

### Post by bhencetotozo on 2010-03-06
Hello there guys,

There is a TERRIBLE bug going on, it took me so long to solve my problem,
I actually had to spend more than 15 minutes working on it,

I really want to solve this problem because I know other people having the same problem in other forums with out resolution.


This is what happened. I was working on a Wine configuration. By accident I 'right click' on Applications >> EDIT  MENUS, Clicked on WINE and DELETED IT. I forgot to UNDO changes, also I didn't know it was a big deal.. *IT IS*.

I lost my wine folder in my menu !!! I uninstalled wine, winetricks, winedoors, wine EVERYTHING. Reinstalled wine again, ... 

THE WINE FOLDER IN THE MENU is still missing. WTF ? ...

I will probably be able to solve the problem with less hustle next time (and also help others)if you guys could possibly answer the question below.


I made a screen shot to make it easyer to understand.

1)I created 1 folder called "plok" in the Applications menu.
1)I created 1 launcher called 444744 in the plok folder.

Where is the plok folder located?
where is the 4447444 launcher located?
Is it a file? a folder? a config file? a text file? ...If i can get into that file and edit, I think I will be able to fix that Wine bug in less than 2 minutes next time... 

Thank you 
Thank you 
Thank you 
Thank you !!!! :D

[IMG]http://98.118.57.8/Screenshot.jpg[/IMG]

Thank you 
Thank you 
Thank you 
Thank you for reading.

---

### Post by flippo on 2010-03-06
All files on the applications menu are in .desktop files in the ~/.local/ directory.  The reason it didn't reappear when you uninstalled and reinstalled wine is simple:  

To make the file disappear from the menu alcarte (the menu editing tool) sets "Hidden=true" within the file when you delete it, which, according to the .desktop file specification, is equivalent to the file being deleted, but when you run the installer for wine it checks if the file exists. Of course, the file exists (the file is there, it just has the line "Hidden=true" in it).  This results in it not being overwritten, and the menu being gone.  If you remove this line from the .desktop file you should be all fixed up.

Have fun :)

NOTE: all of this this comes from previous experience with a similar issue, and has not been tested with 9.10, although I assume it is all still true.

---

### Post by bhencetotozo on 2010-03-06
> **flippo said:**
> All files on the applications menu are in .desktop files in the ~/.local/ directory.  The reason it didn't reappear when you uninstalled and reinstalled wine is simple:  

To make the file disappear from the menu alcarte (the menu editing tool) sets "Hidden=true" within the file when you delete it, which, according to the .desktop file specification, is equivalent to the file being deleted, but when you run the installer for wine it checks if the file exists. Of course, the file exists (the file is there, it just has the line "Hidden=true" in it).  This results in it not being overwritten, and the menu being gone.  If you remove this line from the .desktop file you should be all fixed up.

Have fun :)

NOTE: all of this this comes from previous experience with a similar issue, and has not been tested with 9.10, although I assume it is all still true.


Thank you for the reply, I could not find the file you specified. Do you know by any chance, which file will contain the **"HIDDEN = TRUE"** for the wine menu on the Applications Menu? I mean, if you know it, not only me, but many many many many other people will be very thankful :) ...

I will direct this thread for those who are having this problems. Linuxforums etc.

THank you so much once again for your kindness.
Thank you.
;)

---

### Post by flippo on 2010-03-06
Hmmm, you appear to be right, alacarte does not seem to handle directories this way (it is only for the entries).  I will do some more digging and see if I can come up with anything...

---

### Post by flippo on 2010-03-06
UPDATE:
Okay, it appears your menu information is found in ~/.config/menus/...

I don't have the problem with missing wine directory (my machine does not have a wine directory intentionally) so I can't replicate it.  Does any of this information help you?

---

### Post by flippo on 2010-03-06
Okay, after a little more digging: 

Here's how she works:
Alacarte holds the metadata about the directories in ~/.config/menus/gnome-applications.menu
The actual directory entries are found in ~/.local/share/applications/<directories>.directory OR /usr/share/applications/<directory>.directory
The entries in the directories are found in ~/.local/share/applications/<entry>.desktop OR /usr/share/applications/<entry>.desktop

This should be all the information you need to fix your issue!  I would tell you how, but as I cannot replicate it I don't know EXACTLY whats wrong, just where to fix it.

I'm interested in whats going on.  Please keep me posted with your results.

---

### Post by bhencetotozo on 2010-03-06
> **flippo said:**
> Okay, after a little more digging: 

Here's how she works:
Alacarte holds the metadata about the directories in ~/.config/menus/gnome-applications.menu
The actual directory entries are found in ~/.local/share/applications/<directories>.directory OR /usr/share/applications/<directory>.directory
The entries in the directories are found in ~/.local/share/applications/<entry>.desktop OR /usr/share/applications/<entry>.desktop

This should be all the information you need to fix your issue!  I would tell you how, but as I cannot replicate it I don't know EXACTLY whats wrong, just where to fix it.

I'm interested in whats going on.  Please keep me posted with your results.


Whoa.... you are really helping man !... I am not home right now, I am here at the shop replacing my cylinder #3 on my car it blew up :( ... But I will check as soon as I get home... I checked on other forums and people wrote a DEB package to resolve this but, I will not be happy if I can't fix the problem manually... I will tell you the news as soon as I get a chance, It shouldn't be hard after all your digging.Ur advice will certainly help us all. ... Then they really should take this bug seriously on their next release of ubuntu. It is a huge bug because, restoring alacarte's default by reverting will not fix the issue, 

I had to create a NEW USER in order to fix the problem. LOL...

Thank you so much man ... 
I will tell u what happens when I try it.

Thanks again,

:P

---

### Post by bhencetotozo on 2010-03-09
UPDATE:

Yes !!!! It works !!! PERFECT !

Your a HEROE !

Sorry it took me for ever to test it. I deleted the 

<menu>

WINE ETC.ETC.ETC

</menu>

BY using the following command:

```
sudo gedit ~/.config/menus/applications.menu
```

and everything was resolved. Woot !. Thx again brother!!!

---


---
title: "setting up wireless connection"
date: 2006-05-17
forum: General Help
---

### Post by da f00 on 2006-05-17
I can't figure out how to set up my wireless connection.  I've tried going in to the Network options, and have looked at the Help section.  It says to click Add, but theres no add option, theres only Preferences, Activate, and Deactivate options.  
I have a DWL-G132 Wireless G USB Adapter and a D-Link AirPlus Xtreme G Wireless Router.
I was hoping if anyone could help me out?  Any help would be greatly appreciated :D

---

### Post by xXx 0wn3d xXx on 2006-05-17
[QUOTE=da f00]I can't figure out how to set up my wireless connection.  I've tried going in to the Network options, and have looked at the Help section.  It says to click Add, but theres no add option, theres only Preferences, Activate, and Deactivate options.  
I have a DWL-G132 Wireless G USB Adapter and a D-Link AirPlus Xtreme G Wireless Router.
I was hoping if anyone could help me out?  Any help would be greatly appreciated :D[/QUOTE]
Try following [ this tutorial.](http://ubuntuforums.org/showthread.php?t=112526&highlight=ndiswrapper) Make sure that you have your wireless card's firmware before installing. It can most likely be found on your computer distributor's website.

---

### Post by da f00 on 2006-05-17
It's not a card, it's a USB adapter.  And you install the drivers using a disc, but when I put in the disc nothing loads.  And if you open the disc in the file manager nothing appears.

---

### Post by xXx 0wn3d xXx on 2006-05-17
[QUOTE=da f00]It's not a card, it's a USB adapter.  And you install the drivers using a disc, but when I put in the disc nothing loads.  And if you open the disc in the file manager nothing appears.[/QUOTE]
Ndiswrapper works with USB wifi cards. You also can't use the Ubuntu install disc (if that's what your talking about) to set it up.

---

### Post by da f00 on 2006-05-17
Well I actually figured out why the disc wouldnt load, for some reason Ubuntu has gotten my disc drives mixed up.  It thinks my drive that I use for writing discs is my normal one.
So I can open the disc but I can't run it because the setup is in .exe format.  Can you make it so that Ubuntu can except .exe files?  And remember I can't use the internet on the my computer running Ubuntu.  So if I need to download anything I have to be able to do it on this computer and then somehow transfer it to my other one
](*,)

---

### Post by da f00 on 2006-05-18
anybody?
help?

---

### Post by tonyr on 2006-05-18
You're going to have to learn how to use  **ndiswrapper**, and pretty much
figure it out yourself.   There are other people in these forums that have done that.
You should search for similar threads in these forums that are dealing with
or have dealt with the same problem.  I used the **Search** menu near the
top of this thread page, selected the **Advanced Search** item and used the
keyword **DWL-G132** and found several entries.  Here is one:
[URL="http://www.ubuntuforums.org/showthread.php?t=146018&highlight=dwl-g132"]
http://www.ubuntuforums.org/showthread.php?t=146018&highlight=dwl-g132[/URL]

Then I went to Google, searched for **ndiswrapper**, and came up with this:
[URL="http://ndiswrapper.sourceforge.net/support.html"]
http://ndiswrapper.sourceforge.net/support.html[/URL]

In that document I found this link:
[URL="http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page"]
http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page[/URL]
which, among other things, has a link to a list of supported "cards", where
DWL-G132 is listed, so the [URL="http://ubuntuforums.org/showthread.php?t=112526&highlight=ndiswrapper"]
tutorial[/URL] that you rejected earlier probably has some valuable help.

As you find threads that have information, you might be able to use the private
mail channel in these forums to contact posters directly and ask them for 
help.  Clicking on a poster's name should take you to his profile, or somewhere
that will let you link to his profile, which will tell you whether or not he/she
accepts private email.

Dig it out.  Be adventurous. Enjoy.

---

### Post by da f00 on 2006-05-18
Alright, thanks for the help
:]
I tried the ndiswrapper thing last night and couldnt get one thing to work, but I'll check it out elsewhere

---


---
title: "wine"
date: 2011-06-17
forum: General Help
---

### Post by KRISHNASHK on 2011-06-17
should the wine be configure to run the windows application. or will it run with out any configuration? thanks

---

### Post by dragonfly41 on 2011-06-17
I'm not sure of your question ... I think you're referring to "Configure Wine" in the wine menu

but try this ..

install wine
download and save your windows application (e.g. folder including setup.exe) into a folder (e.g. on desktop)
you should see the application as in attached snapshot .. setup.exe
right click on application setup.exe (or other installation file)
select ... "Open with Wine Windows Program Loader"

and the windows application will be installed through wine.

to run it go to Applications > Wine > Programs

---

### Post by KRISHNASHK on 2011-06-17
> **dragonfly41 said:**
> I'm not sure of your question ... I think you're referring to "Configure Wine" in the wine menu

but try this ..

install wine
download and save your windows application (e.g. folder including setup.exe) into a folder (e.g. on desktop)
you should see the application as in attached snapshot .. setup.exe
right click on application setup.exe (or other installation file)
select ... "Open with Wine Windows Program Loader"

and the windows application will be installed through wine.

to run it go to Applications > Wine > Programsi am having angry birds. but that is nt the setup. i run it directly using angrybirds.exe on xp? how abt that in ubuntu ? thanks

---

### Post by dragonfly41 on 2011-06-17
As in the instructions above ... right click on angrybirds.exe and select ... "Open with Wine Windows Program Loader".

---

### Post by 3rdalbum on 2011-06-17
> **dragonfly41 said:**
> As in the instructions above ... right click on angrybirds.exe and select ... "Open with Wine Windows Program Loader".

You need to right-click the angrybirds.exe file, go to Properties and then the Permissions tab, and allow it to execute as a program.

---

### Post by ajgreeny on 2011-06-17
Not all windows executables still sitting on your windows partition will run that way, and it is not really recommended just in case there are any problems which corrupt the windows install

Some certainly will, I used to run irfan-view that way sometimes, but it was much better to install the program into your /home/.wine folder as suggested by dragonfly41.

Keep your OSs as separate as possible is my recommendation.

---


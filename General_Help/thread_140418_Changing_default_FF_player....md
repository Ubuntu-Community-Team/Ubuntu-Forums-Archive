---
title: "Changing default FF player..."
date: 2006-03-06
forum: General Help
---

### Post by DJiNN on 2006-03-06
Does anyone know how i can change the default player in FireFox, from Mplayer to an external player (Like gxine etc). I've looked in loads of places & tried many things but can't find a place to change it.

I've noticed that whenever i listen to streaming content using Mplayer, afterwards, when i go to save a page or download something in FF, it crashes bigtime, losing all the pages & tabs etc. Also, Mplayer doesn't have much control over the streaming content so i would like to try something else.

Any help would be much appreciated.

DJiNN

---

### Post by codejunkie on 2006-03-06
[QUOTE=DJiNN]Does anyone know how i can change the default player in FireFox, from Mplayer to an external player (Like gxine etc). I've looked in loads of places & tried many things but can't find a place to change it.

I've noticed that whenever i listen to streaming content using Mplayer, afterwards, when i go to save a page or download something in FF, it crashes bigtime, losing all the pages & tabs etc. Also, Mplayer doesn't have much control over the streaming content so i would like to try something else.

Any help would be much appreciated.

DJiNN[/QUOTE]
remove the **mozilla-firefox** plugin in synaptic, then when you click on the media it will open a prompt choose **open with** then choose the player you want.

you can also do this without removing the **mozilla-mplayer **package by clicking on **Edit/Preferences** in firefox go to the downloads tab click on **View & Edit Actions** and set your default player for media types, but sometimes mplayer will still open certian files, no matter if you've set the default player or not, that's why i recommend just removing the mozilla-mplayer package.

---

### Post by DJiNN on 2006-03-06
[QUOTE=codejunkie]remove the **mozilla-firefox** plugin in synaptic, then when you click on the media it will open a prompt choose **open with** then choose the player you want.[/QUOTE]

Thanks for the quick reply & the help. Does this also apply even if i have installed Mplayer via Automatix?  Can i still just remove it using Synaptic or do i have to go about it a different way?

> you can also do this without removing the **mozilla-mplayer **package by clicking on **Edit/Preferences** in firefox go to the downloads tab click on **View & Edit Actions** and set your default player for media types, but sometimes mplayer will still open certian files, no matter if you've set the default player or not, that's why i recommend just removing the mozilla-mplayer package.

I shall give this a try now...... don't know why i didn't see it before..... :)
I'd rather NOT remove Mplayer, because i'm not unhappy with it (Apart from the obvious) but if that's the only way of achieving what i'm after then so be it. 

Thanks for your help, much appreciated.

DJiNN

---

### Post by DJiNN on 2006-03-06
Well, i just went to change the settings & FF just crashed (Again!)..... it does that a lot lately, & the only thing that i can point it to is Mplayer. I've strated using Opera because it seems more stable but that seems just as difficult to change the default players in once they have been set.... :)

Anyway, i also checked the stream type to try & find out what it is, and all i got was this.....

[http://www.premiereinteractive.com/cgi-bin/members.cgi?stream=shows/COASTWIN20060305&site=coast&type=win_show](http://www.premiereinteractive.com/cgi-bin/members.cgi?stream=shows/COASTWIN20060305&site=coast&type=win_show)

So i'm not sure what file type it is.... thus i don't know what extension to choose in FF..... I'm confused. :)

DJiNN

---

### Post by codejunkie on 2006-03-06
yes even though you installed mplayer through automatix you can still uninstall the mozilla-mplayer package in synaptic or by running
```
sudo apt-get remove --purge mozilla-mplayer
``` in a terminal.
mozilla-mplayer used to crash firefox all the time for me, so i just removed it. also you might want to install the **session saver** extension for firefox just incase your problem is related to something else, even if firefox crashes just start it up again, and everything will be just like it was before the crash.

---

### Post by DJiNN on 2006-03-06
Thanks for the help codejunkie. I did what you said & removed Mplayer, but it refuses to go! :) When i go onto a webstream it just goes through the same process as before..... :)

Anyway, i shall keep on trying. Indeed, i have noticed that whenever FF crashes it always starts up again pretty well, it's just the loss of anything unsaved & the hassle that ensues in the process. It never used to be like that. 

As i said, i have started using Opera as a kind of backup, because that seems very stable & works extremely well..... :)

Thanks for all your help.

DJiNN

---

### Post by codejunkie on 2006-03-06
[QUOTE=DJiNN]Thanks for the help codejunkie. I did what you said & removed Mplayer, but it refuses to go! :) When i go onto a webstream it just goes through the same process as before..... :)

Anyway, i shall keep on trying. Indeed, i have noticed that whenever FF crashes it always starts up again pretty well, **[SIZE="2"]it's just the loss of anything unsaved & the hassle that ensues in the process[/SIZE]**. It never used to be like that. 

As i said, i have started using Opera as a kind of backup, because that seems very stable & works extremely well..... :)

Thanks for all your help.

DJiNN[/QUOTE]
this is  why i metioned the **session saver** extension, so you won't ever loose anything if firefox crashes, it make's it  reopen to the exact page/pages history, downloads etc. try running
```
sudo apt-get remove --purge mozilla-mplayer
```
in a terminal then ```
rm ~/.mozilla/firefox/pluginreg.dat
``` and restart firefox this should definitely remove the mplayer plugin since automatix install's it using apt-get.

---

### Post by DJiNN on 2006-03-06
[QUOTE=codejunkie]this is  why i metioned the **session saver** extension, so you won't ever loose anything if firefox crashes, it make's it  reopen to the exact page/pages history, downloads etc. try running
```
sudo apt-get remove --purge mozilla-mplayer
```
in a terminal then ```
rm ~/.mozilla/firefox/pluginreg.dat
``` and restart firefox this should definitely remove the mplayer plugin since automatix install's it using apt-get.[/QUOTE]

I've got it now, & thanks for the suggestion. For some reason i was confusing "Session Saver" with "Feedback Agent".... DUH! :)  It's now installed.... 

I've also done the extra bit of code that you put in, and although Mplayer is still there (It just refuses to go!) gxine works with streaming now, (HURRAH!) and i also now knonw how to change the defaults if i need to.... so i have certainly learned quite a few new things today! :)

Many thanks for taking the time to explain..... much appreciated.

DJiNN

---

### Post by codejunkie on 2006-03-10
[QUOTE=DJiNN]I've got it now, & thanks for the suggestion. For some reason i was confusing "Session Saver" with "Feedback Agent".... DUH! :)  It's now installed.... 

I've also done the extra bit of code that you put in, and although Mplayer is still there (It just refuses to go!) gxine works with streaming now, (HURRAH!) and i also now knonw how to change the defaults if i need to.... so i have certainly learned quite a few new things today! :)

Many thanks for taking the time to explain..... much appreciated.

DJiNN[/QUOTE]
happy to be of some help.

---


---
title: "DASH file lens does not display recent  files or anything"
date: 2012-05-09
forum: General Help
---

### Post by Donalb on 2012-05-09
Just started using 12.04. 

When I summon the HUD, it's empty, no recent files, folders or downloads.

Trying to find the two spreadsheet files & 1 text file I use regularly hasn't worked. I now have to open Calc then got to recent files to open.

Previously I have shortcuts to these files in Docky and it was a one click open.

Any file I've tried to find using the HUD hasn't worked, all I can find is applications. Help!

---

### Post by zombifier25 on 2012-05-09
> **Donalb said:**
> Just started using 12.04. 

When I summon the HUD, it's empty, no recent files, folders or downloads.

Trying to find the two spreadsheet files & 1 text file I use regularly hasn't worked. I now have to open Calc then got to recent files to open.

Previously I have shortcuts to these files in Docky and it was a one click open.

Any file I've tried to find using the HUD hasn't worked, all I can find is applications. Help!

The HUD is the search bar that is invoked when you tap the Alt button. It's supposed to search for menu items in an app (for example, File > Open, ...)
You must be referring to the Dash (the search bar invoked when you press the Super button or when you click the first button in the Launcher)
Try clicking on the "File" lense (the paper-like button)

---

### Post by Donalb on 2012-05-09
Thanks, yes I was confused, i.e. wrong. But the Dash Home only shows Apps, not files also as I have seen in images around the place.

---

### Post by vasa1 on 2012-05-09
> **Donalb said:**
> Thanks, yes I was confused, i.e. wrong. But the Dash Home only shows Apps, not files also as I have seen in images around the place.
Even that takes a while to get populated. You'll see them sooner or later!

---

### Post by Donalb on 2012-05-09
What does sooner or later mean? there are a few files I've opened two or three times each, they don't show up. In fact, they don't even show in hud for Calc, even when I type the start of the filename. 

This is extremely annoying and much slower than how I previously worked, where it took one mouse double click to open much used files from shortcuts.

---

### Post by vasa1 on 2012-05-09
> **Donalb said:**
> What does sooner or later mean? there are a few files I've opened two or three times each, they don't show up. In fact, they don't even show in hud for Calc, even when I type the start of the filename. 

This is extremely annoying and much slower than how I previously worked, where it took one mouse double click to open much used files from shortcuts.
Getting annoyed won't help. I can't give you a timeframe since I didn't and don't use the dash for selecting files. I use the dash to open programs and then get what I want from File, Recently Opened.

But I know that files I've previously opened do populate the dash.

LibreOffice and hence Calc is **not** HUD-ready.

---

### Post by Peter09 on 2012-05-09
It should get populated pretty quickly - try typing the name of a bookmark from firefox in the Dash, mine is pretty good at pickingh those up.

---

### Post by Donalb on 2012-05-09
I use Chrome and yes that works. But I'm far more concerned about opening 
files quickly. 

Does LibreOffice "not being supported" mean .doc or .xls files don't populate the HUD, as it seems, (except as "recently changed" which only allows opening them in Nautilus?

---

### Post by vasa1 on 2012-05-09
> **Donalb said:**
> I use Chrome and yes that works. But I'm far more concerned about opening 
files quickly. 

Does LibreOffice "not being supported" mean .doc or .xls files don't populate the HUD, as it seems, (except as "recently changed" which only allows opening them in Nautilus?
To get HUD to work with LibreOffice you may need to install lo-menubar (from the Ubuntu Software Center): see [this]("http://ubuntuforums.org/showthread.php?t=1927573") and [this]("http://askubuntu.com/questions/115412/why-doesnt-libreoffice-work-with-the-hud").

As I said, I prefer to open LibreOffice Calc from the launcher or dash and then go to File, Recent Documents.

---

### Post by vasa1 on 2012-05-09
But be aware that lo-menubar has some drawbacks:
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/760879](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/760879)
and
[https://bugs.launchpad.net/ubuntu/+source/lo-menubar/+bug/739184](https://bugs.launchpad.net/ubuntu/+source/lo-menubar/+bug/739184)

---

### Post by Donalb on 2012-05-09
Thanks lo-menubar already installed. 

So my question still remains:

Why is Dash not populated with anything except Apps?

---

### Post by vasa1 on 2012-05-09
> **Donalb said:**
> Thanks lo-menubar already installed. 

So my question still remains:

Why is Dash not populated with anything except Apps?

Could you put up a screenshot so we could take a look?

Plus  one question: have you changed any "Privacy" settings in System Settings?

---

### Post by Donalb on 2012-05-10
Shutter pixellated it for some reason, but here it is, I think you can still see that it's populated only with apps. This hasn't changed in the past 24 hours.

[IMG]http://imgur.com/Ibom5[/IMG] [http://imgur.com/Ibom5](http://imgur.com/Ibom5)

I hadn't gone near Privacy settings yet that I recall. When I just looked it the drop down box had activities for the last hour. But I assume the Delete History button has to be activated for that to take effect?

---

### Post by philinux on 2012-05-10
> **Donalb said:**
> Shutter pixellated it for some reason, but here it is, I think you can still see that it's populated only with apps. This hasn't changed in the past 24 hours.

[IMG]http://imgur.com/Ibom5[/IMG] [http://imgur.com/Ibom5](http://imgur.com/Ibom5)

I hadn't gone near Privacy settings yet that I recall. When I just looked it the drop down box had activities for the last hour. But I assume the Delete History button has to be activated for that to take effect?

Click the middle icon on the bottom of Dash that looks like a page. = Files.

---

### Post by Donalb on 2012-05-10
I've tried that. The Files lens is always empty. Not even text files show there.

---

### Post by philinux on 2012-05-10
> **Donalb said:**
> I've tried that. The Files lens is always empty. Not even text files show there.

Thats not right then. Was this an upgrade.

You could try this command unity --reset

n.b.
Lett the command finish and you may see some errors flash by. Wait a minute and then see.
Note that this will reset all unity settings to their defaults. These settings are usually accessible through CompizConfig manager (ccsm). It will reload unity, although you might want to completely log off and back in, just to make sure everything is correctly reloaded.

Also If you have disabled zeitgeist thats why too.
[http://askubuntu.com/questions/48994/unity-files-folders-lens-cant-find-anything](http://askubuntu.com/questions/48994/unity-files-folders-lens-cant-find-anything)

---

### Post by Donalb on 2012-05-10
No, this was fresh install. I was on 10.10, upgraded to 11.04, then did an immediate install with the alternate ISO.

I tried resetting Zeitgeist following those instructions. I did get an error on the reset (3rd) step, *Unable to Install scheme 3*, or something similar, I didn't write it dwon before I logged out and back, sorry.

I also reset Unity, (which fixed another unrelated problem, GIMP 2.8 not showing). Everything is still empty except Apps. I've tried opening an saving an xls and txt file. but they don't show. Music & video lens are empty though I haven;t opened one of either since I've started, nothing showing for downloads (I've dl a few small .torrents).

Thanks for help btw. I'm willing to give Unity the necessry time to get used to it, but right now all I got are problems and slower ways of doing thing I could do easier and more quickly before.

---

### Post by philinux on 2012-05-10
> **Donalb said:**
> No, this was fresh install. I was on 10.10, upgraded to 11.04, then did an immediate install with the alternate ISO.

I tried resetting Zeitgeist following those instructions. I did get an error on the reset (3rd) step, *Unable to Install scheme 3*, or something similar, I didn't write it dwon before I logged out and back, sorry.

I also reset Unity, (which fixed another unrelated problem, GIMP 2.8 not showing). Everything is still empty except Apps. I've tried opening an saving an xls and txt file. but they don't show. Music & video lens are empty though I haven;t opened one of either since I've started, nothing showing for downloads (I've dl a few small .torrents).

Thanks for help btw. I'm willing to give Unity the necessry time to get used to it, but right now all I got are problems and slower ways of doing thing I could do easier and more quickly before.

Although this was a clean install did you format home. If not you may have some conflicting settings in the hidden folders from 10.10 and 11.04 usage.

I backed up .mozilla did an evolution backup and then removed all the settings folders prior to my clean install, thereby avoiding formatting home as it's on it's own partition.

Following the unity reset all the compiz folders should be fine. Maybe remove the gnome gconf ones and logout again.

---

### Post by Donalb on 2012-05-10
No, I didn't touch /home. 

You mean delete .gconf and .gconfd? And let the system recreate? Or just .gconf and leave .gconfd alone?

---

### Post by philinux on 2012-05-10
> **Donalb said:**
> No, I didn't touch /home. 

You mean delete .gconf and .gconfd? And let the system recreate? Or just .gconf and leave .gconfd alone?

To be honest I'd try removing the compiz folders first.

Do a locate compiz, you'll have to scroll back in terminal the remove them all.

Also if you use Evolution then gconf has it's settings under the apps folder.

---

### Post by Donalb on 2012-05-10
Removed the Compiz folders, no effect (other than after I left the system for a while and came back I couldn't wake it up or it was hung, and I had to reboot).

---

### Post by philinux on 2012-05-10
> **Donalb said:**
> Removed the Compiz folders, no effect (other than after I left the system for a while and came back I couldn't wake it up or it was hung, and I had to reboot).

My laptop had issues and I blew away all the config folders to sort it. I'm sure there's a conflict somewhere or zeitgeist is not logging .

---

### Post by Donalb on 2012-05-10
Well I found the solution on AskUbuntu finally.

Removing 

~/.local/share/zeitgeist/activity.sqlite 
and logging out and back in, I finally have files populating the Dash. Looks like the Upgrade to 11.04 created was somehow responsible for this SQL file.

Thanks for the help.

---

### Post by philinux on 2012-05-10
> **Donalb said:**
> Well I found the solution on AskUbuntu finally.

Removing 

~/.local/share/zeitgeist/activity.sqlite 
and logging out and back in, I finally have files populating the Dash. Looks like the Upgrade to 11.04 created was somehow responsible for this SQL file.

Thanks for the help.

Nice. Zeitgeist it was then. I wonder if this is a bug. It's worth reporting on launchpad.

Edit. [https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/986191](https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/986191)

---


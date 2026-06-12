---
title: "Need help to install exe file!"
date: 2012-04-24
forum: General Help
---

### Post by tito-dutta on 2012-04-24
Ubuntu 11.10 I have Wine install, but, foe an exe file Wine can not install the file, tell me any other way to install that exe file.

---

### Post by strask on 2012-04-24
What .exe file are you trying to install?

What did you type when you tried to install it?

What was the error message that wine told you when it failed?

---

### Post by tito-dutta on 2012-04-24
[LIST]
[*]Auto Wiki Browser
[*]I did not type anything, I right clicked on .exe file and chose the option open with Wine
[*]There is not any error message, no window opened or nothing happened after that!
[/LIST]

---

### Post by strask on 2012-04-24
> **tito-dutta said:**
> 
[LIST]
[*]Auto Wiki Browser
[*]I did not type anything, I right clicked on .exe file and chose the option open with Wine
[*]There is not any error message, no window opened or nothing happened after that!
[/LIST]

That won't work, you need to follow the instructions here: [http://en.wikipedia.org/wiki/Wikipedia_talk:AutoWikiBrowser/Mono_and_Wine](http://en.wikipedia.org/wiki/Wikipedia_talk:AutoWikiBrowser/Mono_and_Wine)

---

### Post by tito-dutta on 2012-04-24
Yes, already tried that: [http://en.wikipedia.org/wiki/Wikipedia_talk:AutoWikiBrowser#Can_not_install_AWB](http://en.wikipedia.org/wiki/Wikipedia_talk:AutoWikiBrowser#Can_not_install_AWB)

Talking about Wine, where shall I run this command?```
 sh winetricks dotnet20 gdiplus
```

---

### Post by strask on 2012-04-24
You would type that at a shell prompt in a terminal window.

---

### Post by tito-dutta on 2012-04-24
All Greek to me. Can you give some details please! Shall I type it directly after opening terminal? 
When I did so, I got message in terminal Can't open Wintricks
[Screenshot attached]

---

### Post by strask on 2012-04-24
You typed it wrong, left out an 'e'.

Also make sure you are in the right directory where winetricks was downloaded to... you can type 'ls' to see what files are there.

---

### Post by tito-dutta on 2012-04-24
Excellent catch! ..
See the screenshot..

---

### Post by techsupport on 2012-04-24
> **tito-dutta said:**
> Excellent catch! ..
See the screenshot..

I see you guys working on this. I thought I would pop in really quick and say, Hey maybe you can install this in PlayOnLinux instead. Have you checked to see if it is available through PlayOnLinux?  They have a pretty huge list of software that will install. What is the software you are trying to install anyways?

Try PlayOnLinux to install and run windows apps (it is down the list):

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

I use it for Windows software in Wine all the time. Works great.

---

### Post by GameX2 on 2012-04-24
Yup, PlayOnLinux is pretty good as well.  I use it mostly for games, but also for Office.  For some reason, it's able to run EXE files that.. doesn't seems to start only with Wine, strange.

As for CrossOver, it make things even easier to install, but I'll say it's not worth paying for it, when you can get basically the same result with Wine or PlayOnLinux.
Although I was able to install a game with CrossOver, a game that the installer crashed using Wine.  I moved the folder to the Wine directory, and voilà!

---

### Post by techsupport on 2012-04-24
> **GameX2 said:**
> Yup, PlayOnLinux is pretty good as well.  I use it mostly for games, but also for Office.  For some reason, it's able to run EXE files that.. doesn't seems to start only with Wine, strange.

As for CrossOver, it make things even easier to install, but I'll say it's not worth paying for it, when you can get basically the same result with Wine or PlayOnLinux.
Although I was able to install a game with CrossOver, a game that the installer crashed using Wine.  I moved the folder to the Wine directory, and voilà!

Yeah, I've noticed that as well. PlayOnLinux does seem to do a better job with winetricks preconfiguration settings. It pulls everything they have tested from the WineHQ forums that actually works. I think that could be why. :)  PlayOnLinux sounds like it is just for gamers, but really it is great for everything Windows related that you want to install. Crossover is great, but it is a paid service, and I have never used them before.

---

### Post by tito-dutta on 2012-04-24
[LIST]
[*]I have POL installed, how shall I run it with POL? I mean how shall browse the file which is in "Download" folder, when I right click on the file, I don't get option to "open with POL.
[*]And for Wine this is the exact error message: [Screenshot]
[/LIST]

---

### Post by techsupport on 2012-04-24
> **tito-dutta said:**
> 
[LIST]
[*]I have POL installed, how shall I run it with POL? I mean how shall browse the file which is in "Download" folder, when I right click on the file, I don't get option to "open with POL.
[*]And for Wine this is the exact error message: [Screenshot]
[/LIST]


You almost got it.  OK, to open the file you downloaded with POL you have to open POL and then click "Install" button, and then at the very bottom left hand corner is "Install a non listed program" and then you browse to your download folder.

Make sure to check and see if the software you want to install is already available on the POL list. What you are trying to install may already be listed.

---

### Post by tito-dutta on 2012-04-24
I have installed and added icon in desktop.. but nothing is happening when I am double clicking/right click>trying to open...

I am very frustrated at this moment.. why everyone create software for Micro$oft operating system only.. more bad news.. when I tried to access the very newly launched Google Drive I found, it is not supported in Linux currently: [https://support.google.com/drive/bin/answer.py?hl=en&answer=2375082&p=ww_unsupported](https://support.google.com/drive/bin/answer.py?hl=en&answer=2375082&p=ww_unsupported)

Anyway, back to point... installation is complete, it seems, but not working as intended! 

BTW, are you a Wikipedia editor? In Wikipedia too (and also here in Ubuntu Forum) I have been searching someone who has first hand experience to use Auto Wiki Browser in Ubuntu!

---

### Post by techsupport on 2012-04-24
> **tito-dutta said:**
> I have installed and added icon in desktop.. but nothing is happening when I am double clicking/right click>trying to open...

I am very frustrated at this moment.. why everyone create software for Micro$oft operating system only.. more bad news.. when I tried to access the very newly launched Google Drive I found, it is not supported in Linux currently: [https://support.google.com/drive/bin/answer.py?hl=en&answer=2375082&p=ww_unsupported](https://support.google.com/drive/bin/answer.py?hl=en&answer=2375082&p=ww_unsupported)

Anyway, back to point... installation is complete, it seems, but not working as intended! 

BTW, are you a Wikipedia editor? In Wikipedia too (and also here in Ubuntu Forum) I have been searching someone who has first hand experience to use Auto Wiki Browser in Ubuntu!

What is the software you need? What do you want to do with it? Maybe we know of a native application you can install in Ubuntu to do the same job?  Let us know. 

If you want google drive, why not use Dropbox instead?  Or OakSpider? There are so many other apps like Google Drive that do essentially the same job.  And they are made to run on Ubuntu.  Just look them up in the Software Center and try them out. They are free to use too, just like Google Drive.

---

### Post by tito-dutta on 2012-04-24
Google Drive is not a problem.. Let's talk about Auto Wiki Browser.. I am trying to install Auto Wiki Browser (for last 4-5 months) in Ubuntu.. Auto Wiki Browser is an editing tool in Wikipedia with option to do works very quickly with lots of features.. (more details about AWB: [http://en.wikipedia.org/wiki/Wikipedia:AWB](http://en.wikipedia.org/wiki/Wikipedia:AWB)). 
Not everyone can use it, one needs to request to give access to AWB and after reviewing the editor's edits and contribution to Wikipedia, the editor's request is accepted/rejected.. 
My request was accepted few months back.. but, still I am unsuccessful to install AWB.. 
I have asked in Wikipedia Help (line give above), also asked some Ubuntu Wikipedia users but have not found anyone who use AWB+Ubuntu..
That's why I came here to get some help if anyone can tell me any alternative way to install an exe file which Wine can not recognize as exe file..

---

### Post by techsupport on 2012-04-24
> **tito-dutta said:**
> Google Drive is not a problem.. Let's talk about Auto Wiki Browser.. I am trying to install Auto Wiki Browser (for last 4-5 months) in Ubuntu.. Auto Wiki Browser is an editing tool in Wikipedia with option to do works very quickly with lots of features.. (more details about AWB: [http://en.wikipedia.org/wiki/Wikipedia:AWB](http://en.wikipedia.org/wiki/Wikipedia:AWB)). 
Not everyone can use it, one needs to request to give access to AWB and after reviewing the editor's edits and contribution to Wikipedia, the editor's request is accepted/rejected.. 
My request was accepted few months back.. but, still I am unsuccessful to install AWB.. 
I have asked in Wikipedia Help (line give above), also asked some Ubuntu Wikipedia users but have not found anyone who use AWB+Ubuntu..
That's why I came here to get some help if anyone can tell me any alternative way to install an exe file which Wine can not recognize as exe file..

Have you tried using *Wiki* Publisher in LibreOffice. I love it. Does the same job. It is a free LibreOffice extention. It rocks! All you needed to do was ask. :)

What other Windows programs do you need/want on Linux?

---

### Post by tito-dutta on 2012-04-24
[LIST]
[*]Does Wiki Publisher help in Wikipedia editing (I mean editing articles in Wikipedia)?
[*]No, I do not need any other Windows software, I can install other (MS Paint, IE etc) using Wine etc!
[/LIST]

---


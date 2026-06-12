---
title: "Electric Sheep Screensaver possible answer"
date: 2009-08-14
forum: General Help
---

### Post by phantasmik on 2009-08-14
I know there is some issues with electricsheep (for those of you who don't know what I'm referring to: [http://electricsheep.org](http://electricsheep.org) really cool screensaver) worked great in 8.04 but I had some issues in 9.04 and couldn't really find anything about it, I seemed to have resolved my issue, and I think it may be a fix that should be universal, assuming you run the script they provide on the website.

I have found that the electricsheep.desktop file located in /usr/share/applications/screensavers needs to be edited as so:

[Desktop Entry]
Encoding=UTF-8
Name=ElectricSheep
Comment=Electric Sheep is a distributed screen-saver that harnesses idle comput$
TryExec=electricsheep
Exec=electricsheep --video-driver xv --root 0
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;

--------------

so essnetially, run makesheep.sh, and edit the above file.. not sure if this has been posted, but hope it helps

---


---
title: "KDE desktop sharing"
date: 2010-09-23
forum: General Help
---

### Post by martinblunn on 2010-09-23
O.K. Guys,

I am tearing my hair out now. (Or I would be if I had any) I am running Ubuntu 10.04.

My problem is when I start a new session in Gnome, kde desktop sharing autostarts two windows. I have tried the following to prevent them autostarting with no joy..

> As far as desktop sharing goes, you need to check a couple places. Firstly open system settings and then click on the advanced tab. Under there is autostart. Check if desktop sharing is included on autostart.

No it isn't

> If it is not there, you might be restoring a saved session at every startup that includes desktop sharing. Still in system settings ---> advanced, click on session manager and see what has been set up there. If in doubt, close down everything and save that session, then use that on next startup... 

I have tried this as well as starting with an empty session. No Joy.

> in the file ~/.kde/share/config/ksmserverrc are some specifics 

This file does not exist. I have opened the folder as administrator, enabled view hidden files and it's not there.

> Try to look in System Settings > Server  Settings > Services .You`ll find your application here with a checkmark.Those with a checkmark nearby means that start when the system starts. 

There is no Server Settings in system settings.

I have of course looked in startup programs and it is not there... Can anyone offer a suggestion?

---


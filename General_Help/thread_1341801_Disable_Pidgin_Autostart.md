---
title: "Disable Pidgin Autostart"
date: 2009-11-30
forum: General Help
---

### Post by eli_12345 on 2009-11-30
Hi,
i've installed Pidgin on my system an now each time Ubuntu 9.10 starts up Pidgin gets started. Is there a way to get Pidgin out of the autostart?
I've already tried it via System/Preferences/Startup Applications, but there is no Pidgin-entry there.
The tool 'bum' also shows no Pidgin.
Best,
Eli

---

### Post by qix on 2010-01-27
Bump

I have the same problem...

---

### Post by hhlp on 2010-01-27
take a look in

system - preference - startup aplication

and find if exit an pidgin entry

---

### Post by qix on 2010-01-28
Thanks for trying, though as the post opener stated: *system->preferences->startup applications* doesn't have a pidgin entry!

---

### Post by jdorenbush on 2010-08-27
I'm having the same problem... Hopefully there is a solution out there somewhere, or is this maybe a bug?

---

### Post by Anilix on 2010-12-05
> **qix said:**
> Thanks for trying, though as the post opener stated: *system->preferences->startup applications* doesn't have a pidgin entry!


same problem, no pidgin entry whatsoever!
had to ```
sudo chmod -x /usr/bin/pidgin
```but that's not a fix since when I want to run pidgin I have to ```
sudo chmod +x /usr/bin/pidgin
``` in order to make it executable

---

### Post by IndyGunFreak on 2010-12-05
Isn't there something in Preferences about starting pidgin at startup?

---

### Post by WebNuLL on 2010-12-05
System -> Preferences -> Sessions -> Pidgin

Uncheck and save.

---

### Post by IndyGunFreak on 2010-12-05
I don't have a "sessions" in my preferences menu (but I don't have this problem either.. :))

---

### Post by yuskhanzab on 2011-03-09
i have the same problem here, there is only 1 option.. delay the pidgin at start up using sleep command. =(

---

### Post by wiggly81 on 2011-03-09
if you change your status to offline before you close pidgin does it not start up offline next time meaning its not connected on start up anyway ?

im sure it remembers status or there is a setting to make it remember

---

### Post by ne7runner on 2011-03-20
Have a look in folder ~/.config/autostart/ 
If there is any file like pidgin.desktop have a look does it have 'Hidden=true'. If so change it to false, save file and go back to Preferences > startup applications to see is pidgin now on the list.

---


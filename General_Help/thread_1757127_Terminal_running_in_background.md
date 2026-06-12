---
title: "Terminal running in background"
date: 2011-05-13
forum: General Help
---

### Post by zoi0sooB on 2011-05-13
Im really sorry for asking such a NOOB/STUPID question, its just that i dont know what to google........

Anyway, Basically, Ive got my webserver linked up to my ubuntu computer, and i want it to act like a server controller (for srcds games or w/e)

Basically, When i click the start button, the SSH launches 'css.sh' by doing this 'sh css.sh'...
Anyway, the .sh file has this inside it
cd sourceds/srcds_1/orangebox
clear
./srcds_run -console -game cstrike +map de_dust -maxplayers 16 -autoupdate

But either way, that is becides the point.

When it launches i dont see the terminal window, its invisible.... (but its running)

How do i see it when i go to my ubuntu desktop and how to i put more commands in it once its launched in the background.

Sorry if this has already been answered, i just dont know what to search up!!!

---

### Post by quixote on 2011-05-14
No worries about the noobness :mrgreen: Everybody's always a noob about something!

Open a terminal and type "jobs" (without quotes) at the prompt.  It'll list any jobs you have running in background. You can switch to one of them by typing "%job-number" (eg %2) (without quotes) at the prompt.

---

### Post by zoi0sooB on 2011-05-22
> **quixote said:**
> No worries about the noobness :mrgreen: Everybody's always a noob about something!

Open a terminal and type "jobs" (without quotes) at the prompt.  It'll list any jobs you have running in background. You can switch to one of them by typing "%job-number" (eg %2) (without quotes) at the prompt.
Sorry for the late reply. Ive been busy with stuff..


Anyway, typing in jobs and hitting enter returns nothing, i have launched my Minecraft server by SSH via PHP and i would like to also be able to access it via putty, (or put more commands in via PHP).... Either way, typing in jobs returns nothing.

[img]http://upload.mattcode.net/upload/files/matt/puTTy.PNG[/img]

---

### Post by quixote on 2011-05-22
It returns nothing if there are no background jobs running.  Or, maybe, it doesn't work with putty ... :( ?

Do something that should take a while, like a find command running in background for something not on your system (eg perhaps "Ulan Bator").  Then try the jobs command and see if it's listed.

---


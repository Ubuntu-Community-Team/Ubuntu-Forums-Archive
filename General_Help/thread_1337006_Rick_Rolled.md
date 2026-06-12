---
title: "Rick Rolled"
date: 2009-11-25
forum: General Help
---

### Post by scoobi on 2009-11-25
Hi new here and to Ubuntu. I'm On Karmic Koala. Firefox has got Rick Rolled ;)
One tab cannot be shut down and the Rick Astely song (Never gonna give you up) plays in a continuous loop.
I was all set to uninstall FF and reinstall but that seems complicated from what I've read.
This may not be the correct forum as I'm not sure if the prank has malware. All i know is I can't kill fire fox. Then again I dont know to many commands :P
Thanks.

---

### Post by jacobs444 on 2009-11-25
press alt+f2  then type: 

gksudo killall firefox

---

### Post by scoobi on 2009-11-25
Thanks that fixed it. I relaunched FF and the darned video started off again. Killed it with the command you gave and restarted the SYS. Got File system check are in progress.
Launched FF got the "Well this is embarrassing window". Saw the Rick Video which had been killed last time. This time got a choice to remove the last session (which I did) and start a new one.
Good as new. thanks again:)

---

### Post by akakingess on 2009-11-25
If it still comes back, try launching firefox from the terminal with the command```
firefox -p
``` which should start up with the profile manager and create a new profile and see if that fixes it.

---

### Post by egalvan on 2009-11-25
Check the Preferences in Firefox.. (Edit->Preferences)

The "Main" tab has options for what tabs are opened on start-up.

Yours is probably set for "show windows and tabs from last time".

---

### Post by scoobi on 2009-11-25
Thanks every one FF is behaving its self. egalvan, main tab is for home page. I think the ungraceful shut down was restoring the session. Earlier I was just shutting down the system with the video running. jacobs444 command some how got me the option of starting a new session. Thanks.

---


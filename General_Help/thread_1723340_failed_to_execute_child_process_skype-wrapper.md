---
title: "failed to execute child process skype-wrapper"
date: 2011-04-06
forum: General Help
---

### Post by hkphooey on 2011-04-06
Just figured this one out and thought I'd post it here in case it helped someone else. 

Skype just upgraded itself from 2.1 to 2.2. After upgrading it didn't start, and I got the message 

"failed to execute child process skype-wrapper"

First test out if skype runs from the command line, by running this in a terminal
```
skype &
```

If it runs, you're good to go: simply right click on the menu, locate your entry for skype and change the command to launch it from *skype-wrapper* to *skype*. The reason for this is that in the 2.1 version, skype needed a script called skype-wrapper to set some varibles before start up. Upgrading removes the script, but failed to update the menu entry.

---

### Post by ndstate on 2011-04-07
You are awesome, fixed my issue! :)

Thanks

---

### Post by Raven17 on 2011-04-07
Seems unstable to me.

Sometimes it runs for 5-10 seconds and crashes out.

Sometimes it runs fine.

Thanks for the pointer to the change regarding the wrapper.

I was also having some bluetooth problems with the new version.  

I was occasionally getting these errors also:

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

Which is kind of retarded since I don't have any bluetooth devices...

:(

---

### Post by nmlferreira on 2011-04-10
You saved my life.
Thanks!

---

### Post by Andrew_P on 2011-04-10
The upgrade to Skype (Beta) 2.2.0.25 is still broken on Ubuntu 10.04.1 LTS.  In addition to what user hkphooey stated above about the skype-wrapper being blown away by the upgrade, Skype *still* doesn't show up in the Indicator Applet on the panel, and if one closes its GUI window by clicking on the "X" in the upper right corner, Skype is left running in the background as a sleeping zombie program, consuming CPU resources; one must resort to the System Monitor to "kill" it to shut it down.  Chording (Ctrl+Q) with the keyboard while the Skype window is in focus doesn't work either.  If one attempts to click on the launcher in the Applications Menu to bring up the GUI, it fails, because it detects the previous instance of Skype running.  ***One must be very careful to only shut Skype down with the Quit command in its drop-down menu only.*** This is not user-friendly at all.  It's the only Linux program of which I know that has this nasty behavior.

---

### Post by wenfuli on 2011-04-14
Thank you! This worked for me too.

---


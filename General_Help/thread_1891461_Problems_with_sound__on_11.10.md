---
title: "Problems with sound  on 11.10"
date: 2011-12-05
forum: General Help
---

### Post by bzzzzz on 2011-12-05
I'm not sure what has happened.  I was trying to get my laptop to stream to my airport express using pulseaudio, but although I found the express, I was not successful in getting any sound out.

Unfortunately during the process of doing this I have "damaged" the sound settings.  The sound notification symbol shows speaker and -- next to it.  I no longer have control of the volume using the Fn and appropriate key.  
When browsing youtube I still get sound, so it seems that sound is still working, but I cannot control it with the sound manager.

Anyone got any ideas how I can fix this or do I need to install the whole system.

Many thanks

---

### Post by phidia on 2011-12-06
Have you tried a reboot? If not see if rebooting brings it back up-if that doesn't work you may want to check out the [sound troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=1885240") at the multimedia section and/or search your problem there too. 
Hope that helps. You shouldn't have to reinstall.

---

### Post by bzzzzz on 2011-12-06
All stuff here seems to be dealing with sound not working.  

My sound is working, I've just lost some of the controls. 

Thanks for the help though.

I'll continue to hunt through the forums for any further help

---

### Post by bluexrider on 2011-12-06
alsamixer might restore your settings and give you some additional control

---

### Post by bzzzzz on 2011-12-06
I can open alsamixer from the terminal.  I can fiddle with all sound levels there.  It just seems that there's something missing between control from the keyboard and the sound card.

It's like there are two controlers and I've lost one of them.

---

### Post by bzzzzz on 2011-12-11
I think something is wrong with pulseaudio in my personal settings.

When I login as a different user, everything is working perfectly.

When I try to open pulseaudio in a terminal this is the messagae I get

W: [pulseaudio] pid.c: Stale PID file, overwriting.
E: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
E: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
E: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
W: [pulseaudio] module.c: module-combine is deprecated: Please use module-combine-sink instead of module-combine!
W: [pulseaudio] module-combine.c: We will now load module-combine-sink. Please make sure to remove module-combine from your configuration.
Killed


Also if I try to open pavucontrol in a terminal it says it can't connect to pulseaudio.

Maybe I should just delete my account and set up a new user account.

---


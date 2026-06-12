---
title: "After Upgrading to 9.04, MythTV does not work"
date: 2010-01-25
forum: General Help
---

### Post by FamousAmos on 2010-01-25
Hi,

Like the title says, I recently upgraded from 8.10 to 9.04.  The only other change I made to my system was to switch from PulseAudio to ALSA(had a few sound bugs with Firefox using PulseAudio).  Before the upgrade my MythTV worked fine.  After the upgrade, the backend starts automatically and appears to be okay.  When I try to start the frontend, a small black rectangle appears in the middle of the screen, but the display never appears.  After playing around with it, I discovered that keyboard commands would still work(if I hit enter it will start live TV, and I can here the proper audio for the given channel, can switch channels, etc.) so I don't think I have a hardware issue with my card, etc.  I tried running it out of a terminal next, and got the following output:

```
Starting mythfrontend.real..
2010-01-23 22:35:13.027 New DB connection, total: 2
2010-01-23 22:35:13.028 Connected to database 'mythconverg' at host: localhost
2010-01-23 22:35:13.031 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2010-01-23 22:35:13.031 Enabled verbose msgs:  important general
2010-01-23 22:35:14.190 No theme dir: /home/ablinka/.mythtv/themes/G.A.N.T
2010-01-23 22:35:14.192 Primary screen 0.
2010-01-23 22:35:14.192 Running in a window
2010-01-23 22:35:14.193 Using screen 0, 1024x718 at 0,25
2010-01-23 22:35:14.193 No theme dir: /home/ablinka/.mythtv/themes/G.A.N.T
2010-01-23 22:35:14.194 Switching to square mode (G.A.N.T)
2010-01-23 22:35:14.281 Using the Qt painter
2010-01-23 22:35:14.283 JoystickMenuClient Error: Joystick disabled - Failed to read /home/ablinka/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2010-01-23 22:35:14.291 lirc_init failed for mythtv, see preceding messages
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3c0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2

```

And it continues like that forever.  Just in case it will help:

uname -a:
```
Linux ablinka-desktop 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux
```

Does anybody have any idea what happened and what I can do to correct this issue?  

Thanks in advance :)

---

### Post by FamousAmos on 2010-01-25
Anybody have any ideas?

---

### Post by FamousAmos on 2010-01-26
Just going to up this one more time, if nobody can help me that's fine, but if you have some idea, please share. 



Thanks :)

---


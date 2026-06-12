---
title: "Boot screen not right"
date: 2010-07-09
forum: General Help
---

### Post by BlackedOut271 on 2010-07-09
Hi guys. I am running Ubuntu 10.04 and installed it a couple days ago. I changed the System>Preferences>Appearance>Visual Effects to 'Extra' Ubuntu searched for drivers to make this possible and then installed them. I powered off the machine and the Ubuntu splash screen (purple with the logo and four dots underneath) was stretched, like the resolution was turned down to 800x600. I have a large monitor (LG) that has a resolution of 1920x 1080. So the logo looks crappy and off-center. The OS itself is sized properly though. I want to show off Ubuntu to my friends but this makes it look tacky. Do you guys think the new drivers could have made this happen? What do I do to fix this?

nVidia GeForce 9100 video card
Ubuntu 10.04 LTS
Installed Ubuntu via Wubi

---

### Post by matey3 on 2010-07-09
I had the same problem but it fixed itself after a reboot?!
I could not actually access my Display drivers or change res.  via the System->Pref...->Monitors, it should give you a msg like:
"
```
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
```
I have an nVidia which my install found and installed it by itself.
its under system--admin--nvidia x server settings

if the reboot didnt fix it then look in the /etc/X11/ directory and see if your xorg.conf has an older/backup copy that you could use.

and as always, be sure and back up your files

---

### Post by BlackedOut271 on 2010-07-12
> **matey3 said:**
> I had the same problem but it fixed itself after a reboot?!
I could not actually access my Display drivers or change res.  via the System->Pref...->Monitors, it should give you a msg like:
"
```
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
```I have an nVidia which my install found and installed it by itself.
its under system--admin--nvidia x server settings

if the reboot didnt fix it then look in the /etc/X11/ directory and see if your xorg.conf has an older/backup copy that you could use.

and as always, be sure and back up your files

Yeah, reboot didn't fix it. I'll keep attempting to fix this and post a solution if I find one. It is definately the nVidia drivers. You can change the settings and even modify the xorg.conf directly from the nVidia panel. Hope I figure this out soon!

---


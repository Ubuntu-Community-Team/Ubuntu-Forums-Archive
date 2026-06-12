---
title: "Firefox Portable + Flash"
date: 2010-08-23
forum: General Help
---

### Post by UltraAnders on 2010-08-23
I've been using Firefox Portable for ages, mainly between my work (Windows XP) and home (Ubuntu) machine. Recently, just on Ubuntu (10.04), Firefox Portable has started freezing on pages containing Flash. Anyone else experiencing this? I've done a clean re-install of Firefox Portable, then just added Flash, and it still freezes. Cheers.

---

### Post by UltraAnders on 2010-08-24
Have also tried using Firefox Portable 4.0 beta 2 and I still get the same problem. Should have mentioned Firefox Portable is Windows, so I'm running it under Wine on Ubuntu.

Failing a solution to this, are there any other browsers that can be fully installed and run from a memory stick?
[edit]Oooh, I've just come across this website: [http://portablelinuxapps.org/](http://portablelinuxapps.org/) looks promising ...

---

### Post by UltraAnders on 2010-08-24
Okay, seems to work providing the commands here are used:
[http://portablelinuxapps.org/forum/viewtopic.php?f=13&t=14&start=0](http://portablelinuxapps.org/forum/viewtopic.php?f=13&t=14&start=0)

Flash works, but I didn't have to install it specifically for the Portable Linux App Firefox, so not sure what's going on there. If it's using the version installed on the OS somehow, then it's not as "portable" as it first seems. Anyone used this s/w before? Just realised that it could have been anything I just ran!!

---

### Post by UltraAnders on 2010-09-28
Woo, had some time to look at this again and found this [_post_]("https://forums.addons.mozilla.org/viewtopic.php?f=26&t=1160"). For the record, I installed Flash using this old tried and tested [_method_]("http://www.acidlabs.org/2006/09/05/installing-flash-in-portable-firefox-with-no-installer/") (comment by Chandru). As I'm using a Windows version of FF Portable via Wine, I had to set "dom.ipc.plugins.enabled.npswf32.dll" to false. :)

---


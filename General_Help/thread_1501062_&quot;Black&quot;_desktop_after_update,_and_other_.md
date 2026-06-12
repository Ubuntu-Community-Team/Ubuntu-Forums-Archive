---
title: "&quot;Black&quot; desktop after update, and other major graphics problems"
date: 2010-06-03
forum: General Help
---

### Post by nyarfal on 2010-06-03
I have no idea which part of the system is causing these issues, so I'll put it in general for now.

I am currently running 10.04... just a few hours ago I installed the latest updates, one of which I think was related to the kernel. I am using a 22" Samsung LCD with a native resolution of 1680x1050, hooked up to an Radeon 9200-style (RV280) ATI card.

After the restart and login, I saw only the Gnome panels and the cursor but nothing else -- the desktop wallpaper and the external drive icons weren't there. The entire desktop was black. Like the attached picture on the left.

Everything returned to normal when I turned off Compiz, but it was working fine (if a little slow) just yesterday. So I looked for another solution and found [this thread]("http://ubuntuforums.org/showthread.php?t=1483357").

I followed the advice there and created a new xorg.conf file, dropping my color depth down to 16-bit.

After logging out and in again, the entire screen is now a dark green. The Compiz effects are nice and snappy, though!

I've deleted the custom xorg.conf file, and searched all around the forum, but I can't find any hints. As I've just done a clean install, another one won't hurt too much, but I don't really want this to repeat itself...

Any help would be greatly appreciated!

---

### Post by nyarfal on 2010-06-04
Bump... I'm dyin' over here.

---

### Post by nyarfal on 2010-06-04
I guess I'll have to clean install. Shame, really.

---


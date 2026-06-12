---
title: "Lovinglinux, I summon you! (Firefox question)"
date: 2010-07-22
forum: General Help
---

### Post by Pogeymanz on 2010-07-22
So, I have a portable version of Firefox on my USB flash drive. It is really SLOW.

I have turned off all of the disk-caching options and have even set it to not remember my history.

I only have three addons: NoScript, Adblock+, CS Lite. I could even get rid of CS Lite and manage my cookies totally manually if it means I'll have a faster GUI.

Almost every time I interact with Firefox in any way I have to wait a few seconds and I get that damned spinning beach-ball (did I mention it's the OSX version?).

Any ideas to make the GUI more responsive?

---

### Post by masque7 on 2010-07-22
Just confirming that I had horrible performance issues with the Windows build of Firefox portable a year ago from portableapps.com...

---

### Post by lovinglinux on 2010-07-22
Perhaps you could run the profile on RAM.

[http://firefox-tutorials.blogspot.com/2010/05/running-profiles-from-ram.html](http://firefox-tutorials.blogspot.com/2010/05/running-profiles-from-ram.html)

You might need to hack it to run with the USB installation.

Make backups!

---

### Post by lovinglinux on 2010-07-22
Edit: double post

---

### Post by Pogeymanz on 2010-07-23
I'll have to hack the crap out of it to get it running on OSX or Windows, but thanks for the lead.

---

### Post by lovinglinux on 2010-07-23
> **Pogeymanz said:**
> I'll have to hack the crap out of it to get it running on OSX or Windows, but thanks for the lead.

So you won't be using on Ubuntu machines, just OSX and Windows? Does it behave the same on both systems? Have you tried to run other portable apps to see if the problem is with Firefox or not?

Try  to run [SQLite Optimizer]("https://addons.mozilla.org/en-US/firefox/addon/11198/"). It should help a lot if the problem is due to disk access speed, since unoptimized databases slow down Firefox considerably.

---

### Post by lovinglinux on 2010-08-15
Hey, 

I received a PM from ron999 suggesting to put the cache on RAM.  I haven't tested it for long, but it considerably improves performance of some things. You should try it.

To put the cache in RAM use **about[noparse]:[/noparse]config** and set **browser.disk.parent_directory** to **/dev/shm**.

---

### Post by TheDesertDragon on 2010-08-15
Start Firefox
about:config

Set:

network.dns.disableIPv6

from false to true

That key causes spasmic responsetimes in Firefox. I can't be sure it's this, but it was for me.

---

### Post by lovinglinux on 2010-08-15
> **TheDesertDragon said:**
> Start Firefox
about:config

Set:

network.dns.disableIPv6

from false to true

That key causes spasmic responsetimes in Firefox. I can't be sure it's this, but it was for me.

That fixes slow page loading. What the OP is experiencing is slow Firefox interface responsiveness.

---


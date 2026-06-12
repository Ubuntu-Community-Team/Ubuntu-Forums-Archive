---
title: "Error messages about applets, applets won't appear after startup"
date: 2010-05-29
forum: General Help
---

### Post by unckybob on 2010-05-29
Can someone please help me? I'm a noob and I've never had a problem like this before.

Ever since I installed on this system every time I start up I get a bunch of error windows. They are usually different every time but here's a sample of what they look like.


--------------- QUOTE   ----------------

Error

"Show Desktop" has quit unexpectedly

If you reload a panel object, it will automatically be added back to the panel.

buttons: "Don't Reload", and "Reload"

--------------- UNQUOTE ----------------
--------------- QUOTE   ----------------

Error

The panel encountered a problem while loading "OAFIID:GNOME-WorkspaceSwitcherApplet".

Do you want to delete the applet from your configuration?

buttons: "Don't Delete", and "Delete"

--------------- UNQUOTE ----------------
--------------- QUOTE   ----------------

Error

The panel encountered a problem while loading "OAFIID:GNOME-WindowListApplet".

Do you want to delet the applet from your configuration?

buttons: "Don't Delete", and "Delete"

--------------- UNQUOTE ----------------
--------------- QUOTE   ----------------

Error

The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

Do you want to delete the apllet from your configuration?

buttons: "Don't Delete", and "Delete"

--------------- UNQUOTE ----------------
--------------- QUOTE   ----------------

Error

"Indicator Applet" has quit unexpectedly

If you reload a panel object, it will automatically be added back to the panel.

buttons: "Don't Reload", and "Reload"

--------------- UNQUOTE ----------------

I tried pressing the "Don't Delete" or "Reload" buttons as appropriate. Then the applets sometimes reappear and sometimes they don't. Please help a noob!

---

### Post by dcstar on 2010-05-30
> **unckybob said:**
> Can someone please help me? I'm a noob and I've never had a problem like this before.

Ever since I installed on this system every time I start up I get a bunch of error windows. They are usually different every time but here's a sample of what they look like.
.......
I tried pressing the "Don't Delete" or "Reload" buttons as appropriate. Then the applets sometimes reappear and sometimes they don't. Please help a noob!

Firstly, we have no idea what version you are running, please specify.

Secondly, did you do a fresh install or an upgrade because some of those messages do not apply to the current system (10.04)?

---

### Post by unckybob on 2010-05-31
I found out the answer to this one on my own. It turned out to be a hardware problem. 

This is for a Compaq Presario 5000 5WV254 Desktop PC. I upgraded the RAM to 768MB. I was told by a hardware specialist that many chipsets have load restrictions when maximum memory is installed (or all sockets are filled). There are often limitations for example against using double-sided (multi-bank) dimms in that case. 

He recommended that I cut back to 512MB. I did and everything is working hunky-dory.

---


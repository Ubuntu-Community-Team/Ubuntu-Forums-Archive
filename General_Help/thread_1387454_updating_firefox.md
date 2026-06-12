---
title: "updating firefox"
date: 2010-01-21
forum: General Help
---

### Post by princeofnam on 2010-01-21
this may be a stupid question, but i'm slightly confused on how to update to firefox 3.6.  usually there's a .deb package i can install, but the sit doesn't offer one.  synaptics doesn't seem to give a clear answer either.

---

### Post by michy99 on 2010-01-21
I found this post just a few below yours.

[http://ubuntuforums.org/showthread.php?t=1387443](http://ubuntuforums.org/showthread.php?t=1387443)

---

### Post by lovinglinux on 2010-01-21
See the [COLOR="Sienna"]**Install Other Versions section**[/COLOR] of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by aysiu on 2010-01-21
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net) is the easiest way to get the newest Firefox.

---

### Post by lovinglinux on 2010-01-21
> **aysiu said:**
> [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net) is the easiest way to get the newest Firefox.

Do you know how to make a bot so we can post these replies on every new Firefox 3.6 thread? :) There will a lot of them...

---

### Post by lais on 2010-01-22
For some reason i could not install Firefox 3.6 from ubuntuzilla. But I installed Firefox 3.6 using the instructions i found in [http://digitizor.com/2010/01/22/how-to-install-firefox-3-6-in-ubuntu-9-10/]("http://digitizor.com/2010/01/22/how-to-install-firefox-3-6-in-ubuntu-9-10/").
Worked well. Firefox 3.6 is awesome :D

---

### Post by nanotube on 2010-01-22
> **lais said:**
> For some reason i could not install Firefox 3.6 from ubuntuzilla. But I installed Firefox 3.6 using the instructions i found in [http://digitizor.com/2010/01/22/how-to-install-firefox-3-6-in-ubuntu-9-10/]("http://digitizor.com/2010/01/22/how-to-install-firefox-3-6-in-ubuntu-9-10/").
Worked well. Firefox 3.6 is awesome :D

could you elaborate on your 'for some reason'? any particular errors or problems you encountered? 

if something's wrong with the repo, i'd like to fix it. :)

---

### Post by aysiu on 2010-01-22
Those instructions are terrible. It just replaces /usr/bin/firefox completely without diverting the old symlink. Not very responsible.

---

### Post by nanotube on 2010-01-22
> **aysiu said:**
> Those instructions are terrible. It just replaces /usr/bin/firefox completely without diverting the old symlink. Not very responsible.

the biggest problem is that next time a firefox update through the repos comes through, your /usr/bin/firefox symlink will be overwritten to point back to the repos version. 

so yea, missing the dpkg-divert in those instructions is not a good idea.

---


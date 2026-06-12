---
title: "KNet Can't Initialize Modem"
date: 2006-05-29
forum: General Help
---

### Post by palsyboy on 2006-05-29
I recently took my friend's HP 505n and switched it over to Kubuntu.  Unfortunately, he lives in the country, which puts him out of DSL and cable range, and he can't afford satellite broadband, so he's stuck with dial-up.  I've never worked with dialup on Linux before, so this was a new task for me, and I set the computer up at my house well out of range of a phone line.

Anyway, when I tried to set up the modem via KNet, it gave me a message about "no lock protocol" or something, so I unchecked the "lock modem" box under the modem configuration tab (I don't have it in front of me, so please forgive name approximations).  I no longer got the error.

Next, KNet said /dev/modem wasn't the proper device name, though after scanning for modems, it seemed to think that ttyS0, ttyS1, and a few others were correct device names.   I tried several with the proper number entered, and the modem didn't seem to dial out.  Even with the "modem volume" cranked up all the way, I got no modem dialing sound.  I also tried calling my own cell phone with the computer and got nothing.  No matter which ttyS- number I tried, clicking "Connect" got me a perpetual "Initializing Modem" message. :-? 

Does anyone know what I'm doing wrong?  Thanks!

In case it becomes relevant later in this thread, his ISP is SBC/Yahoo!

---

### Post by towsonu2003 on 2006-05-31
it's almost pure luck, getting those modems to work. See the second link in my signature on how to configure an internal [win]modem.

---

### Post by palsyboy on 2006-06-03
Thanks for the handy reference; I'm not afraid to recompile the kernel, if necessary.

I'll reply as soon as I get over to my friend's house to work on it.

---

### Post by palsyboy on 2006-07-21
I ended up buying a hardware modem, though that didn't work, either.  I started a new thread for that problem, though. ](*,)

---


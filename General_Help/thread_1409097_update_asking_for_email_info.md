---
title: "update asking for email info?"
date: 2010-02-17
forum: General Help
---

### Post by Scooter_X on 2010-02-17
Hey I just barely updated my system, now it pops up a window with the name Debconf in it, and it's saying POSTFIX CONFIGURATION and asks for my 'General type of mail configuration' and when I hit 'internet' it then asks for the 'system mail name'... what in heck is this? It pops up a red flag in my brain, but it looks official. Why would I be asked this after an update?

---

### Post by Scooter_X on 2010-02-17
And now the update manager says it's "unpacking postfix (from .../postfix_2.6.5-3_i386.deb) ..."

---

### Post by danwood76 on 2010-02-17
> **Scooter_X said:**
> And now the update manager says it's "unpacking postfix (from .../postfix_2.6.5-3_i386.deb) ..."

You should just select the defaults.
It doesn't matter unless you are going to run a mail server?

---

### Post by ajgreeny on 2010-02-17
I wonder why you have postfix installed at all, unless you are running a mail server.  It is certainly not installed on my desktop system, and as far as I'm aware never has been.

---

### Post by Scooter_X on 2010-02-17
Nope. No mail server. Not to MY knowledge. Anyway, I just backed up a bit and selected the 'no configuration' option and it didn't do anything. But yea that's weird.

---

### Post by lisati on 2010-02-17
I, too, am baffled by postfix appearing out of the blue. 

A couple of possibilities come to mind. Do others have access to your computer? Did some well-intentioned acquaintance mistakenly think that "postfix" was meant to fix posts to a forum?

---

### Post by glitterball on 2010-02-18
Exact same situation here, Postfix dialog box appeared during the update and is ringing the alarm bells.

---

### Post by kelly harlton on 2010-02-18
Same here

---

### Post by Richard1979 on 2010-02-18
It's from installing Google Chrome.
They probably put Postfix in so you can email bug reports and crashes.

---

### Post by Scooter_X on 2010-02-20
Oh that makes sense. I use remote desktop every now and again, not super secure (just VNC protocol) and figured maybe someone got access somehow through that... I panicked for a second. Then noticed that everyone else was getting that. Well cool, thanks for shedding some light on the subject.

---

### Post by howefield on 2010-02-20
Some detail in this thread.

[http://code.google.com/p/chromium/issues/detail?id=35639](http://code.google.com/p/chromium/issues/detail?id=35639)

> This was an attempt to consolidate our DEB deps on the more generic 'lsb' package 
(similar to what the RPM packages use). Unfortunately, that pulls in a lot of stuff 
that isn't installed by default on some DEB distros, so I'm reverting to the 'lsb-
base' dependency we had before.

---


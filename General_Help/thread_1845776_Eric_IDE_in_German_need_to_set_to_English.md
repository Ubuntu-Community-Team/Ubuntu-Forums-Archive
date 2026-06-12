---
title: "Eric IDE in German need to set to English"
date: 2011-09-17
forum: General Help
---

### Post by acidblue on 2011-09-17
Just installed the Eric IDE for python but it's all in German.
How do I set to english???

---

### Post by gmargo on 2011-09-17
Where did you get **eric**, and what system are you installing on, and what is the locale?

I installed **eric** 4.4.4a-1 from the 64-bit 10.10 Maverick repository, and it seems to be all in English for me.  At least all the menus and visible text when it starts up.

---

### Post by acidblue on 2011-09-17
I got it from the repo's
I'm on Ubuntu 10.10.
It's all in German.

---

### Post by gmargo on 2011-09-17
The rest of the system is in English for you?  Are you using some mixture?

What is the output of the "locale" command?

---

### Post by acidblue on 2011-09-17
My locale is all english
LANG=en_US.utf8
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=

Just need help changing eric to english can anyone help?

---

### Post by gmargo on 2011-09-18
Very strange.  I've no idea why.  I didn't have a german locale available on my system, but even after I generated one, everything was still english.

I managed to force eric into german by running "LC_ALL=de_DE.utf8 eric", but afterwards "eric" alone still gives me english.

What if you run "LC_ALL=C eric"?  That should force it to english.

---

### Post by acidblue on 2011-09-18
No doesn't work, still in German.

---

### Post by gmargo on 2011-09-18
Too strange.  I'd have thought there was no way that "LC_ALL=C" could fail.  How about the output of "locale -a"?

I wonder what would happen if you removed (or renamed) /usr/share/qt4/translations/eric4_de.qm?

---

### Post by acidblue on 2011-09-18
Output of locale -a
C
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

Renaming eric4_de.qm seems to work, it's all in english now, so far.
Why it was in German I have no idea

---


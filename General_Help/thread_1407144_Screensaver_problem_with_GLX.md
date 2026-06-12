---
title: "Screensaver problem with GLX"
date: 2010-02-14
forum: General Help
---

### Post by eraevous on 2010-02-14
I don't know what I'm missing or what I did to break it, but most screensavers that I have end up returning this error message:
"X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16"

This is also the output of glxinfo. I've been searching around on the forums and elsewhere online, but I believe I've hit the limit of my understanding about what's going on. Did I somehow break something in my graphics driver? Is there other information that I can give to help fix this?

---

### Post by davelbarton on 2010-02-25
Bump.

I am having the same problems.  glxinfo gives:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

I am using Ubuntu Koala, with gnome, on an HP dv7-1130 laptop.  No screensaver will operate, with either xscreensaver or gnome-screensaver.  Crash, crash, crash.

Please, can anyone help?

---

### Post by davelbarton on 2010-03-02
Bump.  In desperation.  Please, someone knowledgeable help.

---

### Post by eraevous on 2010-03-02
I wish I could help you somehow, but all I managed to do was break X and then wipe and install, sorry. :-(

---

### Post by hansdown on 2010-03-02
Hi davelbarton and eraevous.

I can't help, but this seems to be a video driver issue, mainly ati.

[http://www.google.ca/search?q=+X+Error+of+failed+request%3A+BadRequest+(invalid+request+code+or+no+such+operation)+Major+opcode+of+failed+request%3A+135+(GLX)+Minor+opcode+of+failed+request%3A+19+(X_GLXQueryServerString)+Serial+number+of+failed+request%3A+14+Current+serial+number+in+output+stream%3A+14&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=+X+Error+of+failed+request%3A+BadRequest+(invalid+request+code+or+no+such+operation)+Major+opcode+of+failed+request%3A+135+(GLX)+Minor+opcode+of+failed+request%3A+19+(X_GLXQueryServerString)+Serial+number+of+failed+request%3A+14+Current+serial+number+in+output+stream%3A+14&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---


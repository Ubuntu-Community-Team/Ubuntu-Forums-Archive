---
title: "Thunderbird opens, then closes."
date: 2010-06-03
forum: General Help
---

### Post by HereInOz on 2010-06-03
Hi All,

I have just upgraded to 10.04 (64 Bit) and now when I open Thunderbird it opens, then after a second or so, it closes.  When run from a terminal, I get this error:

/usr/lib/thunderbird-3.0.4/run-mozilla.sh: line 131:  2565 Segmentation fault      "$prog" ${1+"$@"}

I have tried it with -safe-mode but it makes no difference.  I had the lightning extension installed, and apparently this causes the behaviour sometimes, but I can't get in to Thunderbird to re-install Lightning.

Does anyone have any ideas?  Hope you can help.

---

### Post by -humanaut- on 2010-06-03
You might be better off purging it from your system and reinstalling it hard to say what happened

---

### Post by derekeverett on 2010-06-03
When you say you just "upgraded" to 10.04 what do you mean exactly?

Was it a fresh install from a CD? I've had problems with upgrading with Ubuntu's updade manager.

---

### Post by ajgreeny on 2010-06-03
Rename the hidden ~/.mozilla-thunderbird and ~/.thunderbird folders in your home as backups.  Don't delete them as they contain all your emails.

Start thunderbird again and new profiles will be made into which you can copy all the mail folders from the old profile.

There is a beta version of lightning which runs well in TB3, which you can get direct from the [https://addons.mozilla.org/en-US/thunderbird/](https://addons.mozilla.org/en-US/thunderbird/) site as the .xpi and install with the Tools -Add-ons menu dialog.  I have it running here with no problems.

---

### Post by HereInOz on 2010-06-03
Thanks heaps guys.  In the process of rebuilding the email accounts now.

---


---
title: "Assume root priviledges when opening something"
date: 2010-09-09
forum: General Help
---

### Post by Zintha on 2010-09-09
Hi there wonderful folks. Been a while since I asked a question here so here goes.

I recently got a new printer and wanted to set it up to work with Linux shortly after I got it working in windows OS and found Linux specific software on their website.

> [http://support.lexmark.com/index?page=recommendedDownloads&productCode=LEXMARK_X4650&segment=DOWNLOAD&userlocale=en_US&locale=en#1](http://support.lexmark.com/index?page=recommendedDownloads&productCode=LEXMARK_X4650&segment=DOWNLOAD&userlocale=en_US&locale=en#1)

Fantastic, however when using it it prompts for the root password but rejects anything I put into it. Including obviously the correct password.

So, is there a way of getting around this?

---

### Post by bodhi.zazen on 2010-09-09
use sudo -i for a root shell or gksu for graphical applications.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by sikander3786 on 2010-09-09
For installing Lexmark printers you need a real root account. And posting the instructions for setting up a root password on ubuntuforums.org is discouraged/disallowed.

This thread might help.

[http://ubuntuforums.org/showthread.php?t=1482287](http://ubuntuforums.org/showthread.php?t=1482287)

---

### Post by bodhi.zazen on 2010-09-09
> **sikander3786 said:**
> For installing Lexmark printers you need a real root account. And posting the instructions for setting up a root password on ubuntuforums.org is discouraged/disallowed.

This thread might help.

[http://ubuntuforums.org/showthread.php?t=1482287](http://ubuntuforums.org/showthread.php?t=1482287)

```
sudo -i
``` is sufficient. No need to set a root password.

---


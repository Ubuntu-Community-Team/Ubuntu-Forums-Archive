---
title: "cyrillic filenames corrupted after crash"
date: 2010-11-02
forum: General Help
---

### Post by aeol13 on 2010-11-02
Everything was fine after fresh install of kubuntu 10.10 on my laptop, until today.
I was exploring system settings (didn't change anything, just looking) when KDE crashed suddenly. After restart I found all my filenames with Russian letters corrupted - just like filesystem was mounted with wrong encoding. How can I get them back to normal? Any help would be appreciated.

---

### Post by aeol13 on 2010-11-02
Finally I managed to get my file names back. The problem had nothing to do with KDE crash (it's still a question why it crashed), but rather with some locale settings. Strangely this line in my .profile did all the mess:
export LC_TIME=en_DK.utf8
I removed it and everything is ok.

---


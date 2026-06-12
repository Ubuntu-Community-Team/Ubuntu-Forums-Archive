---
title: "Bizarre Firefox 3.5.2. defaults to open Open Office always even zip, tar, pdf , etc"
date: 2009-09-07
forum: General Help
---

### Post by dubref on 2009-09-07
Ubuntu 9.04 here.

Experiencing very strange behaviour with Firefox 3.5.2. Trying to open any type of file extension(.pdf, .rar, .zip, .c, etc) from Downloads screen results in opening of Open Office... which is not a good idea most of the time.

When OO opens I get either ASCII Filter Options or Filter Selection prompt. 

In Nautilus, this doesn't happen, clicking on say .zip opens File Roller, the way it is by default, and the way it used to be with previous versions of Firefox.

Any ideas to try to fix this? Default downloads open behaviour is not specified in Preferences -> Applications .

Thus, I imagine answer lurks somewhere in about:config?

All I did to get into this mess is
upgrade from Firefox 3.0.13 to 3.5.2 with
```
sudo apt-get install firefox-3.5
```
(and changed symlink in /usr/bin for firefox from firefox-3.0  to firefox-3.5 but that shouldn't matter)

OO is standard 3.0.1


EDIT: just checked and Firefox 3.0.13 continues to work normally, that is clicking on .pdf file in Downloads opens a pdf viewer.

---

### Post by squenson on 2009-09-12
In Firefox, click on the menu Edit > Preferences > Applications and see the associations between the file extensions and the applications to launch. Something is most probably wrong in this list.

---


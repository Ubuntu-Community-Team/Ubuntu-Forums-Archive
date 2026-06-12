---
title: "wrong cyrillic symbols in gedit"
date: 2010-01-05
forum: General Help
---

### Post by malovanyy on 2010-01-05
Using Ubuntu 9.10. Cyrillic console works good, Cyrillic symbols are displayed good in *.doc files, I can type in Cyrillic in all the programs, cyrillic symbols are displayed good in filenames.
But when I open a *.txt file with cyrillics, the letters are messed up. Very similar to what was explained here:
[http://ubuntuforums.org/showthread.php?t=178372](http://ubuntuforums.org/showthread.php?t=178372)
though this post does not provide a solution..
Used the tutorial in Russian here:
[http://web.opennet.ru/docs/HOWTO-RU/Cyrillic-HOWTO.html#ttfonts](http://web.opennet.ru/docs/HOWTO-RU/Cyrillic-HOWTO.html#ttfonts)
with no help (created files fonts.dir, fonts.scale and encodings.dir in the folder with Windows true type fonts).

What else can be wrong?? Is it a mounting or fonts problem. Just in case here are two lines from fstab, where I mount Windows drives:
/dev/sda1 /media/WIN-C ntfs   defaults                          0  0  
/dev/sda6 /media/WIN-D vfat   codepage=866,iocharset=utf8,user  0  0
The problem is the same with txt files on both drives.

Thank you in advance

---


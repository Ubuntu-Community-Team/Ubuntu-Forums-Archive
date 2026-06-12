---
title: "transporting applications"
date: 2009-10-15
forum: General Help
---

### Post by sreerajan on 2009-10-15
i have an ubuntu installed in my system...recently i installed mint linux too. is there some way by which i can get the applications installed in ubuntu to mint..any help???

---

### Post by hwttdz on 2009-10-15
You might be able to move /usr/bin to a different partition and mount that partition in both mint and ubuntu, though that might confuse the package manager in either or both.  

Another possibility is to install all the same packages (or at least those that exist on both), and you could even make a script that checks if something has been added or removed on the other os every time you change.  Here's how to get started with that approach [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366) , the downside here of course is that some packages may differ in name and you're using more hard disk space.

---


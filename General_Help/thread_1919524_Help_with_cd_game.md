---
title: "Help with cd game"
date: 2012-02-03
forum: General Help
---

### Post by dannychoban on 2012-02-03
Hi i tried to install fate a cd game and i keep getting the "unexecutable file" message but whenever i try to change the permissions in properties... it wont let me because "this file is read only"

im really desperate because ive been stuck with this problem for weeks!!

please help me out!

---

### Post by Rodney9 on 2012-02-03
Fate is a Windows game, are using Wine ?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9174&iTestingId=15600](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9174&iTestingId=15600) 

shows poor results using Wine from long ago, but maybe the latest Wine would work, you could try.

This one shows it working with a work around ???

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9174&iTestingId=58689](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9174&iTestingId=58689)

Rodney

---

### Post by 3rdalbum on 2012-02-03
Go into the terminal.

Type 'wine ' (without the quotes) and make sure you leave a spacebar character at the end. Now drag the program you want to install, to the terminal. Click on the terminal to bring it back to the front and you'll find that the program's file path has been filled in. Press Enter and the program will run.

Note that Wine won't run all programs - my estimate is that it runs about 30% of Windows programs. Use Wine as a last resort.

---


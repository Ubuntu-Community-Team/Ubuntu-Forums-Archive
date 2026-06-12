---
title: "scanning"
date: 2011-05-21
forum: General Help
---

### Post by Sissy61 on 2011-05-21
I have a Brother printer MFC 210C I am tring to scan . the printer advise it's connceting to the Pc. Then nothing happens. What else do I need to do Thank you.

---

### Post by hulkman on 2011-05-21
I've done a quick search in the terminal for "mfc 210c" and it comes back with two drivers.  You may only need one of them, I don't.  To install them open Accessories;Terminal and enter one or both of the following commands:

sudo apt-get install brother-cups-wrapper-extra
sudo apt-get install brother-lpr-drivers-extra

-----------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a place to go for deb packages.

---


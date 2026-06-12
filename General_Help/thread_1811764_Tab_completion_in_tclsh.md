---
title: "Tab completion in tclsh?"
date: 2011-07-25
forum: General Help
---

### Post by conradin on 2011-07-25
Hi Everyone,
I am using the tclsh and wish commandlines frequently. I have noticed that I dont have tab complete in either of these shells, which is anoying.
is there anyway to get this feature in tclsh and wish shells?

---

### Post by undeuxtrois on 2011-07-27
Hello,

the tclreadline package provides history and file name completion features for tclsh/wish. It makes it a lot more fun to work with the tcl interpreter !

[http://tclreadline.sourceforge.net/](http://tclreadline.sourceforge.net/)
sudo apt-get install tclreadline

P.

---

### Post by conradin on 2011-07-29
Hey, Thanks, Ill give it a try in a bit!

---

### Post by conradin on 2011-08-07
well, I went to the tclreadline site, and had a look. I tried to install, but  I couldnt locate a .tclshrc  folder anywhere. (Yes, I know its a hidden file, and I know how to find those) but straight up, I cant find where, or how to get this tclreadline program to install. Ive been using tclsh from the expect 8.5 package. Should I get something else??

---


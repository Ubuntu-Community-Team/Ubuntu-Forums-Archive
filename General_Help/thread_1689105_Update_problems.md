---
title: "Update problems"
date: 2011-02-16
forum: General Help
---

### Post by typos1 on 2011-02-16
I ve got updates ready to install but halfway through downloading I get a message saying it couldnt get a password or something. 

So I enabled unsupported updates, but it still did it. 

So then I disabled them again and it said I had a broken package (ia32-libs) and to run apt-get install -f in a terminal after unchecking 3rd party updates, so I unchecked 3rd party updates, but when I type in a terminal it says permission denied and asks if I m root.

It would normally ask for a password in the terminal to root me, dont know how to do it any other way.

---

### Post by David D. on 2011-02-16
Did you remember to put "sudo" in front of the apt-get install -f?

---

### Post by typos1 on 2011-02-16
No, I just typed what I was told to type, kinda thought it would have said sudo apt get if thats what it meant!

Still sorted now-thanks

---


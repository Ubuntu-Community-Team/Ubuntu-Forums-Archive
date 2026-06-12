---
title: "How to undo a symybolic link?"
date: 2006-03-12
forum: General Help
---

### Post by magomago on 2006-03-12
Hey guys I've been playing with the whole Xgl, composites, compwiz stuff recently but for now I want to STOP with it.  When I tried to swtich back I got errors and couldn't boot up.  Looking around and tinkering I figured out how to get back the original setup.  But there is one slight problem:  GDM never starts automatically.  It gives me an error about how some location is invalid (too lazy to restart to check right now), but if I log in and do a startx it errors but the screen goes away and things start...

anyways looking more I noticed I did this command (i tried mixing a few faqs)

sudo ln -sf /usr/X11R6/bin/Xgl /usr/bin/Xgl


now I want to undo that....can anyone assist me?

---

### Post by kaamos on 2006-03-12
sudo rm /usr/bin/Xgl

---


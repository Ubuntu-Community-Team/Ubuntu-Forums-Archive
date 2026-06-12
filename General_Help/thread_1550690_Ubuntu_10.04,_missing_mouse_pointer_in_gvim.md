---
title: "Ubuntu 10.04, missing mouse pointer in gvim"
date: 2010-08-11
forum: General Help
---

### Post by terry_opie on 2010-08-11
Fresh install of 10.04 on a Lenovo Thinkpad W500.  

I use gvim for all of my development.  Using the the vim-gnome package.  I've noticed that most times (but not always), the mouse pointer is "invisible" while over the gvim window.  I've found that if I click to highlight text, it will show up again.

Some investigation has found that once I search for something, the cursor will disappear again.

Anyone else seeing this?  Solutions?

Thanks!

---

### Post by lang2 on 2011-01-11
I'm having the same problem. Unfortunately ubuntu doesn't make it easy to compile my own.

---

### Post by lemsx1 on 2011-04-18
I also was annoyed by this. The fix is to do:

:set nomousehide

Then restart Gvim/vim

[https://bugs.launchpad.net/ubuntu/+source/vim/+bug/616858](https://bugs.launchpad.net/ubuntu/+source/vim/+bug/616858)

---

### Post by terry_opie on 2011-04-18
Yep... I know what the workaround was.  I opened the bug report.  Sorry I didn't report back.

---


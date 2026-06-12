---
title: "Karmic virtual terminal transparancy issue"
date: 2010-01-04
forum: General Help
---

### Post by rowbird on 2010-01-04
Hi all, I have just installed 9.1 and I like to use a semi-transparent terminal so i can see text under it, but on Karmic, it shows the desktop background underneath. Any ideas how to fix this? Thanks

---

### Post by Saiko Berry on 2010-01-04
Well if you want it to not xray (It shouldnt anyways) just set transparency in a normal terminal window like for instance Guake or urxvt. To do it for urxvt you have to fiddle a bit with the flags.

For example, make a file called .Xdefaults in our home ~/* directory, put the following;

URxvt.transparent: true
URxvt.inheritPixmap: true
URxvt.foreground: white

Then open a terminal (uRXVT if youre using it ;)) and do;
$ xrdb merge .Xdefaults

Then rerun uRXVT.

---

### Post by mcduck on 2010-01-04
> **rowbird said:**
> Hi all, I have just installed 9.1 and I like to use a semi-transparent terminal so i can see text under it, but on Karmic, it shows the desktop background underneath. Any ideas how to fix this? Thanks

You need to have visual effects enabled (Compiz or some other compositing manager running) for any real transparency. If compositing manager isn't running Gnome-terminal uses fake transparency as fallback solution.

---

### Post by rowbird on 2010-01-04
Thanks guys, I had to activate Compiz. now it works.

---


---
title: "tar.bz2 and no configure file"
date: 2011-03-07
forum: General Help
---

### Post by hockeytux on 2011-03-07
Im trying to install a program (Celtx, a media pre-production assistant) that Ive downloaded as tar.bz2 file.

Ive unpacked it, moved it into my Home folder, and then wanted to configure, make and install it through the terminal.

However theres no configure file (and no readme, help or install file either for that matter).

I can cd to the Celtx folder in the terminal and then start the program with ./celtx but thats a bit tedious.

How would I install it 'properly' if the ./configure command doesnt work? Any ideas?

---

### Post by TeoBigusGeekus on 2011-03-07
If you can run the program from its folder, then perhaps it's not a source package.
Just create a menu entry in your applications menu with the command
```
/path/celtx
```

---

### Post by hockeytux on 2011-03-07
That did the trick, though I simply right-clicked the Applications menu and added it (ie the celtx shell script file) as a new item. Thanks :D

---


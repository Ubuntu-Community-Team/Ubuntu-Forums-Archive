---
title: "changing GRUB settings."
date: 2011-06-29
forum: General Help
---

### Post by Nekrose483 on 2011-06-29
i'm sure you all know backtrack.. i'll just use that for an example... 

it boots up in CLI mode... and asks you to login... root... toor.. enter..

then its just CLI until you type startx. then it starts XFCE.. or in the BT5 that just came out.. it starts up with KDE or GNOME.. what ever you chose at download time.

anyway, i really like the starting up in CLI idea. i asked a friend how to do it..

he said to change

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
  to
  GRUB_CMDLINE_LINUX_DEFAULT="text"

did that.. its boots up in all black... nothing happens...

booted in single mode and fixed it. :C

so, just wondering how to get it to boot like that...

it'd be nice to have a CLI greet you.. do some work.. if you rally need the GUI then type "startx"

---

### Post by jerrrys on 2011-06-30
should find that here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=boot+to+cli&sa=Search&cof=FORID:9#911](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=boot+to+cli&sa=Search&cof=FORID:9#911)

---

### Post by Nekrose483 on 2011-06-30
none of that actually helped... i'm using 11.04.... eveything else is fo the olde vesions

---

### Post by jerrrys on 2011-06-30
can't just go by versions, command line is still command line.  but check this one out
[http://ubuntuforums.org/showthread.php?p=10991674#post10991674](http://ubuntuforums.org/showthread.php?p=10991674#post10991674)

---


---
title: "Installed debian in pendrive nd lost grub. No grub if pendrive is not connected. HELP"
date: 2011-03-13
forum: General Help
---

### Post by gkkrish on 2011-03-13
So here is my situation.. 
i was using win 7 and ubuntu 10.10 in my dell studio 1555.

and i wanted to try out debian so i installed debian in my pendrive. so the grub was modified.  

when the computer starts it shows debian,ubuntu and win7 no problem.. but if i remove the pendrive, nothing comes up.
it shows grub rescue>..

so now i cant start up unless i plug in the pendrive.

what to do now to solve this problem?? i want to restore my grub to the previos state... PLEASE HELP!! :( :(

---

### Post by gkkrish on 2011-03-13
Solved it...

logged into ubuntu with pendrive pluggd in..

installed grub2..
sudo apt-get install grub2

removed pendrive.

sudo update-grub.

Problem solved.. :) :)

---

### Post by mimor on 2011-03-13
> **gkkrish said:**
> Solved it...

logged into ubuntu with pendrive pluggd in..

installed grub2..
sudo apt-get install grub2

removed pendrive.

sudo update-grub.

Problem solved.. :) :)

Nice ;)
I'm glad for you.
Can you mark your thread as solved plz?

---


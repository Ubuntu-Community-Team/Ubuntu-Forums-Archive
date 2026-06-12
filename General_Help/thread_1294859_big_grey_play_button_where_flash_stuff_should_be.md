---
title: "big grey play button where flash stuff should be"
date: 2009-10-18
forum: General Help
---

### Post by duffy_ryan on 2009-10-18
Hey all, whenever I try to view anything flash, instead i get a big grey play button (non-functioning) instead. Has anyone heard of this? I have flash 10 installed. thx.

---

### Post by fooman on 2009-10-18
do you have any gnash or swfdec items installed?  

open synaptic (system > administration > synaptic package manager) and search for "flash".

make sure that no gnash or swfdec (including libswfdec) items are installed.  if they are...uninstall them.

the only items that should be installed are flashplugin-nonfree and/or flashplugin-installer.

close and restart firefox if it is open,  then test.

hope that helps.

---

### Post by duffy_ryan on 2009-10-18
Worked great! Thanks! Just out of curiosity, why was it the way it was? libswfdec and swfdec-mozilla were both installed. Thanks again for the help!

---


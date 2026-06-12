---
title: "OpenBox acting weird !!!!!"
date: 2011-09-04
forum: General Help
---

### Post by evilheart on 2011-09-04
hi , 

lately i had several problems with open box ,when i click "close , restore , minimize " the window only get restored , as if they are not there at all.


also i have to click on the title bar , to switch between windows on the same screen , instead of clicking any where as usual.

at the startup a message appears saying there's a problem with the rc.xml file , saying something about  the ending of line 406.


also the OpenBox configuration manager doesn't start , it gives me an error 

```
Error while parsing the Openbox configuration file.  Your configuration file is not valid XML.

Message: Premature end of data in tag openbox_config line 4

 
```

i tried re-installing from synaptic but nothing changed , it seems the rc.xml is corrupted , any way to fix it , or make a fresh new copy of it?

---

### Post by evilheart on 2011-09-04
ok , it's fixed , 

i re-installed openbox , but the problem still there , then i deleted the lubuntu-rc.xml file placed in home/~/.config/openbox

and the problem was fixed , new file was created , but i had to recongfigure openbox (not a big deal).

i hope that may help someone.

---


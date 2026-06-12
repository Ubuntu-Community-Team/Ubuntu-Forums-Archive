---
title: "Deskbar Applet Problem"
date: 2010-05-07
forum: General Help
---

### Post by gameplay on 2010-05-07
Upgraded to 10.04 and have a problem I can't solve/don't know what to do with as I am not a linux expert.

On startup I now get a message which reads 

"Panel encountered a problem while loading OAFII:Deskbar-Applet Do you want to delete the Applet from your configuration" 

I don't know the cause of this or what the consequences of deleting it would be. At the moment I select 'dont' delete' and the system appears to be working fine.

So: waht is the cause and can I just delete it?

---

### Post by gameplay on 2010-05-10
Any help appreciated.

---

### Post by dino99 on 2010-05-10
metacity --replace

sudo dpkg --configure -a

---


---
title: "How to uninstall XGL in Breezy"
date: 2006-04-07
forum: General Help
---

### Post by suribe on 2006-04-07
Hi 
How can i uninstall xgl from Breezy?

My PC goes slow with them and I want to remove but I am not sure about the steps.
Thanks in advance

---

### Post by testube_babies on 2006-04-08
[QUOTE=suribe]Hi 
How can i uninstall xgl from Breezy?

My PC goes slow with them and I want to remove but I am not sure about the steps.
Thanks in advance[/QUOTE]

Did you install XGL using a specific tutorial?  If so, please post a link.

---

### Post by sands on 2006-04-08
[http://ubuntuforums.org/showthread.php?t=133772](http://ubuntuforums.org/showthread.php?t=133772)

---

### Post by testube_babies on 2006-04-08
If that is the tutorial you used, then this should do it:

cd /etc/gdm
sudo cp gdm.conf gdm.conf.xgl
sudo mv gdm.conf.backup gdm.conf

---

### Post by suribe on 2006-08-26
:)  Thanks!

---

### Post by jsiii on 2006-09-06
I also have big problems with uninstalling XGL. I actually reinstalled the Ubuntu keeping my /home directories. Now my windows are missing captions and I see other strange behaviour.

Full description of my problem is here:
[http://www.ubuntuforums.org/showthread.php?t=251524](http://www.ubuntuforums.org/showthread.php?t=251524)

---


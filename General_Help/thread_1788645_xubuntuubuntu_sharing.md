---
title: "xubuntu/ubuntu sharing"
date: 2011-06-22
forum: General Help
---

### Post by nick3501 on 2011-06-22
laptop with ubuntu 11.04 on wireless. Desktop with xubuntu 11.04 wired to the router.  I managed to share folders on my laptop by right clicking and hitting simply sharing the folder (after installing required package when prompt. However, so such option seems to exist on Xubuntu. I want to be able to play all the music off my desktop on my laptop , but it seems i can only get it working backwards.

how to share folders in xubuntu?

---

### Post by derklempner on 2011-06-23
> **nick3501 said:**
> laptop with ubuntu 11.04 on wireless. Desktop with xubuntu 11.04 wired to the router.  I managed to share folders on my laptop by right clicking and hitting simply sharing the folder (after installing required package when prompt. However, so such option seems to exist on Xubuntu. I want to be able to play all the music off my desktop on my laptop , but it seems i can only get it working backwards.

how to share folders in xubuntu?
You need to follow the instructions on how to manually configure Samba server found [[COLOR="Red"]_here_[/COLOR]]("https://help.ubuntu.com/community/Samba/SambaServerGuide#Samba Server Configuration - Manual").  It's one configuration file you'll need to edit, making sure you have the **samba** package installed (*sudo apt-get install samba*).  And don't forget to make sure your firewall settings are also configured for Samba shares (if you use a firewall).

---


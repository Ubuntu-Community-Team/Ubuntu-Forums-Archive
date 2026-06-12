---
title: "permanent left-handed mouse in lubuntu/LDXE"
date: 2012-04-02
forum: General Help
---

### Post by joeyjoejoejunior on 2012-04-02
Hello,

I'm trying to permanently switch the right- and left-click buttons on my mouse in lubuntu/LDXE.  I've gone into lxinput and selected 'Left Handed', however, when I reboot it reverts to right-handed.  I love lubuntu/LDXE, but this could be a deal-breaker.
Any fellow lubuntu lefties?

Thanks

---

### Post by Rex Bouwense on 2012-04-02
Menu->Preferences->Keyboard and Mouse and tick Left handed.  That's the easy way.

---

### Post by joeyjoejoejunior on 2012-04-02
> **Rex Bouwense said:**
> Menu->Preferences->Keyboard and Mouse and tick Left handed.  That's the easy way.
Thanks for the reply, but the method you described is how I accessed 'lxinput'.  When I tick the left-handed option it still reverts upon reboot/logout.
Any ideas of how to make it permanent?

---

### Post by mcgrady911 on 2012-04-14
I would try navigating to and edit the following file:
/etc/xdg/lxsession/Lubuntu/desktop.conf

I think you put a "1" in the left handed mouse parameter and then do a reboot.  That should take care of it.

---


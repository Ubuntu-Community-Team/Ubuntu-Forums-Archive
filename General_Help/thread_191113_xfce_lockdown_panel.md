---
title: "xfce lockdown panel ??"
date: 2006-06-07
forum: General Help
---

### Post by oly on 2006-06-07
i am resycling old computers at the school i work so i need a lean desktop ie xfce however i also need to be able to lock the panels and preferences so that users can not modify them, like kde kiosk mode and gnome kiosk mode.

any way i can do this, i have read that kde supports a kiosk mode but could not find anything on locking preferences and panels.

any help appreciated

---

### Post by psychicdragon on 2006-06-07
Xfce documentation is pretty out of date ATM. These links are to the docs for 4.2, so I'm not sure if all the information is still correct.

[http://www.xfce.org/documentation/docs-4.2/xfce4-session.html#xfsm-kiosk-mode](http://www.xfce.org/documentation/docs-4.2/xfce4-session.html#xfsm-kiosk-mode)
[http://www.xfce.org/documentation/docs-4.2/xfce4-panel.html#panel-kiosk](http://www.xfce.org/documentation/docs-4.2/xfce4-panel.html#panel-kiosk)

---

### Post by oly on 2006-06-07
thxs for that one more quick question any one know where this is ${sysconfdir}/xdg/xfce4/kiosk/kioskrc

what is the ${sysconfdir} ? 
else i am cluless where to create the file

---

### Post by xtacocorex on 2006-06-07
I think that might be /etc since that is where the system base configuration files are stored.

I've never tried this, but that makes sense to me.

EDIT: I just found this: [http://svn.xfce.org/svn/xfce/xfdesktop/trunk/doc/README.kiosk](http://svn.xfce.org/svn/xfce/xfdesktop/trunk/doc/README.kiosk)

Check the first paragraph, it says that it's /etc.

---

### Post by oly on 2006-06-07
thanks alot that is great :)

---

### Post by oly on 2006-06-09
still having issues with this have written the kioskrc file and placed it in /etc/xdg/xfce4/kiosk/ path but none of the restrictions happen.

any idea alternatively can i lock the config files for xfce so the the prefs can not be saved or would this cause other problems ??

---


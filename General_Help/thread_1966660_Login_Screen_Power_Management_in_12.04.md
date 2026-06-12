---
title: "Login Screen Power Management in 12.04"
date: 2012-04-27
forum: General Help
---

### Post by compmodder26 on 2012-04-27
Hopefully this has a simple answer.  How do I change the power management settings for the login screen.  Right now if I close my laptop lid when the login screen is up, it sends the computer into suspend.  I don't want this to happen as this breaks functionality for my nightly backups.  Running 12.04.

---

### Post by IWantFroyo on 2012-04-27
Hit the little cog in the top right corner of the screen (while signed in), and select System Settings. Then select Power. Now change the settings for when you close the lid.

I don't know whether or not it will still apply on the login screen. You may want to remain logged in and let it simply lock, but not Suspend/Hibernate.

---

### Post by compmodder26 on 2012-04-27
> **IWantFroyo said:**
> Hit the little cog in the top right corner of the screen (while signed in), and select System Settings. Then select Power. Now change the settings for when you close the lid.

I don't know whether or not it will still apply on the login screen. You may want to remain logged in and let it simply lock, but not Suspend/Hibernate.

Yeah I've done that already but it doesn't apply to the login screen.  I've even installed gnome-tweak-tool and ran it as root with no luck.  I figure that's because the settings that those GUIs hit are for Gnome only and do not apply to LightDM.  But I cannot figure out how to change the settings for LightDM.

I have figured out that if I quickly close the laptop right after I click to log out, then my own user's power settings are taken into account and the laptop will not suspend.  So that is one workaround, but I would still greatly prefer to be able to change the power settings for LightDM.

---

### Post by compmodder26 on 2012-05-01
Bumping.  Still have not found a solution to this.

---


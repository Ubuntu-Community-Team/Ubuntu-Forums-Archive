---
title: "XULrunner 1.9.2 cripples Karmic Help and Support browser"
date: 2009-11-25
forum: General Help
---

### Post by Kirk M on 2009-11-25
I'm currently testing Firefox 3.6 builds (code name: "Namorka") in Karmic Koala. Firefox 3.6 uses XULrunner 1.9.2 which, when installed, cripples Ubuntu's "Help and Support" browser by not allowing it to load any help page with these errors:

**When first opening "Help and Support":**

    [I]Unable to load page

    The requested URI "file:///fakefile#index" is invalid[/I]

**If I enter a search term I get this:**

   [I] Unable to load page

    The requested URI "file:///fakefile#results" is invalid[/I]

Uninstalling XULrunner 1.9.2 returns "Help and Support" back to normal but that's not an option. I haven't uninstalled Firefox 3.5.5 or XULrunner 1.9.1, BTW.

Firefox 3.6 will be released before the years end and many people running Ubuntu will be installing it and having a vital component of the browser crippling Ubuntu's "Help and Support" browser is really not acceptable.

Does anyone have any insight, possible solutions or ideas about this or am I just missing something here? ](*,)

---

### Post by matthewn on 2009-11-25
FWIW, I have the same problem. I looked in galternatives to ensure xulrunner 1.9.1 is the default, and it is. The help browser won't run unless I uninstall xulrunner 1.9.2.

---

### Post by Kirk M on 2009-11-25
> **matthewn said:**
> FWIW, I have the same problem. I looked in galternatives to ensure xulrunner 1.9.1 is the default, and it is. The help browser won't run unless I uninstall xulrunner 1.9.2.

Okay, for what it's worth I did two things and now "Help and Support" is working again. I reinstalled *Firefox 3.6, Firefox 3.6 Branding, Firefox 3.6 Gnome support* and *XULrunner 1.9.2* today (I had already added the respective repository previously so I could get regular updates to Thunderbird 3.0 builds) and then used the Update Manager to bring everything up to date. Then, using the Firefox 3.6 Preferences/Advanced tab, I set it to be the default browser (it wasn't). Now "Help and Support' is working correctly.

---

### Post by libssd on 2010-05-15
Thanks for sharing your experiences. I was just about ready to uninstall Firefox 3.6 and revert to the Canonical distribution of 3.0. After a night of sleep, I decided to reinstall XULrunner, and while doing so, discovered that yelp,
gnome-doc-utils, and ubuntu-docs were all uninstalled! Help works now, and I am a happy camper again. :KS

---


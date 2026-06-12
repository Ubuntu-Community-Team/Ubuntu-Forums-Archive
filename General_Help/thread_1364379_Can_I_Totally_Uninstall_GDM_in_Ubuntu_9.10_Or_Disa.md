---
title: "Can I Totally Uninstall GDM in Ubuntu 9.10? Or Disable Xfce/Xubuntu Login Screen?"
date: 2009-12-25
forum: General Help
---

### Post by OzzyFrank on 2009-12-25
I'm running 9.10 64-bit and, as many of you have realised by now, the old **GDM** has been replaced with **[COLOR="Indigo"]XSplash[/COLOR]**. I'm not here to whinge about that, since I already know how to **[change every aspect of the login process]("http://ubuntugenius.wordpress.com/2009/12/25/customise-the-gdmxsplash-login-screen-in-ubuntu-9-10/")**.
What I want to know is am I supposed to have GDM still installed, or is this solely because I also have Xfce/Xubuntu on the same machine (and KDE/Kubuntu, but that isn't relevant in this case)? I assume this may be so since Xfce uses many parts of Gnome, like the GDM. So I am guessing while Gnome has made the jump to XSplash, Xfce is still using Gnome's GDM.

Anyway, the reason I ask is I actually have a mish-mash at the login screen, being some aspects of the new XSplash - like the background and throbber - with old Xfce-themed GDM remnants, like the panel and user-list window (after upgrading to 9.10, the login was completely Xfce-themed GDM, but I've changed bits to XSplash).

I'd pretty much like to just go with XSplash and not run some mutated hybrid, so should I uninstall GDM, or will this have consequences? Or is there a way to "change back", like how you can pick either GDM or KDM when you run **sudo dpkg-reconfigure gdm**? I Googled and saw lots of mention of Xubuntu having **XDM** as the login manager, but that info is either just incorrect or outdated, and even if it wasn't there doesn't seem to be a way to change to it.

A note of interest is that when I chose to logout and then specifically to switch user, I got to a totally XSplash-themed login, but upon rebooting it is back to the hybrid login.

Any light on this would be appreciated.

---

### Post by Leppie on 2009-12-25
Scott James wrote [this article on xsplash]("http://www.netsplit.com/2009/09/02/making-a-splash/"). It may shed some light on it.

---

### Post by OzzyFrank on 2009-12-25
Yeah, I read that article already as a matter of interest on the subject, but there isn't actually any relevant info regarding my question, just boot time comparisons, hehe. And lots of talk of RedHat. Unfortunately, no mention whatsoever regarding anything I've asked about. Thanks anyway.

---

### Post by blueridgedog on 2009-12-25
On my 9.10 system with Gnome, disabling gdm results in a normal console login and a need to startx manually, so I assume it is still used.

I disabled mine by renaming /etc/init/gdm.conf and rebooting (as a test in another thread regarding creating a text based login).

---

### Post by Leppie on 2009-12-25
well, it states close to the end that normally xsplash should handle things, unless user imput is required before getting to the login screen (for like encryption keys, etc.).
> But what if we have to check the filesystem, or enter a decryption passphrase to mount it?  That&#8217;s why we still have usplash.  In those cases we will start usplash to display the progress or request the key.

---

### Post by OzzyFrank on 2009-12-25
Figured as much. Though I'm even more confused now, hehe. I imagine there has to be a way to let XSplash take over the whole login, or disable Xubuntu's theming of GDM, or something, so hopefully some clever soul shares this info with us soon.

---

### Post by fooman on 2009-12-25
have you tried startupmanager?

---


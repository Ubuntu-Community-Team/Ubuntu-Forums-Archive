---
title: "Intermittent blank login screen."
date: 2010-05-03
forum: General Help
---

### Post by haihovu on 2010-05-03
I just upgraded my home work station from 9.10 to 10.04 and have been plagued by this intermittent problem: after logging out of a desktop session (Gnome), I am presented with a blank black screen, instead of the login screen, no cursor is displayed, the keyboard is dead. The system is still operational in some aspect since I can go to my Windows laptop and XRDP into my Ubuntu workstation and everything seems OK, allowing me to issue a graceful restart. This had only been observed about three times out of a dozen or so session login/logout, typically after I install/uninstall some indicator packages.

Can someone advise on how to diagnose the root cause of this problem, thanks.

---

### Post by haihovu on 2010-05-23
Still happening, the last three times this occurred nothing significant was done prior to logging out, just normal web browsing and so on. Review of the various log file did not reveal anything unusual looking, it's just as though xdm or gdm conked out after logging out of a session, no keyboard no screen. Gnome-session still worked though so that XRDP is still accessible.

---

### Post by alh on 2010-05-25
I have the same problem when trying to log out from one user and log in another. Just a blank screen (no login screen) but the system seems to be trying to do something. Need to do hot reboot.
I initially upgraded karmic to lucid but found the system clogged. I did a fresh install re resetup my computer and reinstall all my data. I had no problem with the upgrade with logging out, but the new install is problematic. Everything else working OK.
Any ideas?

---

### Post by haihovu on 2010-06-28
I removed a bunch of packages related to splash screen, which are no longer usable anyway, over two weeks ago and we no longer see this problem (which used to happen two three times a week).

---

### Post by johnburbridge on 2010-09-02
Could you provide details of what packages were removed to get this to work? I'm trying to get xrdp to work for the first time and am also seeing the blank screen (black background) without any decorations or window manager. 

Is there some type of magic that needs to happen so GDM knows about xrdp or vice versa?

Many thanks in advance!

---

### Post by haihovu on 2010-10-24
This thread is not about xrdp but was about blank logon screen at the main console of the PC.
As for xrdp I rarely had to do anything other than to install the standard tightvnc and then xrdp from Synaptic to get it to work, though I am having a devil of a time to get it to work on Maverick (10.10).

---


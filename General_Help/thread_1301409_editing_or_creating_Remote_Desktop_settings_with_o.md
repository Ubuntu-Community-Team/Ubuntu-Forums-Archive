---
title: "editing or creating Remote Desktop settings with only ssh terminal access"
date: 2009-10-26
forum: General Help
---

### Post by derekshaw on 2009-10-26
a.k.a. [http://ubuntuforums.org/showthread.php?t=937665](http://ubuntuforums.org/showthread.php?t=937665)

I have a remote client w/ ubuntu desktop 8.04 LTS.  I need to be able to create/edit the configuration files, using vi in a terminal window (via ssh) to enable remote desktop for a particular user. I have root access to the host.

I DO NOT have access to the GUI either myself or by way of remotely directing a user to click on objects.

I would like to be able to create and subsequently edit the particular user's Remote Desktop settings so I can connect via VNC to the particular user's logged-on session.

I have plenty of working models, if someone can direct me to where the configuration files reside.

---

### Post by dbyjazz on 2009-10-26
Are you talking about your Xorg.conf file?

---

### Post by nothingspecial on 2009-10-26
On your machine, go system > preferences > main menu 

Find the remote desktop entry and click properties

This will tell you the command to launch the remote desktop settings gui.

(I`d do it myself but I`m not running gnome at the moment)

Then ssh the remote machine with the -X flag and issue that command.

---

### Post by derekshaw on 2009-10-27
> **nothingspecial said:**
> On your machine, go system > preferences > main menu 

Find the remote desktop entry and click properties

This will tell you the command to launch the remote desktop settings gui.  [vino-preferences]

(I`d do it myself but I`m not running gnome at the moment)

Then ssh the remote machine with the -X flag and issue that command.

BRILLIANT!  Exactly what I needed.  Thank you very much.

---


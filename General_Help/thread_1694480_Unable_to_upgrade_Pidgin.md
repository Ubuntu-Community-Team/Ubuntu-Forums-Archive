---
title: "Unable to upgrade Pidgin"
date: 2011-02-24
forum: General Help
---

### Post by windofkeltia on 2011-02-24
I'm running pidgin 2.7.3 and wish to run 2.7.9.

I've been to the Pidgin:Ubuntu site, downloaded the PPA file, right-clicked it, opened it with GDebi Package Installer. The installer comes up, but the status is "Same version is already installed." I click the Reinstall Package button, it does its thing and the status is (still or again) "Same version is already installed."

I reboot. Pidgin version is still 2.7.3 and certain of the interface elements are manifestly NOT like the Pidgin 2.7.9 my colleagues are running. As I'm unable to get Pidgin 2.7.3 set up to collaborate (XMPP) with my colleagues, I figure I had better at least use the same version they're using, or the latest (or nearly so--2.7.10 is out for some platforms).

Do I need to wipe Pidgin from my hardware and try the PPA from scratch? Is this done using

[INDENT][FONT="Courier New"]sudo apt-get purge pidgin[/FONT][/INDENT]

I'll lose all my other Pidgin settings, right? (Alas!)

Profuse thanks to anyone who can help.

Russ Bateman

---

### Post by howefield on 2011-02-24
Try going to System > Administration > Update Manger.

Are there updates waiting to be installed for pidgin ? (you might need to reload your package lists)

---

### Post by windofkeltia on 2011-02-24
No, there are no updates. I've tried that several times during this process.

---

### Post by windofkeltia on 2011-02-28
So, what happened to this?

A few days later, there were updates to install and, at that point, the pidgin updates were included among them. Now I have Pidgin 2.7.9.

Go figure.

I consider this thread closed.

---

### Post by howefield on 2011-02-28
That's good to know, thanks for the update.

I guess there was some lag between the new version being released and being available in the Ubuntu repository.

---


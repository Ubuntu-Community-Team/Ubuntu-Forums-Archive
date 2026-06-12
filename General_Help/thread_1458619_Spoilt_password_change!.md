---
title: "Spoilt password change!"
date: 2010-04-20
forum: General Help
---

### Post by longbeard on 2010-04-20
Just had a traumatic experience with Ubuntu 9.10 because password modification for my user account failed without obvious reason. The only special circumstance I can name is that I was downloading new software at the same time.

When I start Ubuntu, I can log on with my user ID and password. Password has been stored somewhere but it doesn't seem enough. After some time I receive the massage

"Could not update ICEauthority file /home/<xyz>/.ICEauthority"

next step I get

"... gconf-sanity-check-2 terminated with Status 256"

Nautilus does not load because it cannot create some files.

---------

Can I mend this situation somehow? Unfortunately root password is unknown.

If I have to install Ubuntu again, can I do it so that I keep programs and personal data in /home or elsewhere?

---

### Post by cjhabs on 2010-04-20
Permissions on /home/<xyz>/.ICEauthority should be:
Owner = you
Group = you
Perms = 600

---

### Post by sh4d0w808 on 2010-04-20
[FONT="Courier New"]$chown user -R /home/user (where user is obviously your user name - run as su - )[/FONT]

Try this one...

---

### Post by longbeard on 2010-04-20
Ok, how can I start a terminal in this circumstance? All I get is a blank screen of the GUI.

---

### Post by cjhabs on 2010-04-20
> **longbeard said:**
> Ok, how can I start a terminal in this circumstance? All I get is a blank screen of the GUI.

Does ctr-alt-f1 work (function key 1)

---

### Post by longbeard on 2010-04-22
Thanks for the assistance!

I've gotten the terminal, but it hasn't helped. My personal folder was inaccessible. My best guess is that the entire thing was encrypted but reengineering it during password change did fail.

This again shows how fragile Linux systems are (just my enduring impression). If anything little goes fail, the entire system has to be reinstalled. Not really for reliability!

---


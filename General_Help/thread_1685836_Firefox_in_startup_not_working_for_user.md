---
title: "Firefox in startup not working for user"
date: 2011-02-11
forum: General Help
---

### Post by cormack12 on 2011-02-11
Hi

I have specified firefox should startup using the following procedure:

System > Preferences > Startup Applications > Add

And used the following details:

**Name**=firefox
**Command**=/usr/lib/firefox-3.6.11/firefox-bin

But it doesn't start up. I tried also adding a shortcut to the following location:

[B]/home/USER/.config/autostart/SHORTCUT-TO-FIREFOX
[/B]
The account I'm trying to get it working on is unprivileged. I'm sure it was working yesterday but can't swear if I had added extra permissions at that stage.

Does this sound like a common problem?

---

### Post by gmargo on 2011-02-11
Try using **/usr/bin/firefox** as the Command.

If you want to try the shortcut method, link to **/usr/share/applications/firefox.desktop**

---

### Post by cormack12 on 2011-02-11
> **gmargo said:**
> Try using **/usr/bin/firefox** as the Command.

If you want to try the shortcut method, link to **/usr/share/applications/firefox.desktop**

Thanks - that first line worked. Out of interest would it just be a permissions thing?

Thanks

---

### Post by gmargo on 2011-02-11
> **cormack12 said:**
> Out of interest would it just be a permissions thing?

Most likely it's because **/usr/bin/firefox** is a link to a shell script that runs a shell script that runs a shell script that finally starts the firefox binary.  You were skipping ahead.

---


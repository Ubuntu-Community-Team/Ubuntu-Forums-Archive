---
title: "software avlable icon missing in 10.04 ??"
date: 2010-10-13
forum: General Help
---

### Post by columbus2012 on 2010-10-13
Hi!  I'm fairly new to Ubuntu, my first version was 8.04 Lts. In that there was a large red icon with an exclamation mark to notify when updates were available. This was unmissable!  This does not seem to exist in 10.04 Lts - or am I missing something. I've looked for an option to enable this but found nothing. I would have thought it should be a default setting.    So do you just have to remember to run update manager every day?  (I've searched the forum but found nothing)

---

### Post by plucky on 2010-10-13
> **columbus2012 said:**
> Hi!  I'm fairly new to Ubuntu, my first version was 8.04 Lts. In that there was a large red icon with an exclamation mark to notify when updates were available. This was unmissable!  This does not seem to exist in 10.04 Lts - or am I missing something. I've looked for an option to enable this but found nothing. I would have thought it should be a default setting.    So do you just have to remember to run update manager every day?  (I've searched the forum but found nothing)



From [Release Notes](https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes)


> Change in notifications of available updates

Ubuntu 9.10 launches update-manager directly to handle package updates, instead of displaying a notification icon in the GNOME panel. Users are notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

(This change was made in Ubuntu 9.04.)



Good Luck

---

### Post by columbus2012 on 2010-10-13
@ Plucky  That does not happen in 10.04. the only way I know if there are updates available is to open update manager manually.  Are you running 10.04 ??

---

### Post by emoguitarist06 on 2010-10-13
The only time I ever see the Red Triangle (Since 9.10 and I'm running 10.10 now) is when it's been several days without an update and when a update is needed the update manager just pops up

---

### Post by columbus2012 on 2010-10-13
I posted this thread when I had seen nothing warning me & on opening update manager it said * Important security updates . .  . .* how long it had been there I do not know but more than a few days for sure.

---

### Post by emoguitarist06 on 2010-10-13
At the top of the update manager it should say the last time it was updated I think??

---

### Post by plucky on 2010-10-13
> @ Plucky That does not happen in 10.04. the only way I know if there are updates available is to open update manager manually. Are you running 10.04 ??

Have you checked the Updates Tag page settings are set correctly in Software Sources? I have "check daily" and "notify" set.


I am running 10.04 on 2 systems.If there are security updates,the Update Manager goes to the bottom panel on that day.For non-security updates,the Update Manager goes to the bottom panel a week after the last update,if there are any updates.

Good Luck

---

### Post by columbus2012 on 2010-10-13
> **emoguitarist06 said:**
> At the top of the update manager it should say the last time it was updated I think??

Yes it does but that does not tell you how long the *Important security updates . . .* had been sitting there unnoticed.
> **plucky said:**
> Have you checked the Updates Tag page settings are set correctly in Software Sources? I have "check daily" and "notify" set.

Thanks, I have made sure that is the case so we wait & see

---

### Post by columbus2012 on 2010-10-31
No! I am still not getting any notifications - I have deliberately left update manager alone to see! (since my last post!)

I ran it manually today and there were some 35 updates available listed as **"Important Security Updates"**

How do I get an obvious notification icon as I had back in 8.xxxx

---

### Post by Andrew_P on 2011-01-21
See [Bug #549217]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/549217").  Since it was first reported on 2010-03-26, apparently nothing has been done to resolve it and nobody has been assigned to fix it, although it now carries a "high" importance.:-(

I've been running an Ubuntu 10.04.1 LTS installation on an AMD Athlon (32-bit) system since late November 2010 and I have *never* seen the notification icon in the Gnome panel.  What's more, I specified an update-check interval of two (2) days, but Configuration Manager shows a value of seven (7) days, so the Update Manager automatically starts once a week, but it never indicates that updates are available, *not even critical security updates*.  It's obvious that this feature is now *broken* on Ubuntu 10.04/10.04.1 LTS.

This wasn't a problem in my previous Ubuntu 8.10 installation.

---


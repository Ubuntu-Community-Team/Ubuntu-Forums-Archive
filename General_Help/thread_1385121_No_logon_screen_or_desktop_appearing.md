---
title: "No logon screen or desktop appearing :?"
date: 2010-01-19
forum: General Help
---

### Post by Fxy on 2010-01-19
Hi

I have the latest version of ubuntu installed on my laptop & just as of today have been unable to boot into the desktop...  I noticed something was wrong when it was getting sluggish & programs such as terminal failed to load...

Once i got fed up i powered down the computer, but now it's failing to load properly...  Every time i power up the laptop it loads like normal until the login screen, at this point all that appears is the mouse cursor :?...  I have tried using recovery mode & then logging in via that way then using startx to load the graphical environment...

Im stuck on this problem so any ideas & help would be much appreciated thnx

---

### Post by Fxy on 2010-01-19
Bump...

---

### Post by Fxy on 2010-01-19
Through press "ctrl-alt-f1" i was able to run "gdm stop" command & got this output...

> ** (gdm-binary:1706): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1:32" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

then it shows directly after...

> [QUOTE]** (gdm-binary:1706): WARNING **: Could not acquire name; bailing out



Any help on this would be much appreciated as i am having to use another laptop to post this message.

---

### Post by Fxy on 2010-01-19
> **Fxy said:**
> Through press "ctrl-alt-f1" i was able to run "gdm stop" command & got this output...



then it shows directly after...

> 



Any help on this would be much appreciated as i am having to use another laptop to post this message.

The first line of code from above "gdm stop" i tried the other version of it...

[QUOTE]sudo /etc/init.d/gdm stop

But all i get is the following...

> Rather than invoking init scripts through /etc/init.d, use the service (8) utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop(8) utility, e.g. stop gdm gdm stop/waiting

If i type service gdm stop all i get is...

> stop: Unknown instance:

Again any replies or help would be appreciated

---

### Post by jessy722 on 2010-01-19
I had the same issue so I formatted... but mines was caused by plugging in a new monitor and the usplash refused to try a different screen res.....

Once I reformatted with new monitor it will splash to either...

---


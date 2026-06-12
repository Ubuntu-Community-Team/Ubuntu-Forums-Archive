---
title: "Ubuntu - Bleachbit"
date: 2012-09-17
forum: General Help
---

### Post by Quarkrad on 2012-09-17
I've configure Bleachbit to 'start bleachbit with computer' via Edit/Preferences.  My expectation, having tick this box, was that bleachbit was going run after the computer start so when I got to Desktop certain 'things' had been cleaned.  What happens is that when the Desktop is there the main bleachbit window is launched and sits there.  Has it already run?  Is it waiting for me to run it?  What has happened?  I don't know whether my expectation is too great but based on many apps with this sort of feature I was expecting bleachbit to run automatically on computer start up.  Part of an automatic cleaning exercise.

---

### Post by Statia on 2012-09-17
No, that is not the way it works. Bleachbit hasn't run yet, it just opens and waits for your input. You could try to figure out which things Bleachbit does by which commands and put those in your rc.local.
For instance:

```
apt-get autoremove && apt-get autoclean && apt-get clean
rm /var/log/*.gz
rm /var/log/*.old
```(Disclaimer: just a quick idea, research these suggestions further before implementing them)

---

### Post by GeForce 9500GT on 2012-09-17
> **Statia said:**
> Bleachbit hasn't run yet, it just opens and waits for your input
 
Correct. However, there's no need to run Bleachbit everytime you start your computer. Linux will not clog like Windows does. Normally what i do is once a month a clean-up with Bleachbit. And basically what Bleachbit delets are remaining cookies (even i set FF up to remove cookies when i close FF),**_old_** log files, _**old**_ backup files, etc. But not much.

---

### Post by Quarkrad on 2012-09-17
That explains - many thanks.

---

### Post by Andrew.Z on 2012-09-17
> **Statia said:**
> No, that is not the way it works. Bleachbit hasn't run yet, it just opens and waits for your input. You could try to figure out which things Bleachbit does by which commands and put those in your rc.local.


BleachBit also has a command line interface for scripting (which can be put in rc.local too).  For example:

```
bleachbit --delete firefox.cookies firefox.cache
```

---


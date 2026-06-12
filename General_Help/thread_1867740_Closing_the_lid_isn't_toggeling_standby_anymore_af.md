---
title: "Closing the lid isn't toggeling standby anymore after update"
date: 2011-10-23
forum: General Help
---

### Post by Bazon on 2011-10-23
Hello, on my netbook closing the lid only leads to lock screen and not to standby in lubuntu. that happened after the update on 11.10, in 11.04 that worked without problem.
Also, in 11.10 Ubuntu (unity) closing the lid leads to standby.

So how can I achieve the same in Lubuntu 11.10?

---

### Post by raja.genupula on 2011-10-23
have you seen in settings of power management ?

---

### Post by Bazon on 2011-10-23
> **raja.genupula said:**
> have you seen in settings of power management ?

How do I get there in Lubuntu? I searched for it, but didn't find it. (Maybe I'm to blind...?)

---

### Post by amjjawad on 2011-10-23
Hi,

From LXTerminal, please run:

```
sudo leafpad /usr/share/applications/xfce4-power-manager-settings.desktop
```

Replace this line:

```
OnlyShowIn=XFCE;
```

with

```
#OnlyShowIn=XFCE;
```

Save, Exit and check your Menu > Preferences

---

### Post by amjjawad on 2011-10-23
If Lubuntu 11.04 (just in case someone else will see this thread)

```
sudo leafpad /usr/share/applications/gnome-power-preferences.desktop
```

Replace:
```
OnlyShowIn=GNOME;XFCE;
```
With:
```
#OnlyShowIn=GNOME;XFCE;
```

---

### Post by Bazon on 2011-10-23
Indeed the settings in xfce4-power-manager-settings was only lock screen and not standby, so the issue is solved.

Thank you! :-)

P.S.:
Not showing the power settings by default is a bug IMHO, I'll look whether it is filed yet....

---

### Post by amjjawad on 2011-10-23
> **Bazon said:**
> Indeed the settings in xfce4-power-manager-settings was only lock screen and not standby, so the issue is solved.

Thank you! :-)


Glad you managed to fix it :)
You welcome!

> P.S.:
Not showing the power settings by default is a bug IMHO, I'll look whether it is filed yet....

It's not a bug, it's a work-around :)
Before you posted, I was thinking to talk to the developer and hope such options will be available by default with 12.04 :)
I'm member in Lubuntu Team and we already started to discuss the roadmap of 12.04 :)

---

### Post by Bazon on 2011-10-23
Ah! Good to know someone cares about... :-)

---

### Post by amjjawad on 2011-10-24
> **Bazon said:**
> Ah! Good to know someone cares about... :-)

I do and many others do as well :)

If you have any other issue, please let me know. Whenever you need anything, start a new thread and PM me the link and I'll jump to help ;)

---


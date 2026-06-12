---
title: "Enable/Disable automatic sleep/standby/hibernate using BASH?"
date: 2010-09-27
forum: General Help
---

### Post by Glaucous on 2010-09-27
My question is simple, is it possible to enable and disable automatic sleep/hibernate/standby using BASH? I need it for a bash script.

Been searching for a while now, can't seem to find it.

---

### Post by Jack Brown on 2010-10-31
im a newbie,

but what if you look at the code for the screens saver options and power management?  (the ones you can access at the system - preferences panel)

assuming you can find the code or the configuration files...


edit:oops, just noticed this is for kubuntu, and am using gnome... maybe there's something similar in kde?

---

### Post by Zorael on 2010-11-02
You can use the dbus interface that PowerDevil provides to change performance profile.

```
$ qdbus org.kde.powerdevil /modules/powerdevil   [i]# tab tab
[...][/i]
org.kde.PowerDevil.brightnessChanged
org.kde.PowerDevil.getSupportedSuspendMethods
org.kde.PowerDevil.lidClosed
org.kde.PowerDevil.profileChanged
org.kde.PowerDevil.refreshStatus
org.kde.PowerDevil.reloadAndStream
org.kde.PowerDevil.setBrightness
org.kde.PowerDevil.setPowerSave
org.kde.PowerDevil.setProfile
org.kde.PowerDevil.stateChanged
org.kde.PowerDevil.streamData
org.kde.PowerDevil.suspend
org.kde.PowerDevil.turnOffScreen
*[...]*
```

setProfile seems to take a string as its argument, so you can set up a profile without automatic sleep/standby/hibernate and then use **setProfile <profilename>**. I just tried it and it seems to work.

```
$ qdbus org.kde.powerdevil /modules/powerdevil setProfile "Powersave"
```

There is also another FDO interface whose method names suggest that they inhibit automatic power management actions.

```
$ qdbus org.kde.powerdevil /org/freedesktop/PowerManagement   [i]# tab tab
[...][/i]
org.freedesktop.PowerManagement.CanHibernate
org.freedesktop.PowerManagement.CanHibernateChanged
org.freedesktop.PowerManagement.CanSuspend
org.freedesktop.PowerManagement.CanSuspendChanged
org.freedesktop.PowerManagement.GetPowerSaveStatus
org.freedesktop.PowerManagement.Hibernate
org.freedesktop.PowerManagement.Inhibit.HasInhibit
org.freedesktop.PowerManagement.Inhibit.HasInhibitChanged
org.freedesktop.PowerManagement.Inhibit.Inhibit
org.freedesktop.PowerManagement.Inhibit.UnInhibit
org.freedesktop.PowerManagement.PowerSaveStatusChanged
org.freedesktop.PowerManagement.Suspend
*[...]*
```
I imagine you can use Inhibit.Inhibit and Inhibit.UnInhibit for this, too. I think you have to go through some hoops to call those methods though; I'm not that big a wiz on qdbus use.

---


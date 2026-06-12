---
title: "Computer Shuts Down When Idle"
date: 2011-02-02
forum: General Help
---

### Post by alexp91k on 2011-02-02
Sometimes, when I leave my Ubuntu's X Server on, I'll come back after several minutes and see that my machine is powered off. Sometimes this happens, sometimes it doesn't, but I don't think it's because of hardware failure rather than my lack of measurement.

It used to power off in terminal mode (CTRL+ALT+F1) but then I added this to ~/.bashrc and it went away:
```
if [ "${USER}" == "root" ]
then
	export TMOUT = 3600
fi
```

Also, I checked my logs and I see this:
```
Feb  2 00:00:09 l1nux AptDaemon: INFO: Quiting due to inactivity
Feb  2 00:00:09 l1nux AptDaemon: INFO: Shutdown was requested

```

Since it's not a CRITICAL message, but an INFO, it seems like its a planned shutdown.

Does anyone know how I can turn this feature off? Thanks a lot!```

```

---

### Post by alexp91k on 2011-02-02
Bump

---

### Post by Hedgehog1 on 2011-02-03
> **alexp91k said:**
> Sometimes, when I leave my Ubuntu's X Server on, I'll come back after several minutes and see that my machine is powered off. Sometimes this happens, sometimes it doesn't, but I don't think it's because of hardware failure rather than my lack of measurement.

It used to power off in terminal mode (CTRL+ALT+F1) but then I added this to ~/.bashrc and it went away:
```
if [ "${USER}" == "root" ]
then
	export TMOUT = 3600
fi
```

Also, I checked my logs and I see this:
```
Feb  2 00:00:09 l1nux AptDaemon: INFO: Quiting due to inactivity
Feb  2 00:00:09 l1nux AptDaemon: INFO: Shutdown was requested

```

Since it's not a CRITICAL message, but an INFO, it seems like its a planned shutdown.

Does anyone know how I can turn this feature off? Thanks a lot!```

```

The first place to start is in power management.

Menu: System >> Preferences >> Power management.
The set the 'put computer to sleep when inactive' to 'never'

This fooled me because it has a battery icon, so I at first assumed it was a laptop only setting - but it applies to desktops too.

Hope this helps...  :KS

---

### Post by alexp91k on 2011-02-03
> **Hedgehog1 said:**
> The first place to start is in power management.

Menu: System >> Preferences >> Power management.
The set the 'put computer to sleep when inactive' to 'never'

This fooled me because it has a battery icon, so I at first assumed it was a laptop only setting - but it applies to desktops too.

Hope this helps...  :KS

Thanks I do have that set to 'never' but it's a good starting place to check. That was my first thought too but it didn't seem to help.

---


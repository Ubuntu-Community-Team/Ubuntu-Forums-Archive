---
title: "Lucid Lynx Panels disappeared"
date: 2010-05-13
forum: General Help
---

### Post by nip37 on 2010-05-13
I did fresh install of Lucid lynx, every thing was working fine, after installation I was prompted for updates and when I restarted the computer after upgrade panels were disappeared, never shown up.

I reinstalled Lucid lynx again, same thing happened after upgrades when I restarted computer there were no panels?

Is there any workaround for this problem?
while upgrading I had one error if that might help

> WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)

---

### Post by nip37 on 2010-05-13
> sudo apt-get install --reinstall gnome-panel 
did not work either.

> 
gconftool-2 &#8211;-shutdown
rm -rf ~/.gconf/apps/panel/
pkill gnome-panel


Above method brings back panels, but after restarting you need to do it again.

---

### Post by tonus on 2010-05-16
Can you paste the output of

```
sudo lspci -v
```

This shows if and what type of Matrox video card you are using, which would make it [bug #572550]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/572550").

---

### Post by lidex on 2010-05-16
Try this variation:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---


---
title: "Ubuntu will not start"
date: 2010-12-11
forum: General Help
---

### Post by Magma828 on 2010-12-11
I'm using Ubuntu 10.04, dual booted with WinXP. I'm on XP now :(

When I select Ubuntu from the OS menu, it starts to load but prints this:
```

Starting AppArmor Properties Skipping profile in /etc/apparmor.d/disable usr.bin.firefox [OK]
Cannot open locale definition file `en_GB.utf8`: No such file or directory

```

It then continues and tries to load cupsd, and just hangs without saying [OK]. I know it's not a problem with cupsd, because earlier it was doing the same with lm-sensors instead, before I removed it (because I thought lm-sensors was causing it).

I can access the terminals (Ctrl+Alt+1/2/3 etc), but Gnome wont load. Typing "sudo restart gdm" etc does nothing.

I tried fixing the "locale" error by typing "sudo dpkg-reconfigure locales", and the output didn't contain any errors, but still nothing works.

**I have a feeling it MAY be related to permissions. Before I last restarted, something was wrong with dpkg. I googled the problem, and it seemed that it was because the user root did not exist. This was true, and it seemed root had been replaced with vroot. So I just added a new user called root, and dpkg worked. Could this be the issue?**

Any suggestions?

---

### Post by Magma828 on 2010-12-11
Added more information to topic.. anyone?:neutral:

---

### Post by jim_deadlock on 2010-12-11
Have you tried booting into recovery mode from the grub menu?

---

### Post by Magma828 on 2010-12-11
It's working!!!!!

Not sure if I've fixed the problem fully.. but anyway, I went into the file /etc/group and removed the user called root I added. I then renamed vroot to root, and added it to the root group.

User bin was not part of any groups, so had to add it to root,bin,daemon.

User daemon was not part of any groups, so had to add it to root,bin,adm.

User disk was not part of any groups, so had to add it to root.

I have no idea how this happened... Have I missed anything, though?

---


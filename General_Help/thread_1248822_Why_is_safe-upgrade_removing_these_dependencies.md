---
title: "Why is safe-upgrade removing these dependencies?"
date: 2009-08-24
forum: General Help
---

### Post by VipX1 on 2009-08-24
[IMG]http://www.black-diamond.ie/Safe-upgrade.png[/IMG]

---

### Post by VipX1 on 2009-08-24
I had a problem where I opened Synaptic and then entered my pass word but the mouse never stopped spinning and everything froze. I went onto the terminal with Ctrl Alt F6 and killed the synaptic pid but the desktop was gone when I exited out of the terminal. I was able to return to the terminal and reboot. I install Komodo-edit-5 yesterday and Aptana the day before. That's the only new changes.

---

### Post by dmizer on 2009-08-24
Almost all of those are development packages (dev), so it doesn't look like it will hurt anything to remove them. Did you remove any packages recently ... medibuntu's ffmpeg perhaps?

---

### Post by VipX1 on 2009-08-24
I did have a problem with Flash 10 recently so I uninstalled swfdec-mozilla and then just put the .so file into the /.mozilla/firefox/plugins directory myself. Flash 10 is fine. I have 9.04 64bit.

---

### Post by VipX1 on 2009-08-24
```
sudo aptitude upgrade
```Incorrect!```
sudo aptitude safe-upgrade
```Correct!!
I did the first one 'upgrade' on my Ubuntu server not so long ago and lost my desktop completely. So I'm I bit nervous with aptitude upgrade since. That's obviously why they have the safe-upgrade. I didn't re-install the Gnome because I'm reading a bit about server security and I'm trying to reduce my services.

---

### Post by P4man on 2009-08-24
I had never heard of safe-upgrade. I checked out the man pages, but Im still confused in what way it differs from upgrade?

> 
 safe-upgrade
           Upgrades installed packages to their most recent version. Installed
           packages will not be removed unless they are unused (see the
           section “Managing Automatically Installed Packages” in the aptitude
           reference manual). Packages which are not currently installed may
           be installed to resolve dependencies unless the --no-new-installs
           command-line option is supplied.

           It is sometimes necessary to remove one package in order to upgrade
           another; this command is not able to upgrade packages in such
           situations. Use the full-upgrade command to upgrade as many
           packages as possible.

Strangely, I dont see a man page entry for "upgrade" to compare with (only full-upgrade) and  when i type aptitude -h there is no upgrade either. 

Is "upgrade" = "full-upgrade" or "safe-upgrade" or something undocumented lol ?

---

### Post by CatKiller on 2009-08-24
> **P4man said:**
> I had never heard of safe-upgrade. I checked out the man pages, but Im still confused in what way it differs from upgrade?

It doesn't, really. "upgrade" and "dist-upgrade" are apt-get options rather than aptitude options, since aptitude uses "safe-upgrade" and "full-upgrade," respectively. dist-upgrade/full-upgrade removes packages to satisfy dependencies, upgrade/safe-upgrade doesn't. aptitude will accept apt-get options currently, but it won't necessarily for ever. Hence the warning.

---

### Post by CatKiller on 2009-08-24
To the OP: I don't think those packages are being removed by the upgrade process. I think they are being removed because they were installed to meet a dependency that is no longer required ("automatically installed"). aptitude will habitually do this. apt-get requires you to run *apt-get autoclean*.

---

### Post by P4man on 2009-08-25
> **CatKiller said:**
> It doesn't, really. "upgrade" and "dist-upgrade" are apt-get options rather than aptitude options, since aptitude uses "safe-upgrade" and "full-upgrade," respectively. dist-upgrade/full-upgrade removes packages to satisfy dependencies, upgrade/safe-upgrade doesn't. aptitude will accept apt-get options currently, but it won't necessarily for ever. Hence the warning.

thanks, that makes sense.

---


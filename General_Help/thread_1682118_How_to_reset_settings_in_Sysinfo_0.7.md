---
title: "How to reset settings in Sysinfo 0.7"
date: 2011-02-05
forum: General Help
---

### Post by Nico-dk on 2011-02-05
**What happended:**
I installed Sysinfo 0.7, unfortunately I set 'Section to start in' to System. As some of you probably already know, and I didn't, is that there's a bug in Sysinfo, that crashes the app, when System is selected (details here: [https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727](https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727)).

What this means, is that I can't run Sysinfo anymore, because it crashes on startup. Starting it as superuser works, but since I use Gnome Do, I would like to launch it w/o having to go through the terminal.

**What I've tried:**
Did a complete removal from Synaptics, thinking this would delete settings as well. It didn't.

Ran locate sysinfo from terminal, looking for a settings file. no luck

**My question (finally):**
How to I delete og change the current settings in Sysinfo for my user?

As always, thanks for your time

---

### Post by cgroza on 2011-02-05
> **Nico-dk said:**
> **What happended:**
I installed Sysinfo 0.7, unfortunately I set 'Section to start in' to System. As some of you probably already know, and I didn't, is that there's a bug in Sysinfo, that crashes the app, when System is selected (details here: [https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727](https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727)).

What this means, is that I can't run Sysinfo anymore, because it crashes on startup. Starting it as superuser works, but since I use Gnome Do, I would like to launch it w/o having to go through the terminal.

**What I've tried:**
Did a complete removal from Synaptics, thinking this would delete settings as well. It didn't.

Ran locate sysinfo from terminal, looking for a settings file. no luck

**My question (finally):**
How to I delete og change the current settings in Sysinfo for my user?

As always, thanks for your time

You need to remove the configuration file and this should force the program to generate a new default one. You can use 
```
sudo apt-get purge <program name>
```
and then reinstall it.

---

### Post by Nico-dk on 2011-02-05
Thanks, unfortunately that didn't solve my problem.
After a reinstall, sysinfo still crashes on startup. Starting from terminal reproduces the bug, I linked to above

```
Exception in Gtk# callback delegate

[...]

System.NullReferenceException: Object reference not set to an instance of an object

```

On a sidenote:
Isn't ...```
apt-get purge
``` ...the equivilant of Synpatics 'Mark for complete removal'?

---

### Post by cgroza on 2011-02-06
Well, that should delete the configuration file. Are you sure that the bug is not somewhere else? Try installing the latest version from a PPA or something.

---

### Post by Nico-dk on 2011-02-06
> **cgroza said:**
> Well, that should delete the configuration file. Are you sure that the bug is not somewhere else?
No, but running from terminal, I get the same error messages, as the reported in the sysinfo bug (see my first post)

Purged it again, and config files should be removed (as you said):

```
Removing sysinfo ...
Purging configuration files for sysinfo ...
```

Then to double check I ran

```
sudo updatedb
locate sysinfo
```

Which returned

```
/etc/apparmor.d/apache2.d/phpsysinfo
[B]/home/[myuser]/.gconf/apps/sysinfo
/home/[myuser]/.gconf/apps/sysinfo/%gconf.xml[/B]
/usr/bin/ipod-read-sysinfo-extended
/usr/include/sys/sysinfo.h
/usr/share/app-install/desktop/sysinfo.desktop
/usr/share/man/man2/sysinfo.2.gz
/usr/src/linux-headers-2.6.35-25/arch/alpha/include/asm/sysinfo.h
/usr/src/linux-headers-2.6.35-25/arch/mips/include/asm/octeon/cvmx-sysinfo.h
/usr/src/linux-headers-2.6.35-25/arch/s390/include/asm/sysinfo.h
```

I highlighted the entries that caught my eye. Although %gconf.xml doesn't seem to hold any sysinfo settings.
I could try to delete that entire dir, but I'm so new to the linux filesystem, that I'm not sure if that's adviseable.

Thanks for taking the time help me out :)

---

### Post by Nico-dk on 2011-02-06
Sorry for the double post.

The %gconf.xml was the key.
Opened it and found

```
<entry name="section_start" mtime="1297010041" type="int" value="1"/>
```

Changed that one to a 3 on a suspicion the entry 1 was for System. Worked like a charm, and I can now open sysinfo once again.

I'm running my /Home as a Logical partition on sda2. Thought purge would still remove all config file regardless.

Thanks for the help

---


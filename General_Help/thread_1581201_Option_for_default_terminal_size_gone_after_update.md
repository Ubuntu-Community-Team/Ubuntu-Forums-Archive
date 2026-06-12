---
title: "Option for default terminal size gone after update"
date: 2010-09-24
forum: General Help
---

### Post by edmazur on 2010-09-24
After updating/upgrading my packages this morning, the terminal profile preferences screen (Edit > Profile Preferences) no longer had the option at the bottom for setting the default terminal size. This is a problem because the default size went from the 132x43 I had set it to down to 80x24.

I'm running Ubuntu 10.04 LTS on three machines and had this problem on all of them. After noticing the problem on the first machine, I checked the option screens of the other machines before upgrading. The default size option was there before the upgrades, but after upgrading, it was gone.

Here is the aptitude log from the upgrade:

[UPGRADE] ant 1.7.1-4ubuntu1 -> 1.7.1-4ubuntu1.1
[UPGRADE] ant-gcj 1.7.1-4ubuntu1 -> 1.7.1-4ubuntu1.1
[UPGRADE] ant-optional 1.7.1-4ubuntu1 -> 1.7.1-4ubuntu1.1
[UPGRADE] ant-optional-gcj 1.7.1-4ubuntu1 -> 1.7.1-4ubuntu1.1
[UPGRADE] gnome-terminal 2.29.6-0ubuntu5 -> 2.30.2-0ubuntu1
[UPGRADE] gnome-terminal-data 2.29.6-0ubuntu5 -> 2.30.2-0ubuntu1
[UPGRADE] google-chrome-stable 6.0.472.62-r59676 -> 6.0.472.63-r59945
[UPGRADE] libphonon4 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-assistant 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-dbus 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-designer 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-help 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-network 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-opengl 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-qt3support 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-script 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-scripttools 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-sql 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-sql-mysql 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-svg 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-test 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-webkit 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-xml 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqt4-xmlpatterns 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqtcore4 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] libqtgui4 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1
[UPGRADE] phonon 4:4.6.2-0ubuntu5 -> 4:4.6.2-0ubuntu5.1

It's almost surely gnome-terminal or gnome-terminal-data, but I included the full list just in case.

What are my options for fixing this? Should I try rolling back the upgrade? Should I not bother with that and just try setting the default terminal size through other means?

---

### Post by philinux on 2010-09-24
Same here. Only just noticed.

Back to the old ways then. Seem regressive to me.

```
gksudo gedit /usr/share/vte/termcap/xterm

Line 10
```

Logout then in for it to take effect.

---

### Post by drs305 on 2010-09-24
Open gconf-editor, a configuration tool, and see if the options are still listed there:

```
gconf-editor /apps/gnome-terminal/profiles/Default/default_size_columns
```

The two settings (columsn/rows) are adjacent to each other. Try manually setting the values. Then go down a bit in the same section and enable "use_custom_default_size".

---

### Post by edmazur on 2010-09-24
> **philinux said:**
> Same here. Only just noticed.

Back to the old ways then. Seem regressive to me.

```
gksudo gedit /usr/share/vte/termcap/xterm

Line 10
```

Logout then in for it to take effect.

Thanks, this worked.

> **drs305 said:**
> Open gconf-editor, a configuration tool, and see if the options are still listed there:

```
gconf-editor /apps/gnome-terminal/profiles/Default/default_size_columns
```

The two settings (columsn/rows) are adjacent to each other. Try manually setting the values. Then go down a bit in the same section and enable "use_custom_default_size".

I checked these configuration options (before applying the above fix) and they were actually already set to my old size (132x43). I did not see the use_custom_default_size option.

---

### Post by drs305 on 2010-09-24
> **edmazur said:**
> I checked these configuration options (before applying the above fix) and they were actually already set to my old size (132x43). I did not see the use_custom_default_size option.

If you are interested in pursuing this, here is the setting that exists for me:

> gconf-editor /apps/gnome-terminal/profiles/Default/use_custom_default_size

If it doesn't exist, you might be able to create it. In the same section, right click, new key. Here are the values:

Name: /apps/gnome-terminal/profiles/Default/use_custom_default_size
Type: Boolean
Value: True

---

### Post by edmazur on 2010-09-24
> **drs305 said:**
> If you are interested in pursuing this, here is the setting that exists for me:



If it doesn't exist, you might be able to create it. In the same section, right click, new key. Here are the values:

Name: /apps/gnome-terminal/profiles/Default/use_custom_default_size
Type: Boolean
Value: True

I was curious, so I tried this on one of the other machines before applying the other fix. I added the use_custom_default_size property, set it to true, logged out/in, but it didn't have any effect.

---

### Post by drs305 on 2010-09-24
> **edmazur said:**
> I was curious, so I tried this on one of the other machines before applying the other fix. I added the use_custom_default_size property, set it to true, logged out/in, but it didn't have any effect.

Thanks for the update and sorry it didn't work. I'm using Lucid and Maverick, updated, and they still exist and work on my systems.

---

### Post by edmazur on 2010-09-24
> **drs305 said:**
> Thanks for the update and sorry it didn't work. I'm using Lucid and Maverick, updated, and they still exist and work on my systems.

No worries, thanks for the suggestion.

---

### Post by luigi_mb on 2010-09-24
Why not add the following switch to the launcher:

--geometry=132x43

i.e.

gome-terminal --geometry=132x43


/luigi

---

### Post by philinux on 2010-09-25
Look like the option is available in Maverick for now. I wish the devs would make their minds up.

---

### Post by FrankyG on 2010-09-27
> **philinux said:**
> Same here. Only just noticed.

Back to the old ways then. Seem regressive to me.

```
gksudo gedit /usr/share/vte/termcap/xterm

Line 10
```Logout then in for it to take effect.

You don't need to log out/log in for the changes to take effect. Simply close _every_ terminal and open a new one.

---

### Post by Dreamboat on 2011-01-21
> **philinux said:**
> 

```
gksudo gedit /usr/share/vte/termcap/xterm

Line 10
```Logout then in for it to take effect.

Thanks phil .. one piece of info! And to edmazur too, for raising this.

---


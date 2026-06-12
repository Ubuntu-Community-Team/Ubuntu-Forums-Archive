---
title: "can not install adobe flash player on my 10.04"
date: 2010-07-04
forum: General Help
---

### Post by nightfall77 on 2010-07-04
it shows a warning message saids adobe flash player is virtual,
how do i solve this problem?

---

### Post by khelben1979 on 2010-07-04
Have you tried to download the Adobe flash player from the Adobe website?

---

### Post by philinux on 2010-07-04
> **nightfall77 said:**
> it shows a warning message saids adobe flash player is virtual,
how do i solve this problem?

Open a terminal Apps>access

```
sudo apt-get install flashplugin-nonfree
```

This installs the plugin from adobe.

---

### Post by nightfall77 on 2010-07-04
i type that command in terminal, and it ask me for [sudo] passwprd:
but i can not type password,it just stuck there.what should i do?

---

### Post by lovinglinux on 2010-07-04
> **nightfall77 said:**
> i type that command in terminal, and it ask me for [sudo] passwprd:
but i can not type password,it just stuck there.what should i do?

The password input in the terminal does not show any asterisks. Just type the password and hit Enter.

---

### Post by DonThompson on 2010-07-08
Doesn't work for me...

don@lanthia4:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for don: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libkworkspace4 libplasma-geolocation-interface4 libplasmaclock4
  libweather-ion4 kdebase-workspace-bin libprocessui4 libprocesscore4
  libsolidcontrol4 libsolidcontrolifaces4 akonadi-server libksgrd4
  libtaskmanager4 libqimageblitz4 kdebase-workspace-data
  libplasmagenericshell4 kdebase-workspace-kgreet-plugins libkephal4
  plasma-dataengines-workspace ksysguardd libkscreensaver5 libkfontinst4
  libplasma-applet-system-monitor4 kdepim-runtime plasma-widgets-workspace
  libgda3-sqlite
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
don@lanthia4:~$

---

### Post by lovinglinux on 2010-07-09
> **DonThompson said:**
> Doesn't work for me...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
**flashplugin-nonfree is already the newest version.**
...

It is already installed. If flash still doesn't work for you, try [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/).

---


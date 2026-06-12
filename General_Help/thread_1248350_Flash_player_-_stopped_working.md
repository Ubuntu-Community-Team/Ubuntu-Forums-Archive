---
title: "Flash player - stopped working?"
date: 2009-08-24
forum: General Help
---

### Post by mac666 on 2009-08-24
Hey!
go to Program > Accesories > Terminal and type:

```
[FONT=verdana, arial, helvetica][SIZE=2]sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree[/SIZE][/FONT]
```

And restart Firefox...

---

### Post by djurny on 2009-08-24
> **Alex Last said:**
> Got this:

```
alex@Alex-Ubuntu:~$ sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin

```

just remove the 'adobe-flashplugin' from the commandline..

maybe type the following:

```

for package in adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla; do
  sudo apt-get purge $package
done
sudo apt-get install flashplugin-nonfree

```

what he meant was to remove and purge those packages, but apt-get stops at the first 'error' it encounters.. in your case, you didn't have 'adobe-flashplugin' installed, so trying removing it caused an error

---


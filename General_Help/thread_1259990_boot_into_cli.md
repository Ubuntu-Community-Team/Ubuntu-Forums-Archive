---
title: "boot into cli"
date: 2009-09-07
forum: General Help
---

### Post by e24ohm on 2009-09-07
Folks:
I understand that F1 gets you into the shell; however, is there a way to boot Ubuntu right into a cli/shell/command line mode without starting Gnome?

//why I want to do this//
Due to performance issues with my old PII Celeron hardware on my laptop, I have cli based apps that I need - so this will not be an issue...I only use the laptop for note taking and Linux studies at this point. The real issue is the processor idles around 60%, and when I go to load a website, it max. at 100% for sometime. The screen even dims out for a while, then comes back into focus, so I have been using the cli app Elinks for my forums.

---

### Post by Linteg on 2009-09-07
If to want to start to the CLI you'll need to remove GDM from the rc/upstart scripts:
```
sudo update-rc.d -f gdm remove
```
If you want to start GDM temporarily it's always possible to do so by executing:
```
sudo /etc/init.d/gdm start
```
(although just running startx will start gnome).
If you ever want to undo the changes to the rc scripts:
```
sudo update-rc.d gdm defaults 30 01
```

---

### Post by hal10000 on 2009-09-07
> Due to performance issues with my old PII Celeron hardware on my laptop, I have cli based apps that I need - so this will not be an issue...I only use the laptop for note taking and Linux studies at this point.

What about using another distro such as gentoo or dsl (damn small linux), which is made specially for smaller/older systems?
I have dsl running on a 10 year old ibm laptop and it runs like hell, believi it or not, it's faster than ubuntu on my 1 year old Amilo Xi2528 with 4GB RAM/Core2Duo.

---

### Post by RedSquirrel on 2009-09-07
> **Linteg said:**
> If to want to start to the CLI you'll need to remove GDM from the rc/upstart scripts:
```
sudo update-rc.d -f gdm remove
```If you want to start GDM temporarily it's always possible to do so by executing:
```
sudo /etc/init.d/gdm start
```(although just running startx will start gnome).
If you ever want to undo the changes to the rc scripts:
```
sudo update-rc.d gdm defaults 30 01
```

Another way is to rename the symlink, as described in /etc/rc2.d/README.

For example:

```
sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/K87gdm
```To have it start up as part of the boot sequence once again:

```
sudo mv /etc/rc2.d/K87gdm /etc/rc2.d/S13gdm
```

> **hal10000 said:**
> What about using another distro such as gentoo or dsl (damn small linux), which is made specially for smaller/older systems?
I have dsl running on a 10 year old ibm laptop and it runs like hell, believi it or not, it's faster than ubuntu on my 1 year old Amilo Xi2528 with 4GB RAM/Core2Duo.

Since Gentoo is source-based, it can be a pain to keep up to date on old hardware.

---

### Post by lswb on 2009-09-07
Take a look here for making it a choice at boot:
[http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml](http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml)
and
[http://lwasserm.freeshell.org/ubuntu/editrl.shtml](http://lwasserm.freeshell.org/ubuntu/editrl.shtml)

The link was written for 8.04 but the instructions apply to 8.10 and 9.04 as well

---

### Post by e24ohm on 2009-09-08
> **hal10000 said:**
> What about using another distro such as gentoo or dsl (damn small linux), which is made specially for smaller/older systems?
I have dsl running on a 10 year old ibm laptop and it runs like hell, believi it or not, it's faster than ubuntu on my 1 year old Amilo Xi2528 with 4GB RAM/Core2Duo.I thought DSL loaded into RAM? I ony have 1000mb, and the processor gets hosed as it is right now.

thanks for the suggestion...I'll look into DSL.

---

### Post by e24ohm on 2009-09-08
> **Linteg said:**
> If to want to start to the CLI you'll need to remove GDM from the rc/upstart scripts:
```
sudo update-rc.d -f gdm remove
```
If you want to start GDM temporarily it's always possible to do so by executing:
```
sudo /etc/init.d/gdm start
```
(although just running startx will start gnome).
If you ever want to undo the changes to the rc scripts:
```
sudo update-rc.d gdm defaults 30 01
```thanks I'll try this out today.

---

### Post by hal10000 on 2009-09-08
> I thought DSL loaded into RAM?
It can be loaded into RAM, but it's not mandatory. With 1000MB you'll have more than enough space to do this, which would it make even faster.

---

### Post by wojox on 2009-09-08
You could also install Ubuntu Server instead of Desktop.

---


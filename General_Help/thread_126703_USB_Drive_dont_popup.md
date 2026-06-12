---
title: "USB Drive dont popup"
date: 2006-02-07
forum: General Help
---

### Post by mrtin on 2006-02-07
Hi,
I have an External USB Harddrive. My problem is that it doesnt popup on my desktop or in Nautilus.
Aren't usb devices supposed to popup when i connect them to my computer? Or do i have to mount them manually?

I can see the hardrdive in, System -> Administration -> Disks, and i can mount it manually. The partition properties are
Access Path: None
Status: Inaccessible


/martin

---

### Post by schdefan on 2006-02-07
you have to make sure that gnome-volume-manager is running. 
```
$ps -A|grep gnome-volume-*
```
Also check the configuration of gvm with gconf-editor.
Under /desktop/gnome/volume_manager make sure that
automount_media and autobrowse is active.

schdefan

---

### Post by mrtin on 2006-02-09
[QUOTE=schdefan]you have to make sure that gnome-volume-manager is running. 
```
$ps -A|grep gnome-volume-*
```
Also check the configuration of gvm with gconf-editor.
Under /desktop/gnome/volume_manager make sure that
automount_media and autobrowse is active.

schdefan[/QUOTE]


Hi,
thanks for your help im not so familiar with linux, but i think the the things you said was on already. Do you have any other suggestions?

[img]http://hem.bredband.net/b222874/dump2.png[/img]

[img]http://hem.bredband.net/b222874/dump1.png[/img]

---

### Post by soonindallas on 2006-02-09
I have had the same issue with a usb stick.  The stick I have is mounted on first insertion about 50% or the time.  If it is not mounted right away I take it out and reinsert it.  It has always mounted on the second try.

This seems to occur when I use the same stick on WinXP with about the same frequency.

Maybe my stick is bad.

---

### Post by mgor on 2006-02-09
also make sure your user belongs to the "plugdev" group. as your user, type
```
$ groups
usergroup adm cdrom audio video **plugdev** lpadmin scanner admin
$ sudo usermod -G cdrom,audio,video,plugdev,lpadmin,scanner,admin,adm username
```

or if you prefer a GUI, run: user-admin (System -> Administration -> Users and Groups), check the properties for your user and the last tab (not sure the en_US translation). the "something something external volumes somthing" should be checked :)

you'll have to logout and login again for the changes to take effect.

---

### Post by mrtin on 2006-02-09
[QUOTE=mgor]also make sure your user belongs to the "plugdev" group. as your user, type
```
$ groups
usergroup adm cdrom audio video **plugdev** lpadmin scanner admin
$ sudo usermod -G cdrom,audio,video,plugdev,lpadmin,scanner,admin,adm username
```

or if you prefer a GUI, run: user-admin (System -> Administration -> Users and Groups), check the properties for your user and the last tab (not sure the en_US translation). the "something something external volumes somthing" should be checked :)

you'll have to logout and login again for the changes to take effect.[/QUOTE]

Yes I think my user belongs to plugdev already.
Maybe its something missing in my ubuntu installation. I tried to upgrade Firefox by follow a guide, which i shouldn't have done.  Instead of getting the firefox. The old firefox dissapperad and the menu options "System\Help" and "Program\Add applications" dissapeared too. :cry:  But i managed to get these things back with the Synaptic Package Manager \\:D/ 
Maybe i just should have stuck to M$.

[img]http://hem.bredband.net/b222874/dump3.png[/img]

[img]http://hem.bredband.net/b222874/dump5.png[/img]

---

### Post by schdefan on 2006-02-09
You can try to reinstall the gnome-volume-manager.
```
$apt-get --reinstall --purge gnone-volume-manager
```
schdefan

---


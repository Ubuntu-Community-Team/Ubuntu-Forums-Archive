---
title: "Wine 10.04 Trouble.."
date: 2010-06-20
forum: General Help
---

### Post by JugglinPhil on 2010-06-20
With the new Security Policy in 10.04, you can't run a .exe in wine unless you mark it as trusted ([https://wiki.ubuntu.com/Security/ExecutableBit](https://wiki.ubuntu.com/Security/ExecutableBit)). This however is only possible if you have write access to the file you are trying to access. 
Now when I use wine for windows-games, I obviously do not have write access to the cd-rom, and thus can not execute them. This makes wine pretty much useless, so I don't really get the point of this policy.
Is there any way around this without having to copy the disc to the hdd?

---

### Post by davidmohammed on 2010-06-20
yes - install wine from the [ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa") - dont use the default wine 1.2 available in synaptic.  Last time I looked, they disabled this "feature" introduced by canonical.

---

### Post by JugglinPhil on 2010-06-21
As I am using a program called "PlayonLinux" it automatically installed wine, can I just reinstall wine without it getting all messed up?

---

### Post by OtakuWrath on 2010-06-21
Go into the CD and highlight everything and copy it to your desktop or something.. you then have write access to the file run the install.exe.. i did this for Starcraft like an hour ago.. just deleted the useless files as once its installed it runs off the CD like normal.

Edit: Copying to the HDD can't be that bad. You don't need to keep the files there after installing.. it doesn't take up space for more then maybe 30 minutes while you install...

---

### Post by JugglinPhil on 2010-06-22
Yeah but it's still annoying.

---

### Post by mc4man on 2010-06-22
2 ways among several
revert the Exec= in wine.desktop to orig.
```
gksu gedit /usr/share/applications/wine.desktop
```
change the Exec= to this
```
Exec=wine start /unix %f
```
or if you don't have an fstab entry for the drive, if you create one and a mountpoint then the security bit shouldn't be applied to .exe's on a cdrom disk

Typical fstab for /dev/sr0
```
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

plus create the mountpoint
```
sudo mkdir /media/cdrom0
```

(have never gotten any answers as to whether there is any issue having fstab entry(s) for optical drive(s) on lucid - don't see any here as of yet

---

### Post by JugglinPhil on 2010-06-24
Thanks, I tried your first suggestion and it worked well.

---

### Post by brigadoon on 2011-02-27
> **mc4man said:**
> 2 ways among several
revert the Exec= in wine.desktop to orig.
```
gksu gedit /usr/share/applications/wine.desktop
```
change the Exec= to this
```
Exec=wine start /unix %f
```
or if you don't have an fstab entry for the drive, if you create one and a mountpoint then the security bit shouldn't be applied to .exe's on a cdrom disk

Typical fstab for /dev/sr0
```
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

plus create the mountpoint
```
sudo mkdir /media/cdrom0
```

(have never gotten any answers as to whether there is any issue having fstab entry(s) for optical drive(s) on lucid - don't see any here as of yet
Been trying to install Neverwinter Nights 2 without having to copy the CD to my system just to install. Thanks you very much for this solution. The wine edit worked for me. Now I have to find a way to get NWN2 to run in Wine with 3D acceleration. Oh well, what's life without a challenge?

---


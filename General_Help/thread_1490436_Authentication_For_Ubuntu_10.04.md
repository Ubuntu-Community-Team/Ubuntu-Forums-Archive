---
title: "Authentication For Ubuntu 10.04"
date: 2010-05-22
forum: General Help
---

### Post by gurulenin on 2010-05-22
Hi,

I am using ubuntu 10.04. I want to set up authentication to mount hard disk and other removable devices. Anybody can help me.:confused:

---

### Post by sanderd17 on 2010-05-22
Did you try System -> administration -> users and groups and than go in the advanced settings to "userrights".

Or do you want more specifical things?

---

### Post by bodhi.zazen on 2010-05-22
Moved to general help.

---

### Post by DawieS on 2010-05-22
The default behavior in Ubuntu 10.04 is to allow mounting of [COLOR=Red]**all**[/COLOR] drives (internal & external) without password authentication. If you want to change this behavior, open a terminal and enter:
```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```Change the first occurrence of 'ResultActive=[COLOR=Red]**yes**[/COLOR]' to 'ResultActive=[COLOR=Red]**auth_admin_keep**[/COLOR]' and save.

The default behavior should now require a password when mounting [COLOR=Red]**all**[/COLOR] drives (internal & external USB drives).  If you want to change this behavior, and require a password for [COLOR=Red]**either**[/COLOR] internal drives [COLOR=Red]**or**[/COLOR] external USB drives, open a terminal and enter:
```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```Delete these first 4 lines:
```
[Mounting, checking, etc. of internal drives]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
ResultActive=yes
```Save and exit the editor, then enter in a terminal:
```
sudo gedit /usr/share/polkit-1/actions/org.freedesktop.udisks.policy
```To allow mounting without password for External USB disks and flash-drives:
Under the first heading: <action id="org.freedesktop.udisks.filesystem-mount">
Change <allow_active>[COLOR=Red]**auth_admin_keep**[/COLOR]</allow_active> to <allow_active>[COLOR=Red]**yes**[/COLOR]</allow_active>

To allow mounting without password for Internal (and External eSata) drives:
Under the second heading: <action id="org.freedesktop.udisks.filesystem-mount-system-internal">
Change <allow_active>[COLOR=Red]**auth_admin_keep**[/COLOR]</allow_active> to <allow_active>[COLOR=Red]**yes**[/COLOR]</allow_active>

Save and exit the editor.

Please note that these changes may be overwritten with an update, and may need to be redone thereafter.:smile:

---

### Post by gurulenin on 2010-05-22
Thanks !!! its working fine.    ):P

---

### Post by jvdurme on 2010-12-13
You're a livesaver [DawieS]("http://www.uluga.ubuntuforums.org/member.php?u=869922").
Worked out perfect on 10.10. :D

---


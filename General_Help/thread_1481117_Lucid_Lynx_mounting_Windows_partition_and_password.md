---
title: "Lucid Lynx: mounting Windows partition and password"
date: 2010-05-12
forum: General Help
---

### Post by t36 on 2010-05-12
Hi,

I was just wondering, is there a reason why when mounting a Windows partition I am no longer prompted for a password?
I kinda liked this behaviour because it helped me lower the risk of doing stupid stuff to the windows partition.

Thanks in advance

---

### Post by QLee on 2010-05-12
[QUOTE=t36]
I was just wondering, is there a reason why when mounting a Windows partition I am no longer prompted for a password?
I kinda liked this behaviour because it helped me lower the risk of doing stupid stuff to the windows partition.[/QUOTE]

Well, since none of us was looking over your shoulder and you didn't give much information, it isn't going to be easy to answer because we don't know the conditions under which it happened.

Given no further information, I would guess that you had already used a command that elevated your permissions and that you tried before the elevated permissions "time out" expired. But that's just a guess.

Otherwise, please explain a bit more about what you are asking.

---

### Post by DawieS on 2010-05-12
Open a terminal and enter:

```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```Change the first occurrence of '**ResultActive=yes**' to '**ResultActive=auth_admin_keep**' and save. The behaviour should now revert to the default of requiring a password when mounting internal disks.

:smile::razz::smile:

---

### Post by t36 on 2010-05-12
I was indeed referring to mounting internal disks. In 9.10 whenever I wanted to browse my windows partition via places -> WinXP partition I would get a prompt asking for authentication. Now in 10.04, that doesn't happen any more (I'm pretty sure I didn't change any thing). And that just feels a bit weird and unsafe. 
I will try DawieS's solution once I get home.

Thanks.

---

### Post by t36 on 2010-05-12
Thanks! DawieS's answer did the trick :).

---

### Post by chanakyakv on 2010-05-19
Thanks! DawieS's answer worked for me too.

But, now even mounting a External pen drive / flash drive / usb drive requires authentication. !!

Can I get help in getting Authentication on mounting drives as exactly in KarMic.
i.e. Authentication for mounting Windows partitions but no authentication for mounting external usb drives.

---

### Post by DawieS on 2010-05-19
> **chanakyakv said:**
> Thanks! DawieS's answer worked for me too.

But, now even mounting a External pen drive / flash drive / usb drive requires authentication. !!

Can I get help in getting Authentication on mounting drives as exactly in KarMic.
i.e. Authentication for mounting Windows partitions but no authentication for mounting external usb drives.
I have done some experimenting with authorization settings. It seems as if the settings in the file mentioned in post #3 overrides settings of the **/usr/share/polkit-1/actions/org.freedesktop.udisks.policy** file (probably for compatibility reasons for other lighter versions of Ubuntu).

To achieve what you want, open a terminal and enter:
```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```Cut and paste the first 4 lines into another text file, for your own backup purposes (should you want to revert later):
```
[Mounting, checking, etc. of internal drives]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
ResultActive=auth_admin_keep
```After deleting these first 4 lines, save and exit the editor. Then enter in a terminal:
```
sudo gedit /usr/share/polkit-1/actions/org.freedesktop.udisks.policy
```**For USB disks and flash-drives:**
Under the first heading: <action id="org.freedesktop.udisks.filesystem-mount">
Change <allow_active>[COLOR=Red]**auth_admin_keep**[/COLOR]</allow_active> to <allow_active>[COLOR=Red]**yes**[/COLOR]</allow_active>
**For Internal (and External eSata) disks:**
Under the second heading: <action id="org.freedesktop.udisks.filesystem-mount-system-internal">
Leave the same <allow_active>[COLOR=Red]**auth_admin_keep**[/COLOR]</allow_active> (unless you want to change the behavior)

Save and exit the editor. The behavior should now default to auto-mounting for USB drives, but require a password for mounting internal (and external eSata) disks.

Please note that these changes may be overwritten with an update, and may need to be redone thereafter.:smile:

---

### Post by chanakyakv on 2010-05-20
Thank you Very Much !!  :)  :-)

That Worked !!

---


---
title: "Mount ntfs file systems without permission"
date: 2010-02-01
forum: General Help
---

### Post by sharaq on 2010-02-01
First open a terminal 

> Application >> Accessories >> Terminal

then type 

[B]```
$ sudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

```[/B]

then look for this. 
[COLOR="Blue"]<action id=[/COLOR][COLOR="Magenta"]"org.freedesktop.devicekit.disks.filesystem-mount-system-internal"[/COLOR][COLOR="blue"]>[/COLOR] 
under that block there will be something like this
 > <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      [COLOR="Red"]<allow_active>auth_admin_keep</allow_active>[/COLOR]
    </defaults>


change the highlighted one to
[COLOR="red"]> <allow_active>yes</allow_active>[/COLOR]

And save the file and exit.
Now you can mount the ntfs partitions without permission.

---


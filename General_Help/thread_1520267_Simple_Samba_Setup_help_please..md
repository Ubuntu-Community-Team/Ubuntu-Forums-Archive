---
title: "Simple Samba Setup help please."
date: 2010-06-29
forum: General Help
---

### Post by User0123 on 2010-06-29
All I wish to do is create a samba share which anyone on my LAN can access without being prompted for a username and password.

Whatever I try seems to go wrong.

Surely this would only require a few lines in smb.conf but following the tutorials posted on here seem to give me a huge mess of config which is irrelevant to what I am trying to achieve.

I wish to allow read & write access to /media/EXTERNAL/Shared to all users on my LAN, without them needing to log in (guest account?). 

Please would someone be kind enough to help.

---

### Post by User0123 on 2010-06-29
Anyone? ^_^

---

### Post by mikewhatever on 2010-06-29
Try the following few lines:
```
[Shared]
        path = /media/EXTERNAL/Shared
        browseable = yes
        writeable = yes
        guest ok = yes

```

---

### Post by Morbius1 on 2010-06-29
> Whatever I try seems to go wrong.**First**, I assume you first tried Nautilus-share ( Right click > Sharing Options ) . What was presented above is Classic-share. It's best not to use both samba methods on the same target at the same time. If you post the output of the following command it will tell us if you are using Nautiuls-share:
```
net usershare info
```**Second,** is the external drive by any chance formatted in NTFS or FAT32.
If it is then neither method will work unless you add one line to smb.conf:
```
force user = morbius
```*[COLOR=Blue]Changing morbius with your own login user name.[/COLOR]* Where you put that line depends on what samba method you're using.

The exteranl drive will mount with you as owner and with permissions set to read/write to you only.

---

### Post by User0123 on 2010-06-30
Thanks Morbius. You sorted it =]

---


---
title: "Edit profile.ini in Ubuntu to lead to Windows profile"
date: 2010-12-21
forum: General Help
---

### Post by SpringHalo on 2010-12-21
I've already gotten into the .mozilla folder and found the profiles.ini file. My windows XP system has it's Documents and Settings folder on a seperate drive (D:\Documents and settings) And I've located the profile (application data\mozilla\firefox\profiles\) Now all I need to do is put the path into the profiles.ini file in the .mozilla folder in Ubuntu. The problem is I don't know exactly how to format it. In windows the path is:

D:\Documents and Settings\Administrator\Application Data\Mozilla\Firefox\Profiles

The profiles.ini file looks like this in the ubuntu folder:

[Profile0]
Name=default
IsRelative=1
Path=zp8i40jg.default

How would I translate this into something ubuntu "follows?" I already have the profile name changed as well.

Any help appreciated! 
-Spring

---

### Post by oldfred on 2010-12-21
Welcome to the forums.

It depends on where you mount your d: drive in Ubuntu. You need to have it as a permanent mount in fstab, so you do not have any issues.

This is my profile.in from Ubuntu:

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/mnt/shared/mozilla/firefox/profiles/wojjex8t.default

```

You have to change the IsRelative and add the path. Now my path is complex as I created a mount of /shared in /mnt and my /shared has several folders.

mkdir /mnt/shared
I then add this to fstab using my UUID from sudo blkid:
```
UUID=44332FD360AA9657                      /mnt/shared  ntfs-3g      defaults                             0  0  
```

And I have my files in a mozilla folder and inside the mozilla folder I have both Firefox & Thunderbird.

---


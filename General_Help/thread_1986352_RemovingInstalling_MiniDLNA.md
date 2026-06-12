---
title: "Removing/Installing MiniDLNA"
date: 2012-05-24
forum: General Help
---

### Post by ump001 on 2012-05-24
hi,

i had minidlna working fine until i encountered some issues where i thought it would be easier to remove and reinstall. I did the usual:
sudo apt-get remove minidlna

but it looks as though some of the files are still there, i removed them manually and tried to reinstall.

The app installs ok but minidlna.conf is not there and neither is the database path that minidlna requires.

Just want to know if there is a way to cleany remove the app entirely and reinstall as i did when i installed for the first time.

thanks for your help.

---

### Post by cariboo on 2012-05-24
I always use:

```
apt-get --purge <package_name>
```

From man apt-get:

> Use purge instead of remove for anything that would be removed. An
           asterisk ("*") will be displayed next to packages which are
           scheduled to be purged.  remove --purge is equivalent to the purge
           command. Configuration Item: APT::Get::Purge.

---


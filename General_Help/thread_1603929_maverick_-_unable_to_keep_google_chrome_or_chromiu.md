---
title: "maverick - unable to keep google chrome or chromium alive"
date: 2010-10-23
forum: General Help
---

### Post by swimfish on 2010-10-23
i've got issues with both google chrome and chromium.  nuking the config file will allow it to start fine, it bugs me about the usually import from other browser, and the 2 other questions there, however when i get to a fully blown browser, it crashes and dies, and i can't get them to launch ever again.

both config files which i've tried to nuke are in /home/user/.config

---

### Post by TeoBigusGeekus on 2010-10-23
Launch them from command line and post any error messages.

---

### Post by swimfish on 2010-10-23
google-chrome
[29897:29897:5436128376:ERROR:chrome/common/json_pref_store.cc(48)] Error reading Preferences: File doesn't exist. /home/bobcat/.config/google-chrome/Local State: No such file or directory
[29897:29897:5436202268:ERROR:chrome/common/json_pref_store.cc(48)] Error reading Preferences: File doesn't exist. /home/bobcat/.config/google-chrome/Default/Preferences: No such file or directory
Attempting to load the system libmoon 
Segmentation fault

chromium-browser
Attempting to load the system libmoon 
Segmentation fault

---

### Post by RBM on 2010-10-24
The issues appear to be moonlight, I was suffering with the same thing with google chrome closing shortly after opening. After removing libmoon it started working again.

---

### Post by dundacil on 2010-10-24
If this can be of any help, I had the same issue, which I sort of solved as per my post in _[http://ubuntuforums.org/showpost.php?p=10021491&postcount=10](http://ubuntuforums.org/showpost.php?p=10021491&postcount=10)_

---


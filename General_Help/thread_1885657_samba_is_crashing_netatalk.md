---
title: "samba is crashing netatalk"
date: 2011-11-23
forum: General Help
---

### Post by mattinsalto on 2011-11-23
Hello,
I've been running netatalk alongside samba without any problem with Ubuntu 11.04. Today I've installed Ubuntu 11.10 and netatalk. Everithing was OK until i've installed samba. With samba installed I can't access my shares via afp. Even stopping the service I can't access Ubuntu from Mac OS 10.7. If I uninstall samba everithing works again. Anyone knows a workaround for solving this :confused:?

Thanks in advance:).

---

### Post by mattinsalto on 2011-11-24
I don't know exactly how I fixed it, but now works :D. The only things I did are:
1. Install gnome-session-fallback to go back to gnome classic desktop:
[http://ubuntuforums.org/showthread.php?t=1859961]("http://ubuntuforums.org/showthread.php?t=1859961")

2. Stop netatalk:
sudo /etc/init.d/netatalk stop

3. Install samba:
sudo apt-get install samba

4. Start netatalk
sudo /etc/init.d/netatalk start

---


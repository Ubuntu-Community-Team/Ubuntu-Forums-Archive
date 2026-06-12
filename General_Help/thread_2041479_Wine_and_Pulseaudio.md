---
title: "Wine and Pulseaudio"
date: 2012-08-12
forum: General Help
---

### Post by Rixonomic on 2012-08-12
I'm following this guide - [http://wiki.winehq.org/WineAndPulseaudio](http://wiki.winehq.org/WineAndPulseaudio) - and it tells me to edit /etc/pulse/defualt.pa. How do I do this? When I try to save it, it says that I can't open the file for writing. I understand that this needs to be done as sudo and/or root, but that means very little to me. I'm fairly new to linux. Can anyone help me out?

---

### Post by oldos2er on 2012-08-12
First make a backup copy of the file to be edited: ```
sudo cp /etc/pulse/default.pa /etc/pulse/default.pa.backup
```

Now open it in gedit with root privileges: ```
gksu leafpad /etc/pulse/default.pa
```

You might need to reboot or restart pulseaudio for the changes to take effect.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Rixonomic on 2012-08-12
Okay, the code for the backup worked great! :D

But the code to open in gedit doesn't appear to do anything. Is there something I'm missing?

---

### Post by sienile on 2012-08-12
You might not have gksu installed.

```
sudo apt-get install gksu
```

---

### Post by nothingspecial on 2012-08-13
lubuntu doesn't ship with gedit, use leafpad instead.

---

### Post by oldos2er on 2012-08-13
Oops. Changed command in post #2 to work with leafpad. I'm assuming "gksu" still applies.

---


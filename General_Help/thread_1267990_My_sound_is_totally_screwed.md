---
title: "My sound is totally screwed"
date: 2009-09-16
forum: General Help
---

### Post by ade234uk on 2009-09-16
After an update yesterday my acer 8930G sound did not work. I followed some advice on other sites and now the situation is even worse. I have the volume control back, but when I goto System >> Preferences >> Sound I cannot get the controllers to come up.

I really need to go back to square one, so how do I remove all the packages that give me sound, so I can start with a clean slate again.

---

### Post by NightwishFan on 2009-09-16
Try this command to change volume:
```
alsamixer -c0
```

---

### Post by ade234uk on 2009-09-16
In order to get sound on this laptop I needed to install OSS
When I run alsamixer on it own from the terminal I get

alsamixer: function snd_ctl_open failed for default: No such file or directory

---

### Post by NightwishFan on 2009-09-16
You are using stock Ubuntu correct? Not Xubuntu or otherwise? I am asking so this command does not install GNOME if you use XFCE or other. Try this command:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by ade234uk on 2009-09-16
Yes I am running Ubuntu. Will this just re-install everything for me again?

---

### Post by NightwishFan on 2009-09-17
It will make sure you have all the needed packages for the Ubuntu system, it will not reinstall anything yet. If you are missing something, it will add it though.

---


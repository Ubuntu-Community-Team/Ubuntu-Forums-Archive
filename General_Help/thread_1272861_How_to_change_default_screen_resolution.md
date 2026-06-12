---
title: "How to change default screen resolution?"
date: 2009-09-22
forum: General Help
---

### Post by bcsikos on 2009-09-22
Hello everybody:

I am new to xubuntu/ubuntu. I have installed the latest stable xubuntu version, 9.04, on my computer.  Xubuntu set my screen resolution/refresh rate to 1152x863/75Hz. This looks very ugly on my CRT screen, furthermore I prefer 1024x768/85Hz. I can change the resolution in Applications -> Settings -> Display. However it last only until logout. After logging out the 1152x863/75Hz setup comes back. It is very inconvenient to change the setting after each logging in. How can I permanently change the default screen resolution? I tried 'dpkg-reconfigure xserver-xorg' but it has not led anywhere, it exited after keyboard configuration. I also find strange that the xorg.conf file does not have any concrete numbers, only stuff like "Configured Video Device", "Configured Monitor", "Default Screen".

Thansk for you help,
bcsikos

---

### Post by Thingymebob on 2009-11-23
I had a similar situation with crunchbang. I created a .xprofile file in the users home directory and in it used xrandr to change the resolution.
```

xrandr -s 1024x768

```
So the login screen is still at 1600X1280 while the desktop is 1024x768 and all the other modes are still selectable.

This would be better done in one of the gdm startup scripts (/etc/gdm) but I haven't found out which one yet.

---


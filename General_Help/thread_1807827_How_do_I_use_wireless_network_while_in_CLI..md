---
title: "How do I use wireless network while in CLI."
date: 2011-07-19
forum: General Help
---

### Post by Cammaaron on 2011-07-19
Without using Gnome or any type of GUI.

How would I enabled wireless networking using WEP security? (WPA not supported by router)
Reason being is that I am making server with my old laptop, however my parents will not allow it near the router and I can't afford a homeplug solution at this time.

---

### Post by TeoBigusGeekus on 2011-07-19
```
ifconfig wlan0 up
iwconfig wlan0 essid "insertSSIDhere" key s:insert_password_here
```

---

### Post by nothingspecial on 2011-07-19
If you can get a wired connection for a couple of minutes.....

```
sudo apt-get install wicd-curses
```

```
sudo service wicd start
```

Right arrow key to enter the config

Space selects stuff

I say this because although the Greek-Geek (no offence TeoBigusGeekus, I mean that with affection) is correct, to make that permanent, you need to edit stuff whereas wicd-curses is "almost" like a gui and (I would think) slightly easier.

---


---
title: "Curious: Howto make a .deb that just runs a script?"
date: 2010-12-13
forum: General Help
---

### Post by drewsus on 2010-12-13
I know, running a script is pretty easy itself, but some people (family, gf) just hate using the terminal and assisting them remotely, you have no idea what they are really doing on the other side of the screen. This way, they can essentially just double click and enter their password. 

Plus, I just want to know!

So, I was curious. How can I easily create a .deb package for this script:
```
#!/bin/bash

sudo apt-get install -y libnotify-bin

sudo apt-get purge -y firefox
sudo apt-get purge -y flashplugin-*
sudo apt-get purge -y adobe-flashplugin

sudo apt-get -y clean && sudo apt-get -y autoremove
sudo apt-get install -y firefox
sudo apt-get install -y flashplugin-installer

notify-send "Task Complete" "Firefox and flash player have been reinstalled." -i /usr/share/pixmaps/firefox.png
```

---

### Post by nolag on 2010-12-13
Make a program that calls system and executes the commands.  It is slower but making a .deb for it would be like making a deb for any program and should be easy :).

---

### Post by drewsus on 2010-12-13
sorry, but how?

---


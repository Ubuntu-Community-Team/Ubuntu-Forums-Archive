---
title: "killed xserver/gnome"
date: 2011-03-05
forum: General Help
---

### Post by nearlymagicman on 2011-03-05
Hey

i somehow screwed my xserver (I guess it is the xserver).

I got the following problem:

1)When i have 2 monitors connected, the cursor stays at the left one even though i select text on the right one.

2)(i plugged the left one out)As soon as i open a window and click on something in the window the window cannot be moved anymore, and the desktop cannot be selected anymore either (though u still can do something inside the window), as soon as you close the window (if you are lucky and there is a "close" button) the desktop can be used again.


This all started when i played a flash game which froze like everything but the game, and i had to restart the computer. I guess it somehow screwed the .conf file or the xserver. I already tried the xorg.conf.backup but it didn't help!

Hope this problem is familiar, don't feel like reinstalling my computer...


thx for your help

---

### Post by nearlymagicman on 2011-03-05
isn't really solved but i am now going to try to reinstall my OS... well thats probably faster than looking for an irradical error.

---

### Post by seawolf167 on 2011-03-05
You can try reconfiguring xserver-xorg and see if that helps

```
sudo dpkg-reconfigure xserver-xorg
```

Or you can reset back to default values with 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---


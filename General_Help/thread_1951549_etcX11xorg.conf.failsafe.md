---
title: "/etc/X11/xorg.conf.failsafe"
date: 2012-04-02
forum: General Help
---

### Post by Mariane on 2012-04-02
Who had the brilliant idea to include a file called:
/etc/X11/xorg.conf.failsafe ?

After fiddling with the nvidia-current package I rebooted and the computer said (on the screen) "no screen found". Neither xinit not startx could start the X server. 

In /etc/X11 I discovered I had a file called xorg.conf.failsafe
I did:

[code]
sudo cp xorg.conf.failsafe xorg.conf
sudo reboot now
[code]

AND IT WORKED!

So who is the person who saved my silly ***? I would really like to say a big thank you!

---


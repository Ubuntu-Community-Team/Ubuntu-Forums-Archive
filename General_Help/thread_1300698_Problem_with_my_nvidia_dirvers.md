---
title: "Problem with my nvidia dirvers"
date: 2009-10-25
forum: General Help
---

### Post by prasadchalasani on 2009-10-25
I updated my nvidia grahic card driver 185.18.36

The problem is I want set my resolution 1280x1024. when I changed the resolution it works fine. If I reboot the system it goes back to previous resolution. I try to save configuration in X-server it throws an error like this

Failed to parse existing X config file '/etc/X11/xorg.conf'!

Please help me I have to set every time I start system


regards
prasad

---

### Post by whoop on 2009-10-25
are you using "nvidia x server settings" app?
If so try launching it in root mode (command line):
```

gksudo nvidia-settings

```
Then change settings... save it to xorg. they should stick...

---

### Post by DarthScape on 2009-10-29
I used sudo and I still got this error.

---

### Post by OpenGuard on 2009-10-29
> **prasadchalasani said:**
> 
Failed to parse existing X config file '/etc/X11/xorg.conf'!


Because there's no xorg.conf in Karmic.


Create an empty configuration file:
```
sudo touch /etc/X11/xorg.conf
```Now, fire up nvidia-settings and try again ..

---

### Post by prasadchalasani on 2009-11-04
I solved this problem.

first I created a backup of xconf.org.

After that in Nvidia X Server Settings I changed setting my desired resolution, then I try to save to X configuration file. it throws an error "unable to remove old x config backup file  '/etc/X11/xorg.conf.backup'. I tried again to save the config. this time instead of pressing ok. there is a button show preview I clicked and copied entire text and click cancel..

After that 
in terminal 

gksudo gedit /etc/X11/xorg.conf

it asks for admin pass. enter password

then it opens the file in gedit. select the whole text and paste the copied text from show preview in Nvidia X sever settings

save and close.

reboot...

---


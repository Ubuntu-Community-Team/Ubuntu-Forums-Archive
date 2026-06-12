---
title: "gdm stop!"
date: 2010-01-07
forum: General Help
---

### Post by systembreak on 2010-01-07
hi all, 

I've been of my computer for a while, so I got some new updates and tried to install my nvidia-driver, but it seems that sudo /etc/init.d/gdm stop dosen't work anymore. 

What is the new way to stop the x-server?

-thanks

---

### Post by tommcd on 2010-01-07
> **systembreak said:**
> 
What is the new way to stop the x-server?

Are you running Karmic 9.10? Your profile says Hardy. If you are running Karmic then try this:
 Hit ctrl + alt + F2 to get to a virtual terminal. Then login and run:
```
sudo gdm stop
```
Then to restart X just run:
```
sudo gdm start
```
I think the reason /etc/init/gdm stop does not work anymore is due to the new **upstart** that now handles the bootup process:
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)


You could install the nvidia driver from the Ubuntu repos and this would not be necessary.

---

### Post by systembreak on 2010-01-07
Hi, 

yea im using karmic now. I tried the command you send me, but then it said:
WARNING ** : Failed to acguire org.gnome.Displaymanager
Warning ** : Could not acguire name; Bailing out.

? 

-thanks

---

### Post by Greenwidth on 2010-01-07
I think it's:
```
sudo service gdm stop
```

---

### Post by systembreak on 2010-01-07
Thanks :) that was it! 

- Thanks to all.

---


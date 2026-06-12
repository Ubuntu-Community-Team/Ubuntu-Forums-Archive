---
title: "Session Login with Environments"
date: 2011-05-12
forum: General Help
---

### Post by suryateja.sun on 2011-05-12
Hai,

I think I completely messed up my Desktop Environments.

I am using Natty with Unity and Gnome3 installed. Gnome3 got disappeared from Session menu while login and I can't able to login through Unity. So I decided to uninstall gnome3. 
I have done following steps.

```
user@computer:$ sudo apt-get remove libgtk-3-common
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get install gnome-panel
```

Then when I reboot, there is no startx server. When I tried it using startx command, it strucked up and never comes the Desktop sessions selection screen. So, I Installed XFCE. Still again the same thing happens. Then, I went to previous linux images recovered from grub and login to XFCE anyway. 

In between I tried to install gnome-session and this is the error I got.

```
The following packages have unmet dependencies:
gnome-session: Depends: gnome-session-common (=2.32.1-0ubuntu20) but 3.0.1-0ubuntu1~build2 is to be installed
E: Broken packages
```


How to get back that login to Desktop Environments? ( I am talking about [http://ihaveapc.com/wp-content/uploads/2011/04/Ubuntu-11.04-Classic-Gnome-Session-001.png](http://ihaveapc.com/wp-content/uploads/2011/04/Ubuntu-11.04-Classic-Gnome-Session-001.png))

---


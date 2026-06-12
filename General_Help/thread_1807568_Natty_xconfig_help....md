---
title: "Natty xconfig help..."
date: 2011-07-19
forum: General Help
---

### Post by Geezanansa on 2011-07-19
Recent upgrade to 64bit natty working good.  Really enjoy using my desktop when unity working.  I have though been having trouble configuring nvidia x server settings so that i)  my system boots ii) plymouth then log in screen loads iii)accelerated graphics works iv) unity works.
The way i am booting is through recovery options after loading grub cant see screen/garbled but guessed three down and enter.  System then boots into low graphics mode i log in to desktop then out and log back into safe mode for trying to reset unity and configuring nvidia x server settings.

When i try start nvidia x server settings i get > You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.So after opening a terminal and running  ```
sudo nvidia-xconfig
``` we get ```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```Then when i close terminal and save current configuration in the nvidia x server settings i get asked where the /etc/X11/xorg.conf file gets saved.

The default is /home/usr/.nvidia-settings-rc

Where should i save this file for it to be used as current and permanent xconfig file??

---

### Post by Geezanansa on 2011-07-19
Any advice or information on what i am doing wrong is welcomed.
I can  now boot my system without loading grub manually it now is loading automatically different format screen i choose normal kernel plymouth errors/does not mount but does get to log in screen after logging in no unity......
So basically after resetting unity and reconfiguring xconfig i have a bootable pc but not to its full potential ie no unity plymouth errors 
Any body willing to help out a new ubuntu user?
Any advice or information on what i am doing wrong is welcomed.:popcorn:

---


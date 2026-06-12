---
title: "how to boot windows xp as default operating system"
date: 2009-09-11
forum: General Help
---

### Post by mrakesh85 on 2009-09-11
Hai,
      I am having windows Xp as well as ubuntu in my system. Grub is shows both my operating systems. By default  after five seconds ubuntu is loading, I want windows xp to be loaded by default. How to change it.

Rakesh

---

### Post by travmon69 on 2009-09-11
install startupmanager.  it is in synaptic package manager.  or use  terminal an use this "  sudo apt-get install startupmanager  "

---

### Post by Efwis on 2009-09-11
open terminl then

```
sudo apt-get install startupmanager
```

---

### Post by pastalavista on 2009-09-11
Install StartupManager. It makes it easy. It's in the repositories (Synaptic) or install it with terminal```
sudo apt-get install startupmanager
```It will be in the System > Administration menu.

edit: haha.. great minds think alike

---

### Post by j7%&lt;RmUg on 2009-09-11
Theres also an option in your grub boot file if startup manager doesnt play nice.

---

### Post by faical117 on 2009-09-11
backup menu.lst before y modify this file !

in terminal :
sudo gedit /boot/grub/menu.lst

move this before the linux part
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by digitalpbk on 2009-11-09
NOTE : For Ubuntu 9.10 Karmic Koala Users

Just change the default from 0 to most probably 4 on the /etc/default/grub file and run update-grub

for detailed instructions and samples check out 
[Changing default boot OS on ubuntu 9.10]("http://digitalpbk.com/2009/11/changing-default-boot-os-grub-ubuntu-910")

---

### Post by murthy on 2009-12-16
After trying changing the default to 4 in /default/grub and running update-grub, nothing has happened, ubuntu itself is booting.  Help.

---


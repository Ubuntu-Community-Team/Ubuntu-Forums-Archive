---
title: "How do I run this script on boot"
date: 2009-07-06
forum: General Help
---

### Post by ZettaGeek on 2009-07-06
How do I run this script on start up of the computer? Preferably it would automatically type the SUDO password as well.

```
sudo rmmod ndiswrapper
sudo rmmod b43legacy
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo modprobe ndiswrapper
```

Thanks for your help!

---

### Post by Emper on 2009-07-06
Check out init.d script
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by ZettaGeek on 2009-07-06
Am I supposed to put my boot scripts in the init.d folder? If so, that still doesn't help me with the automatic SUDO password. That way, I don't have to enter the pass every time the computer boots.

---

### Post by eldragon on 2009-07-06
if its in the init script, you dont need to run it with sudo, its already run by root

anyway, it seems you need to learn how to blacklist kernel modules instead...

---

### Post by nothingspecial on 2009-07-06
Put the modules you don`t want in /etc/modprobe.d/blacklist.conf

Put the one you want in /etc/modules

---

### Post by Dr Small on 2009-07-06
You can either do as nothingspecial suggested, by putting the modules that you want blacklisted/probed in their correct files, or you can add your commands to the /etc/rc.local file, and just drop off the sudo commands, since that file is executed as root.

Just be sure to add your commands before `exit 0` :)

Dr Small

---


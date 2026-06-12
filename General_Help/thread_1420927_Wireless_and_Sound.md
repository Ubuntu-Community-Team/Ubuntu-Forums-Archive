---
title: "Wireless and Sound"
date: 2010-03-03
forum: General Help
---

### Post by Brotherbrat13 on 2010-03-03
The Title says Xubuntu, but I have had to do this on Ubuntu as well.

The First issue is that whenever I turn on my computer, the sound is muted. Its not a big issue, but it is an annoying one to have to un-mute it then turn the volume back up. I solution for that would be awesome.

The second one is a little worse. To get my wireless USB Stick (Linksys  WUSB100 Version 2) to turn on, I need to run the command (Found in another thread)

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
```In the thread, it says that you only need to run the command once.. but I have to run it whenever I do anything that has me restart the computer.

My question is, is there a way that I can have that script run automatically when the computer turns on? Or even better a permanent fix for my Wireless USB stick?

Thanks in Advanced~

---

### Post by Bradj47 on 2010-03-03
> **Brotherbrat13 said:**
> The Title says Xubuntu, but I have had to do this on Ubuntu as well.

The First issue is that whenever I turn on my computer, the sound is muted. Its not a big issue, but it is an annoying one to have to un-mute it then turn the volume back up. I solution for that would be awesome.

The second one is a little worse. To get my wireless USB Stick (Linksys  WUSB100 Version 2) to turn on, I need to run the command (Found in another thread)

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
```In the thread, it says that you only need to run the command once.. but I have to run it whenever I do anything that has me restart the computer.

My question is, is there a way that I can have that script run automatically when the computer turns on? Or even better a permanent fix for my Wireless USB stick?

Thanks in Advanced~

Add the script to System -> Preferences -> Startup Programs (or something along those lines)

---


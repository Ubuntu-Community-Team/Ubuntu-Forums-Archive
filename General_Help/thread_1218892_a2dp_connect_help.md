---
title: "a2dp connect help"
date: 2009-07-21
forum: General Help
---

### Post by kingmoffa on 2009-07-21
Hi All, 

Im trying to script a few commands to use my bluetooth a2dp speakers. 

Good news is that I have it all setup and working inside a GUI using the blueman applet and some alsa .asoundrc

I want to remove the blueman part of things because I want to set things up by pressing a button on a IR remote with lirc and irexec (which works) to execute my scripts. 

So - my question is this - how can I get ubuntu to connect to a a2dp blueooth device without using bluetooth applets like gnome-bluetooth or blueman? Something that I can execute upon reboot and/or script execution.

I know the MAC address of the speakers and have already paired with blueman. 

Thanks in advance.

---

### Post by zzzBrett on 2009-07-24
> **kingmoffa said:**
> Hi All, 

Im trying to script a few commands to use my bluetooth a2dp speakers. 

Good news is that I have it all setup and working inside a GUI using the blueman applet and some alsa .asoundrc

I want to remove the blueman part of things because I want to set things up by pressing a button on a IR remote with lirc and irexec (which works) to execute my scripts. 

So - my question is this - how can I get ubuntu to connect to a a2dp blueooth device without using bluetooth applets like gnome-bluetooth or blueman? Something that I can execute upon reboot and/or script execution.

I know the MAC address of the speakers and have already paired with blueman. 

Thanks in advance.


This may help:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)


sudo hidd --connect aa:bb:cc:dd:ee:ff

---

### Post by kingmoffa on 2009-07-27
thanks for the help - I needed to install bluez-compat to get the hidd command. 

My machine hasn't had to be rebooted for a while (its a mythtv server) - once It has been then I can figure out if this command will work.

---


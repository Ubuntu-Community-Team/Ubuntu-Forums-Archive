---
title: "bluetooth"
date: 2012-03-10
forum: General Help
---

### Post by Rakeshvijayan on 2012-03-10
how can i connect my phone bluetooth to my laptop ,

see attachment 
this is the window when i click on the preferences from right bottom,from the drop down window shows that bluetooth is enabled . how can i possible this

---

### Post by WthIteh on 2012-03-10
The top panel bluetooth icon is out of sync with the real bluetooth status which is shown in that preference window.
Click on that "off" button in the preference window to enable your bluetooth.
If it did not work, also type this in terminal:
```
sudo service bluetooth start
```

---

### Post by Rakeshvijayan on 2012-03-11
> **WthIteh said:**
> The top panel bluetooth icon is out of sync with the real bluetooth status which is shown in that preference window.
Click on that "off" button in the preference window to enable your bluetooth.
If it did not work, also type this in terminal:
```
sudo service bluetooth start
```


Thanks for the replay ,I tried with your suggestion but that doesnt work for me, please the screen shot

---

### Post by Kirboosy on 2012-03-12
What type of computer is it? I know my Dell Duo has to have a special driver installed in order to use Bluetooth correctly.

---

### Post by Rakeshvijayan on 2012-03-12
> **Caboose885 said:**
> What type of computer is it? I know my Dell Duo has to have a special driver installed in order to use Bluetooth correctly.

Toshiba x4014 c640

---

### Post by Kirboosy on 2012-03-12
Well I'm not sure if this Driver will help any but its worth a shot

[Bluetooth Driver]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/+attachment/1913129/+files/ar3011-dkms_1.1ryu2.3_all.deb")

I can't seem to find any info on your laptop and ubuntu. Just install the package above and reboot. See if that fixes the issue.

---

### Post by Rakeshvijayan on 2012-03-12
> **Caboose885 said:**
> Well I'm not sure if this Driver will help any but its worth a shot

[Bluetooth Driver]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/+attachment/1913129/+files/ar3011-dkms_1.1ryu2.3_all.deb")

I can't seem to find any info on your laptop and ubuntu. Just install the package above and reboot. See if that fixes the issue.
  same result , I am not able to enable the settings from preference option on the bluetooth button

---


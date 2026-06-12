---
title: "Startup script with root privileges"
date: 2009-10-07
forum: General Help
---

### Post by nsac on 2009-10-07
I want to add a script to start at boot or login & it needs root privileges.

```
sudo echo none > /sys/class/leds/iwl-phy0::RX/trigger
sudo echo none > /sys/class/leds/iwl-phy0::TX/trigger
sudo echo none > /sys/class/leds/iwl-phy0::radio/trigger
sudo echo none > /sys/class/leds/iwl-phy0::assoc/trigger
```

Running the script from a terminal works (wifi led turns off) but it won't start at boot. I tried adding it to init.d & running update-rc.d & nothing. I tried adding root access to the file using visudo NOPASSWD & nothing. Doesn't work adding it to startup applications either. 

Any ideas?

---

### Post by Baelus on 2009-10-07
> there is a file called /etc/init.d/rc.local

it is run last (after all of the other startup scripts)

it's runs as root

This is post #7 from [http://ubuntuforums.org/showthread.php?t=181041]("http://ubuntuforums.org/showthread.php?t=181041")

I would remove all the sudo's from the script as they will be executed as root anyway.

---

### Post by nsac on 2009-10-07
I tried adding it to rc.local & didn't work, or rather it worked for about a second & then something else triggered the led class. So I think I need to run the script after everything is done loading, but adding it to Startup Applications doesn't work even with the NOPASSWD option enabled.

---


---
title: "Wireless needs enabling on boot"
date: 2010-11-03
forum: General Help
---

### Post by mouldy on 2010-11-03
Hey guys,

After my previous stint with 10.10 I've gone back to 10.04 because it boots in 20 seconds instead of 70+ and 10.10 didn't really seem to offer much new stuff that I need. Except one thing. When 10.10 boots, it automatically connects to whatever wireless network is set to Auto. 10.04 however, doesn't. I have to right click the tray applet and click on "Enable Wireless" and only then does it connect to the Auto networks. After a reboot, it's forgotten that I've clicked on "Enable Wireless" and I have to do it all over again.

I've found [this](http://ubuntuforums.org/showthread.php?t=1471456&page=4) thread that seems to describe the same problem and the only working suggesting is to use wicd instead of network-manager.

Does anybody know of a way to make it work using network manager? Do you know what command clicking on "Enable Wireless" runs - if I could just run that in an init script, problem solved. I thought it would be;
ifconfig wlan0 up 
but that doesn't seem to do anything at all (wlan0 is definitely the right adapter)

Thanks

---

### Post by cpmman on 2010-11-03
The rfkill command is the cli to use.

e.g.

```
rfkill list
```

shows current state

```
rfkill unblock wlan0
```

will unblock soft blocking of wlan0

---

### Post by mouldy on 2010-11-03
> **cpmman said:**
> The rfkill command is the cli to use.

e.g.

```
rfkill list
```

shows current state

```
rfkill unblock wlan0
```

will unblock soft blocking of wlan0

Thanks. Using rfkill doesn't seem to do anything though.

rfkill list shows;
```
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
I've tried;
rfkill unblock wlan0
rfkill unblock 0
rfkill unblock wlan
rfkill unblock wifi
rfkill unblock all

And running rfkill list afterwards always states that acer-wireless is still soft blocked.

---

### Post by cpmman on 2010-11-03
```
man rfkill
```

for more options

---

### Post by mouldy on 2010-11-03
> **cpmman said:**
> ```
man rfkill
```

for more options

Thanks, but rfkill doesn't seem to have a man page in Ubuntu, but I googled and found one anyway. There doesn't seem to be any information that's not already in rfkill help though. That's where I figured out the various rfkill unblock xyz commands I posted earlier.

I ran `rfkill event` and then enabled the wireless using the network manager applet and the rfkill event process didn't come up with anything - shouldn't it have noticed that the wireless was enabled?

Also, when I run `rfkill list` after I've enabled the wireless from the network manager applet, it still says that my acer-wireless is soft blocked...but it works, so I don't really understand that. Maybe rfkill isn't the right tool to use?

Does anybody have any more ideas, or any ideas why I can't seem to get rfkill to work?

Thanks (:

---

### Post by mouldy on 2010-11-04
Sorry to bump, but does nobody else have any ideas?

Thanks (:

---


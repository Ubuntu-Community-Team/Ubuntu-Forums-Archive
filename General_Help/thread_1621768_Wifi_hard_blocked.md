---
title: "Wifi hard blocked"
date: 2010-11-14
forum: General Help
---

### Post by Blodskaal on 2010-11-14
I've got an HP Elitebook 8530w, with an Intel wifilink 5300 agn. It's dual booted with Ubuntu 10.10 and Windows 7
Recently my windows fried, as it does ever so often. I reinstalled it and started to curse it for erasing my bootloader. Reinstalling GRUB from a live boot didn't work, so I reinstalled ubuntu 10.04 without formatting / to keep my data. Everything works fine now again except my wifi. This is the problem:

The wifi switch is turned on on my laptop.

```

root@laptop:/home/user# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
root@laptop:/home/user# rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```Now I turn the wifi switch on my laptop to off.
```

root@laptop:/home/user# rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```As you can see in both modes, phy0 is hard blocked.

I tried most conventional and unconventional solutions on the web already, which didn't work. Please help me, as I need wifi on the campus to do my homework.

---

### Post by Blodskaal on 2010-11-15
It started by itself again. I'll mark this thread fixed if it stays on after a few reboots.
No idea why it's working once again though... I'm pretty stumped. I've been messing around with it all day yesterday to no avail. Still who am I to complain when things fix themselves for me ^^

EDIT:
I realised now why it's working. Apparently my WLAN interface gets hard blocked now when I connect by wire. This is a new "feature", though I've no idea where it came from. Apparently one or more of my attempts to fix my WLAN after it broke have worked, but as I was connected by wire, my WLAN was hard blocked. This morning at the campus I was using my laptop in a lecture room without wired connection present and my wireless started automatically.

EDIT2:

For those who come across this thread while trying to fix their WLAN I can recommend:
```
#rm /dev/rfkill
#reboot
```

---

### Post by Hippytaff on 2010-11-15
Also any blocks can be unblocked by
```

rfkill unblock all

```
:-)

---

### Post by floorripper on 2011-09-12
Hello,


I had the same issue. Thank you for your hint. is it functionality of the Ubuntu or it is HP isssue? (security feature
)
Is there any way how to have active both interfaces for the same time? 

Eth1 and also wlan01 ??

Thanks

---

### Post by quick-dudley on 2011-10-22
I was having similar trouble, but then I found out the wifi button stops working when I've got my mobile phone plugged in for charging.

---


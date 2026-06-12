---
title: "Network manager disabled after suspending.."
date: 2010-05-14
forum: General Help
---

### Post by qwerty123321 on 2010-05-14
What happened:

- I run out of battery (laptop)
- I believe Kubuntu tried to suspend to disk, but that failed, the system froze
- after reboot the system tray applet just told "network manager disabled" 
How do I fix this ??..
 I tried but after entering the second line of code it says no such file/directory exist...
```
service network-manager stop
rm /var/lib/NetworkManager/NetworkManager.state
service network-manager start
```

---

### Post by cottfcfan on 2010-05-14
Same thing happened on my desktop.
You need to edit the file:
root/var/lib/networkManager/networkmanager state
and make sure all the options are set to true.
 For some reason after suspend/freeze it sets itself to false.

---

### Post by pytheas22 on 2010-05-14
What is the output if you type:

```
/etc/init.d/network-manager status
sudo /etc/init.d/network-manager restart
sudo /etc/init.d/networking restart
```

---

### Post by chaosgrimm on 2010-05-14
Check both of these, should be:

/etc/NetworkManager/nm-system-settings.conf

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

-------
and

/var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

---


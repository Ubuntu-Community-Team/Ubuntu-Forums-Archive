---
title: "Network Manager disappeared from taskbar"
date: 2012-06-04
forum: General Help
---

### Post by Nando88 on 2012-06-04
I installed lubuntu 12.04, and discovered that the network manager does not appear in the taskbar, and I don't know how to bring it back.
I updated the network manager via synaptic, but it still dowsn't show up.
Someone please help me!
Thanks in advance!

---

### Post by Rex Bouwense on 2012-06-04
Right click the panel.  You can get to panel preferences as well as add/delete from there.

---

### Post by Nando88 on 2012-06-04
The only similar apps I find are: Network status Monitor and Manage Networks.
I think its the Manage Networks app, but the thing is that when I try to add it, it does not appear in the taskbar.
Please tell me another way to fix this.
Thanks in advance!

---

### Post by wildmanne39 on 2012-06-04
Hi, try this:
```
sudo apt-get install --reinstall network-manager network-manager-gnome
```
Thanks

---

### Post by Steve Kroon on 2012-06-13
I have the same problem, but can't try reinstalling anything *because the network doesn't work*.  Running ifconfig only shows lo0.  eth0 and wlan0 have disappeared...

---


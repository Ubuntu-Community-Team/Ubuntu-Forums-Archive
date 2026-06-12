---
title: "Connecting to a network...."
date: 2011-02-18
forum: General Help
---

### Post by gaultwizard on 2011-02-18
I am currently using xubuntu 10.04 but can not seem to figure out how to connect to a wireless network. It says that the wireless network is off and I am unconnected. Help is appreciated.

---

### Post by Hippytaff on 2011-02-18
hi and welcome to the forums

what is the output of ```
lspci | grep -i net
```

try```
ifconfig [the name of your wireless controller - usually iw0, but for me eth0] up
```

---

### Post by gaultwizard on 2011-02-18
I  checked network i con and it says that the device is not ready. How do i make it ready? If you couldn't tell I am new to the whole Ubuntu system, so sorry if i sound like a noob.

---

### Post by Hippytaff on 2011-02-19
try turning it off and on again first.

Then if the name of your wireless connection is iw0 (which it sometimes is though mine is eth0) then type
```
ifconfig iw0 up
``` find out the name of your wireless connection with the lspci code in my previous post

---


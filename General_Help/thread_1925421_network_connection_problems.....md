---
title: "network connection problems...."
date: 2012-02-14
forum: General Help
---

### Post by K4NEB on 2012-02-14
Hey everyone 

currently running 11.10

lately my computer has decided it no longer likes connecting to the Internet :(

i use a belkin wireless g  usb thingy and i could connect fine automatically on startup but after ten minutes of browsing connection disappeared, even though it was still connected :(

only way to get connection back was to restart, F ing annoying. 

then it stopped detecting the router all together and now does nothing :(

so now i have pulled it out and found my Ethernet cable. but even with it the cable plugged in the computer does not detect it it takes a few plugs and un plugs to get it to register so i can use the Internet :( 

anyone else having connection problems? just wondering if its maybe my router or my system.

if anyone has any advice i would be very great full thank you   

:guitar:

---

### Post by K4NEB on 2012-02-16
Ok well not that any one has replied but ive fixed it now, seems it was the usb port, works fine in a different usb port

---

### Post by jonobr on 2012-02-16
Hi there,

Just for future reference if you are having trouble like this again, may be worth while running ifconfig in terminal to see if you getting an ip address from your DHCP server.


If not, then you could type the following command in terminal

```
sudo /etc/init.d/networking restart
```

If you still cannot get an IP address you could try posting the results of 

```
lshw -C network
```
and maybe look through your dmesg to see if you get an error indication message there,.

---


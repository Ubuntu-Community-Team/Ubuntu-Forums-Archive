---
title: "connecting to wireless problem"
date: 2006-03-12
forum: General Help
---

### Post by niyazb on 2006-03-12
Am new to Linux I have installed Linux ubuntu on my laptop everything seems to be working fine except my wireless connection causing me lots of problems 

I have installed Linux while am in university so it picked all wireless settings of university wireless network  when I was back home tried to connect to home wireless network but its refusing to connect to the network 

I have tried to modify all the settings i.e. DNS, IP address but no luck.
I am struggling with this problem for almost 2 days. 

thanks.

---

### Post by Titus A Duxass on 2006-03-12
We'll need a little more info. before we can give help.

Card details, etc.
results of:

lspci
iwconfig

details of your /etc/network/interfaces file, etc.

---

### Post by sadjack on 2006-03-12
Does it connect to your uni network ok? 

Does it see you home network but just will not connect?

---

### Post by niyazb on 2006-03-12
yes its connecting wiht uni network 
but not able to switch it to any other wireless network :-(

---

### Post by niyazb on 2006-03-12
Well am new to linux i have figure out how to use these commands..

---

### Post by sadjack on 2006-03-12
OK so we know the card works.

Do you have KWifimanager installed. See "Applications - Internet"

If you do you can set up several configurations, one say for your university and one for the home network and activate the one you want.

I would also look at stuff like WEP encryption to make sure you have it configured correctly and whether your computer and network are compatible ie is one set for dhcp and the other fixed ip addresses.

---

### Post by niyazb on 2006-03-12
Thanks guys its seems to be working
Thank you very much:)

---


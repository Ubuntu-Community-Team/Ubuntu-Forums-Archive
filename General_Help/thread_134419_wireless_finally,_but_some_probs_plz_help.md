---
title: "wireless finally, but some probs plz help"
date: 2006-02-21
forum: General Help
---

### Post by crxyem on 2006-02-21
Well I was finally able to get my wireless nic up and running using ndiswrapper, onto the next problem I have to do the following everytime a I boot/re-boot 

```

iwconfig wlan0 mode Managed
iwconfig wlan0 essid {my AP name}
iwconfig wlan0 key {hex key}
dhclient -r
dhclient wlan0

```

after that is all said and done my wireless nic works and I can browse the net and my local lan etc.. 
any ideas ?

---

### Post by jchau on 2006-02-22
if you do a "man wireless", you will see at the bottom:
> DEBIAN 3.0
       In Debian 3.0 (and later) you can  configure  wireless  LAN  networking
       devices using the network configuration tool ifupdown(8).

       File : /etc/network/interfaces

       Form : wireless-<function> <value>
              wireless-essid Home
              wireless-mode Ad-Hoc

       See also :
              /etc/network/if-pre-up.d/wireless-tools
              /usr/share/doc/wireless-tools/README.Debian




This should point you in the right direction.  Hope this helps... Take a look.

---

### Post by Prospero2006 on 2006-02-22
My laptop has slackware set up for wardriving, and activating the network card also requires a series of commands like that. I wrote a bash script to execute those commands and then added it to the boot up sequence. 
Also, you can add a desktop icon pointing to the script. 

This way it becomes a no brainer, and you can easily configure the script you have written to accomodate whether you are using static ip, dhcp, or whatever.

Pros

---

### Post by crxyem on 2006-02-22
well, setting up wpa_supplicant , and ditching WEP solved my problems
so in the long run, more secure, and my nic configs on bootup

thanks for the ideas tho

---


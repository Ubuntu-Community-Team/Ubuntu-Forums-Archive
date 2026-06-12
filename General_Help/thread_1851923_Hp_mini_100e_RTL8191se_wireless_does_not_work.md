---
title: "Hp mini 100e RTL8191se wireless does not work"
date: 2011-09-29
forum: General Help
---

### Post by barteks on 2011-09-29
Hp mini 100e RTL8191se wireless does not work
 
I am working for school as a technician and need to install ubuntu on 100 mini laptops 
I have tried to install linux drivers from Realtek website. but no luck. Any ideas?

---

### Post by 3rdalbum on 2011-09-29
What version of Ubuntu are you using?

When you say "I've tried to install linux drivers from the Realtek website but no luck", what exactly prevented you from installing the driver? What error message did you get, at what point did you get it, and what did the error message say?

As a technician I'm sure you'll appreciate that we really need as much information as you can provide :-)

---

### Post by gandaran on 2011-09-29
> **barteks said:**
> Hp mini 100e RTL8191se wireless does not work
 
I am working for school as a technician and need to install ubuntu on 100 mini laptops 
I have tried to install linux drivers from Realtek website. but no luck. Any ideas?
what version of Ubuntu? I believe this realtek RTL8191se chipset works out of the box on Ubuntu 11.04 only.

---

### Post by barteks on 2011-09-29
ubuntu 11.04 - natty narwhal.
I didn't get any error message during installation so I assume installation was succesful 
when i type in Terminal: **[COLOR=royalblue]rfkill list all[/COLOR]** 
**hp-wifi: Wireless LAN**
Soft blocked: yes
hard blocked: yes
**phy0: Wireless LAN**
Soft blocked: yes
hard blocked: no
 
Any ideas

---

### Post by barteks on 2011-09-29
I believe drivers are ok but they are blocked or deactivated somehow by Ubuntu.

---

### Post by barteks on 2011-09-29
WOOOOOW
I have  tried those commands 
 
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
 
and get wireless working, but after restart it stopped again.
I need to type commands again after each restart.
[COLOR=darkred]How I can setup wireless permanently so its working on every reboot?[/COLOR]

---

### Post by bkratz on 2011-09-29
> **barteks said:**
> WOOOOOW
I have  tried those commands 
 
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
 
and get wireless working, but after restart it stopped again.
I need to type commands again after each restart.
[COLOR=darkred]How I can setup wireless permanently so its working on every reboot?[/COLOR]


The first thing I would do is add to hp-wmi module to the blacklist file

```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
exit


```

Next to make the others happen I would add

gksudo gedit /etc/rc.local
Add a line above exit 0:

```
rfkill unblock all

```

At reboot it should all happen for you!

---

### Post by barteks on 2011-09-30
That solved the problem. Thanks a lot BKRATZ.

---

### Post by 1John on 2011-10-17
This works for me it fixed the problem on my wife's 100e. There are a few other threads around where this solution would help. How do we let others know? Also I would like to know what we would need to do to ensure this works out of the box for other new users as these are the type of users who will be on the 100e. Why is a working driver somehow blocked?

---


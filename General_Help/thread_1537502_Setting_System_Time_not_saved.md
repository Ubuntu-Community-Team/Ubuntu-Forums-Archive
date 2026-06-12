---
title: "Setting System Time not saved"
date: 2010-07-23
forum: General Help
---

### Post by oxf on 2010-07-23
Right now I'm 2hrs ahead of my normal time zone, i.e. the time zone I chose when I installed. So I changed the system clock right , ie right click Time > Prefferences. But when I re-boot it keeps reverting to the original time. 

What am I doing wrong???
Thanks

---

### Post by ajgreeny on 2010-07-23
Nothing.

The clock in the panel is, I think, synced to NTP servers, and will reset itself to your timezone when you log in at boot time.  Change your timezone temporarily whilst in this different time.

---

### Post by cavalier911 on 2010-07-23
The computer's motherboard clock on Linux/Unix is set to UTC. When you choose a timezone it is offset plus or minus from UTC. If your dualbooting windows,it sets the motherboardclock to realtime which makes linux time wrong. The explanation on how to fix this is in the link below.
Let's see what is happening with your offset.
Reboot so your time is wrong. 
Open terminal:
```
diff -s /etc/localtime /usr/share/zoneinfo/`cat /etc/timezone`
```1.What zoneinfo is /etc/localtime set to ?
```
sudo dpkg-reconfigure tzdata
```Set to your correct timezone.
Use the up/down arrow keys and tab to OK then enter
2.Now run this command again to verify the change to your localtime.
```
diff -s /etc/localtime /usr/share/zoneinfo/`cat /etc/timezone`
``` Reboot
If the time has switched back rerun.
 ```
diff -s /etc/localtime /usr/share/zoneinfo/`cat /etc/timezone`
```Did /etc/localtime switch back what it was in 1. ?
This may help: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by oxf on 2010-07-25
> **ajgreeny said:**
> Nothing.

The clock in the panel is, I think, synced to NTP servers, and will reset itself to your timezone when you log in at boot time.  Change your timezone temporarily whilst in this different time.

Thanks, I didn't realise that! I reset the time zone to eastern Europe and it's displaying the correct time now...

> **cavalier911 said:**
> The computer's motherboard clock on Linux/Unix is set to UTC. When you choose a timezone it is offset plus or minus from UTC. If your dualbooting windows,it sets the motherboardclock to realtime which makes linux time wrong. The explanation on how to fix this is in the link below.
Let's see what is happening with your offset.
Reboot so your time is wrong. 
Open terminal:
```
diff -s /etc/localtime /usr/share/zoneinfo/`cat /etc/timezone`
```1.What zoneinfo is /etc/localtime set to ?
This may help: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

Thanks anyway. Doesn't seem like I have any problem but will read up anyway!

---

### Post by rtimai on 2010-07-27
Cavalier911, thanks for the info. My system time (Lucid) recently began displaying 1 hour ahead of local time, in both the login screen and Gnome Desktop after logging in, despite no recent changes in my registered timezone. Your post made me aware of the several methods of time tracking and how many systems use many different methods of accessing the information. I found that my hardware clock (CMOS) was set to timezone America/Chicago (CDT, correct, even though I'm near Nashville TN) while the "Time & Date" tool (time-admin) was set to Monticello KY, which I thought to be closest to Nashville, but turns out is in EDT. Sometimes selecting one's timezone from a map can be entirely counter-intuitive!

So then, I used 'sudo dpkg-reconfigure tzdata' to change the timezone in Linux to match the Hardware Clock (America/Chicago,) then confirmed that it was changed in the time-admin tool. Now restarting does not set Linux system time a hour ahead.

Oddly enough my timezone has been set to Monticello KY since Feisty, and I never had any time adjustment symptoms. There must have been some recent fix in Ubuntu which began to detect the discrepancy in my system.

Thanks again for your good info. I will read the UbuntuTime link you suggested also.

---


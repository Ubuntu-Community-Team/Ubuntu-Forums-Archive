---
title: "Network or LAN problems"
date: 2011-09-06
forum: General Help
---

### Post by crackedmaster on 2011-09-06
Hi and Hello, I'm just getting to know ubuntu 11.4, I just installed it a week ago. I can connect to the internet using the wifi but it seems my laptop which is running ubuntu 11.4 cannot access other pc on our network, I can't seem to view their files and I can't print to our network printer since I can't see it. In this foundation I'm the network manager but I feel that I'm blind since I can't get my laptop to work right since installing ubuntu 11.4. Please help me make things right, is their a software which will help me monitor and control the other pc's, so that I will know what sites each user visits and what they are doing during office hours.

Thank you very much for your help and I know ubuntu will make my life easier.

---

### Post by axatrikx on 2011-09-06
is it properly shared? can the other users see each other?

---

### Post by Drenriza on 2011-09-06
can you by running ```
arp
``` se other devices?

Are you running any servives like samba?

---

### Post by crackedmaster on 2011-09-06
I ran arp in the terminal and it worked fine

[COLOR="Red"]nathan@nathan-Satellite-U200:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   c0:c1:c0:e7:a0:7f   C                     wlan0
nathan@nathan-Satellite-U200:~$ [/COLOR]

All the windows based pc are communicating except for me and I'm not running
samba, I'm just new with Ubuntu...

Please help me....

---

### Post by e79 on 2011-09-07
For accessing the Windows Shares
Install CIFS support:

```
sudo apt-get install smbfs
```and have a look here :
[http://ubuntuforums.org/showthread.php?t=1655434](http://ubuntuforums.org/showthread.php?t=1655434)

For printing, check your manufacturer's website to see if they have drivers for Linux if your laptop cannot query the printer by default and/or does not have the drivers installed by default. As this could be an extensive topic, I won't say more for now; but be sure to check the forum for your printer model and number.

As for monitoring, restricting and spying users habits, I suggest you open another thread as this would be another extensive topic on its own.
 
Hope this helps

---

### Post by crackedmaster on 2011-09-17
Still no developments on connecting to the network. It's been a month that I can't connect to the network and print to any printer since ubuntu can't seem to find the other Win7 and WinXP computer connected to the LAN. Please help me resolve this issue.

---


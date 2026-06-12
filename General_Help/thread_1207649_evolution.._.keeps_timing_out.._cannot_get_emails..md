---
title: "evolution.. .keeps timing out.. cannot get emails."
date: 2009-07-08
forum: General Help
---

### Post by beanco on 2009-07-08
I have been having a problem with emails and web browsers actually

Evolution will not work

it starts up, I hit send/receive

I get the Sending & Receive Mail dialogue box..

I see GEtting message 1 of 9

smtp: smpt.datanet.hu

Complete


now, if I start up evolution from the CL then after a minute or two that dialogue box dissapears.

IF I start evolution up from the desktop.. I see the same as above, then I get a timed out error msg....

robi

ps. I am using a router, plugged into the box.. the kids use the WiFi.. no worries.

I cannot use any browsers.. they time out tooo

I can use remote desktop...

---

### Post by beanco on 2009-07-09
here is a thread i have asking similar questions and ideas ppl have given me to try out

[http://ubuntuforums.org/showthread.php?t=1202662](http://ubuntuforums.org/showthread.php?t=1202662)

somebody out there in Ubuntuland please help me..

robi

---

### Post by unutbu on 2009-07-09
Can you access email from the "kids" laptop?

---

### Post by beanco on 2009-07-09
> **unutbu said:**
> Can you access email from the "kids" laptop?

yeah,,, i have full range of web apps on the laptop.... i use the web mail service of my ISP from the kids' mac.....


any ideas?

robi

---

### Post by unutbu on 2009-07-09
Could you post
```

ifconfig
route -n
```

---

### Post by beanco on 2009-07-09
> **unutbu said:**
> Could you post
```

ifconfig
route -n
```

ifconfig got me this

etho link encap:Ethernet HWddr 00:13:D4:E8:C7:61
 
inet addr:192.168.0.50  Bcast: 192.168.0.255 Mask:255.255.255.0

UP BROADCAST RUNNING BULTICAST MTU:1500 Metric:1

RX packets:27 errors:0 dropped:0 overruns:0 frame:0

TX packets:387 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueeulen:100

RX bytes:3231 (3.1 KiB) TX bytes:5388 (5.2 KiB)

Base address: 0xe800 Memory:fbfe0000-fc000000



lo Link encap:Local Loopback

inet addr:127.0.0.1 Mask:255.0.0.0

UP LOOPBACK RUNNING MTU: 16436 Metric:1

RX packets:2 errors:0 dropped:0 overruns:0 frame:0

TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0

RX bytes:100 (1000 b) TX bytes:100 (100.0b)


route -n


rob@rob-desktop:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0 


thanks

robi

---

### Post by unutbu on 2009-07-09
beanco, let's try to figure out if the problem is isolated to your user account in Ubuntu, or if the problem is system-wide.

How about click System>Admin>"Users and Groups", and create a new (temporary) user. Then log in as the new user and see if web browsing and evolution work there.

If it does, then it means there is some configuration file in your normal user account which is causing the problem. We can then work on finding which configuration file it is.

If web browsing and evolution do not work even for the new user, then at least we'll know the problem is system-wide.

---

### Post by beanco on 2009-07-13
i tired browsing in a temp account and in an old account already on teh computer,, neither worked.

so I guess the problem is system wide....


robi

---

### Post by unutbu on 2009-07-13
Let's review what we know:
[list]
[*] Ubuntu has a wired connection to the router.
[*] Ubuntu used to have a working internet connection.
[*] web browser doesn't work (for any user)
[*] email doesn't work (for any user)
[*] ping works
[*] dig works
[*] ktorrent works
[*] the ubuntu firewall is the default firewall
[*] no proxy server is being used
[*] kid's wifi works. 
[/list]

I guess there is only one solution: take the kid's laptop. ;)

Well, seriously now, I'm stumped. We've been at this for a week now. Maybe I should have suggested this earlier: backup your personal data and reinstall?

---

### Post by beanco on 2009-07-13
> **unutbu said:**
> Let's review what we know:
[list]
[*] Ubuntu has a wired connection to the router.
[*] Ubuntu used to have a working internet connection.
[*] web browser doesn't work (for any user)
[*] email doesn't work (for any user)
[*] ping works
[*] dig works
[*] ktorrent works
[*] the ubuntu firewall is the default firewall
[*] no proxy server is being used
[*] kid's wifi works. 
[/list]

I guess there is only one solution: take the kid's laptop. ;)

Well, seriously now, I'm stumped. We've been at this for a week now. Maybe I should have suggested this earlier: backup your personal data and reinstall?



I will be scalped if I keep using the kids laptop... they insist that it working fualtlessly and the Ubuntu box floundering is proof perfect that Mac is better than Linux....

I will just have to back up my emails and my bo9ok marks... if I could only remember how to... when I get home and then reinstall..

would this mean I hsould completely wipe out FF, evolution, etc? purge them and all that?

thanks

robi

---

### Post by unutbu on 2009-07-13
Well, before you reinstall, it may not hurt to purge the FF and evolution packages, and then reinstall them -- if you have deb packages for them. Without an internet connection, I'm not sure if you want to go through the trouble of downloading deb packages through another computer and porting it to the Ubuntu machine. Also, if you are using Feisty, I'm not sure if there are repositories available.

If you choose to just reinstall from a LiveCD, then there is no need to purge FF and evolution first. You could also use this as an opportunity to upgrade your version of Ubuntu.

I'm not sure where evolution saves email (~/.evolution?).

Firefox saves bookmarks somewhere in ~/.mozilla/firefox/*.default/. Depending on what version of Firefox you use, it could be called bookmarks.html (for Firefox before version 3.0), or places.sqlite (for FireFox version 3.0), or the bookmarkbackups directory (for FireFox version 3.5).

Good luck.

---

### Post by beanco on 2009-07-14
I have been meaning to update but never really got around to it....

so maybe this is a good time with all the problems I have been having, and all...


I might try the purge and reinstall of FF just as a test first...

but for a total reinstall, live Cd etc, I need a different computer.. the kids will be taking their laptop soon for a coule of weeks.... hm, maybe I shoudl just do it now while they are sleeping...

robi

---

### Post by beanco on 2009-07-14
drats, i was just about to finish downloading and then burn a live CD and the kids needed their macbook.... 

i will have to do this later...

robi

---

### Post by unutbu on 2009-07-14
I don't know if the macbook has the "wget" terminal program, but if it does, 
you can download large files in two (or more) pieces. For example

If you run
```

wget http://lug.mtu.edu/ubuntu-releases/jaunty/ubuntu-9.04-desktop-i386.iso
```

and have to quit, then later you can resume the dowload with the command
```

wget -c http://lug.mtu.edu/ubuntu-releases/jaunty/ubuntu-9.04-desktop-i386.iso
```

---


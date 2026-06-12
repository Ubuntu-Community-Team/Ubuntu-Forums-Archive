---
title: "Internet Is slow/non responsive."
date: 2006-03-24
forum: General Help
---

### Post by Dakaru on 2006-03-24
Ok, So my internet seems to be alot slower than what it is in windows. 

I have a Realtek ethernet onboard card, and a Dlink Router.. 

Any way to speed things up? 

Also I am using Firefox and Konqerour.

---

### Post by PhoenixP3K on 2006-03-24
You should test your internet speed with
[http://www.bandwidthplace.com/speedtest/](http://www.bandwidthplace.com/speedtest/) or [http://reviews.cnet.com/7004-7254_7-0.html](http://reviews.cnet.com/7004-7254_7-0.html)
Doing both would be good. Then as soon as you completed the test, reboot and do the same test on the other OS. If you tested on Ubuntu first switch to Windows. You get the point.

Now, after you tested, and if there is a real difference you might need to check for new drivers for the ethernet card or check firewall settings for both the PC and the router.

---

### Post by WolfJay_83 on 2006-03-24
First, you want to differentiate whether it is your internet, or browsing that is slow.
Open a terminal window
type in ```
ping www.google.ca
```
press the Ctrl key on your keyboard symultaniously with the C key to stop it.
you should have a line like...
```

9 packets transmitted, 9 received, 0% packet loss, time 8006ms
rtt min/avg/max/mdev = 21.789/22.338/22.988/0.350 ms

```
If there is packet loss or extreme lag then there may be an ethernet/network issue.

If it is a browsing issue, you could try some of the firefox tweaks at
[https://wiki.ubuntu.com/FirefoxTipsAndTricks?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxTipsAndTricks?highlight=%28firefox%29)
or upgrading to 1.5:
[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)

hope this helps

---

### Post by dcstar on 2006-03-24
[QUOTE=Dakaru]Ok, So my internet seems to be alot slower than what it is in windows. 
.....[/QUOTE]
Do a forum search for "disable IPv6".

---


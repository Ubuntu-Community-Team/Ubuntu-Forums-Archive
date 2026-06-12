---
title: "internet seems slow"
date: 2010-10-07
forum: General Help
---

### Post by boarder428 on 2010-10-07
When booted to Ubuntu and using Firefox to surf the web it seems much slower than when I'm booted to windows and using IE.  Are there any reasons why this may be?

---

### Post by xjesse on 2010-10-07
You also using Windows I'm sure you're familiar with Ccleaner, right? Well Linux has something somewhat the same minus all bells and whistles. 

```
sudo aptitude install bleachbit
```

It will clean out all the temp and junk that build up in the browsers as well as in other applications if you choose to.

If not, simply clear all cache and history specifically through Firefox. You may see a performance increase. :)

---

### Post by Ahava591 on 2010-10-07
This has been reported for months. There have been suggestions that it is related to IPv6. 

One option that has been claimed to work is this:  Type into your browser, about:config
then type in the filter box: ipv6
and disable it when it comes up.

Then try browsing. If it is still slow, it is not likely a problem with IPv6. I haven't seen any evidence that disabling IPv6 in your browser will cause you any "harm," however, please be aware that this may cause unreported breaks in Firefox.


The problem seems to be isolated to Firefox; I use it daily at home and don't really notice any problems. If you want to switch browsers, though, that is an option.

---

### Post by aisajib on 2010-10-07
I don't have such problem. In fact, internet is much much faster in my ubuntu than in windows xp and seven.

I think you should try that ipv6 trick (in the second reply).You may also clean caches.

---

### Post by markh789 on 2010-10-08
You haven't got a lot of extensions installed either? 

Many extensions are loaded with the page, and could be slowing you down.

Also, are you using a Proxy or VPN?

---

### Post by Dustin2128 on 2010-10-08
see if chromium does the trick.

---

### Post by shahan on 2010-10-08
> **boarder428 said:**
> When booted to Ubuntu and using Firefox to surf the web it seems much slower than when I'm booted to windows and using IE.  Are there any reasons why this may be?
What type of internet you are using?

---

### Post by sendblink23 on 2010-10-08
> **Dustin2128 said:**
> see if chromium does the trick.

^^^ This

---

### Post by ibtkm on 2010-10-08
you can add your limit : 
```
sudo gedit /etc/sysctl.conf
```
add this to the end of file : 
```
 ## increase TCP max buffer size setable using setsockopt()
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
 ## increase Linux autotuning TCP buffer limits
 ## min, default, and max number of bytes to use
 ## set max to at least 4MB, or higher if you use very high BDP paths
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
 ## don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
 ## recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
 ## for 10 GigE, use this, uncomment below
 ## net.core.netdev_max_backlog = 30000
 ## Turn off timestamps if you're on a gigabit or very busy network
 ## Having it off is one less thing the IP stack needs to work on
 ## net.ipv4.tcp_timestamps = 0
 ## disable tcp selective acknowledgements.
net.ipv4.tcp_sack = 0
 ##enable window scaling
net.ipv4.tcp_window_scaling = 1
```

and then use : 
```
sudo sysctl -p
```

---

### Post by boarder428 on 2010-10-09
I have cable internet, my subscribed speeds are up to 20 mbps down and 5 mbps up,  I'll try some of the other options and see if they help, I doubt it has anything to do with temp files and cache.  I'n my experience it always seems to be even slower after clearing the cache.  Not many extensions installed. No Proxy or VPN. Thanks for all the input!

EDIT:  Just disabling the ipv6 seems to have made a big difference,  I noticed that it comes disabled in Linux Mint. (Which may explain why mint seemed faster than Ubuntu)  Think i'll try that for a few days and then maybey try ibtkm's suggestion aswell!

---


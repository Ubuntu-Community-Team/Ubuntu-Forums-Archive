---
title: "internet very slow on ubuntu 10.10 64-bit"
date: 2011-03-20
forum: General Help
---

### Post by mapplex on 2011-03-20
Hey Guys, 
I got ubuntu 10.10 64 bit and I really do like it. My only problem is that the internet is very slow. It takes ages to load a page. i got Ubuntu as my second system on my computer and the internet works fine on my windows 7 partition. 
I already disabled the ipv6  and my DNS. I dont think the problem comes from firefox either. 
I read so many threads already but i didnt get any solution that worked for me. 
do I need a ping test for u to help me with my problem and if yes how do i do it? 
I would really appreciate any help, thanks Mapplex

---

### Post by Templaillo Ahi on 2011-03-20
Hi, I'm new on this forum though I've been using Ubuntu and some other distros for a long time, mostly for testing purposes. I have the same problem as mapplex and some other users as I've seen through the forum. However, none of the other solutions worked for me (disabling ipv6, changing DNS, etc...).

I can tell it's not a hardware issue, as internet works perfectly on my Windows partition (XP 32-bit), with the full speed my ISP gives me (3Mbps). Also, it's not a browser problem, as I have the same slow speed when downloading from repositories via apt-get, or downloading with wget. It slows down to a mere 30Kbps most of the time. The fastest it got was over ~1Mbps. Seeing this, I assume it's got to be either a driver or a software problem of some sort.

My machine is a Dell Vostro 1700. I connect through an integrated Intel PRO/Wireless 3945, which uses the module iwl3945 that came with Ubuntu. I haven't tried wired connection, though.

Any help solving the problem would be greatly appreciated.

Thanks in advance.

---

### Post by ravi89 on 2011-03-20
Hi #Mapplex & #Templaillo,
     I am not sure the reason for the slowness but simply guessing it out, Had you enabled the **Download all updates in the Background** option under Update manager settings if so disable it. Try installing the "Net speed" like small applets to monitor the real download & upload speed since some #chat,#mail-clients,#File Synchronization(Dropbox,Ubuntu One),#Torrent applications etc., consume half of the Bandwidth.

---

### Post by blueridgedog on 2011-03-20
How about some numbers if you have a dual boot?

Go here:

[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

and run a test in each OS, with the same browser, using the same location and report back the numbers you get.

---

### Post by Templaillo Ahi on 2011-03-21
@ravi89: No, I've got it set to notify me when there's an update. As I said, apt-get also downloads really slowly. I also have Ubuntu One disabled, no chat, no torrent... I even tried disabling ufw, just in case. I really don't think there's something else downloading in the background.

@blueridgedog: Did that already like 20 times. On Windows I get 2900~3000Kbps download and ~260Kbps upload, which is roughly what I have contracted with my ISP. On Ubuntu I get at most ~800Kbps down and ~260Kbps up, normally getting 400~600Kbps down. Right now I gave it a try and got 496Kbps down and 254Kbps up.

Thanks for the suggestions so far.

---

### Post by blueridgedog on 2011-03-21
Try a 32 bit LiveCD and test the speed.

---

### Post by peely on 2011-03-21
Have you checked the MTU size on your router is correct for your broadband connection?

The MTU for a given interface can also be set in /etc/network/interfaces.

---

### Post by pqwoerituytrueiwoq on 2011-03-21
Lossy connection is possible due to a driver issue
ping your gateway address
to find it out use the [route](http://www.cyberciti.biz/faq/how-to-find-gateway-ip-address/#post-780) command
then ping it a few times
ping $ADDRESS -c 15
example
```
me@linux-laptop:~$ ping 10.0.0.1 -c 15
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=64 time=1.17 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=0.836 ms
64 bytes from 10.0.0.1: icmp_seq=3 ttl=64 time=0.841 ms
64 bytes from 10.0.0.1: icmp_seq=4 ttl=64 time=1.03 ms
64 bytes from 10.0.0.1: icmp_seq=5 ttl=64 time=0.827 ms
64 bytes from 10.0.0.1: icmp_seq=6 ttl=64 time=0.828 ms
64 bytes from 10.0.0.1: icmp_seq=7 ttl=64 time=0.839 ms
64 bytes from 10.0.0.1: icmp_seq=8 ttl=64 time=0.812 ms
64 bytes from 10.0.0.1: icmp_seq=9 ttl=64 time=0.838 ms
64 bytes from 10.0.0.1: icmp_seq=10 ttl=64 time=0.831 ms
64 bytes from 10.0.0.1: icmp_seq=11 ttl=64 time=1.35 ms
64 bytes from 10.0.0.1: icmp_seq=12 ttl=64 time=0.850 ms
64 bytes from 10.0.0.1: icmp_seq=13 ttl=64 time=0.797 ms
64 bytes from 10.0.0.1: icmp_seq=14 ttl=64 time=1.17 ms
64 bytes from 10.0.0.1: icmp_seq=15 ttl=64 time=0.815 ms

--- 10.0.0.1 ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 14004ms
rtt min/avg/max/mdev = 0.797/0.923/1.356/0.172 ms
me@linux-laptop:~$
```

---

### Post by Templaillo Ahi on 2011-03-21
@blueridgedog: Tried it, no dice. Tested it on two different speed test sites, three consecutive times each, and got: 943/237, 752/209 and 1030/241 on the first one; 570/240, 590/260 and 730/240 on the second. (All in Kbps) Seems pretty random.

@peely: MTU is 1500 on both the router and my wireless config. Already checked it works following another thread's instructions.

@pqwoerituytrueiwoq(whoa): I'm guessing that's where the problem comes from, which is strange since I had CrunchBang installed previous to Ubuntu and it worked fine, with the same (AFAIK) driver. Anyway, here's the ping results, which really look abnormal to me:

```
ubuntu@ubuntu:~$ ping 192.168.0.1 -c 15
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=2 ttl=254 time=105 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=254 time=10.2 ms
64 bytes from 192.168.0.1: icmp_req=4 ttl=254 time=18.3 ms
64 bytes from 192.168.0.1: icmp_req=5 ttl=254 time=153 ms
64 bytes from 192.168.0.1: icmp_req=6 ttl=254 time=104 ms
64 bytes from 192.168.0.1: icmp_req=7 ttl=254 time=8.02 ms
64 bytes from 192.168.0.1: icmp_req=8 ttl=254 time=24.7 ms
64 bytes from 192.168.0.1: icmp_req=9 ttl=254 time=111 ms
64 bytes from 192.168.0.1: icmp_req=10 ttl=254 time=2.03 ms
64 bytes from 192.168.0.1: icmp_req=11 ttl=254 time=13.0 ms
64 bytes from 192.168.0.1: icmp_req=12 ttl=254 time=17.0 ms
64 bytes from 192.168.0.1: icmp_req=13 ttl=254 time=10.1 ms
64 bytes from 192.168.0.1: icmp_req=13 ttl=254 time=161 ms (DUP!)
64 bytes from 192.168.0.1: icmp_req=15 ttl=254 time=7.34 ms

--- 192.168.0.1 ping statistics ---
15 packets transmitted, 13 received, +1 duplicates, 13% packet loss, time 14027ms
rtt min/avg/max/mdev = 2.039/53.379/161.467/57.258 ms

```

---

### Post by blueridgedog on 2011-03-21
Would be curious to compare the output of "ifconfig" under Linux to "ipconfig /all" under windows.

Do each use an ip or DHCP?

---

### Post by Templaillo Ahi on 2011-03-21
They both use the same IPs and DNS, they're manually set. However, I'm on DHCP on the 32-bit Live CD right now and it makes no difference whatsoever.

BTW, mapplex, if you're out there I'd like to hear if anything worked for you. I almost feel like I hijacked your thread, man. :oops:


EDIT: I just tried wired connection. Works like a charm, I get my top speed on tests and pings to the router look normal. Currently I'm blaming it on the wireless driver.

```
ubuntu@ubuntu:~$ ping 192.168.0.1 -c 15
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=254 time=0.553 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=254 time=0.563 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=254 time=0.623 ms
64 bytes from 192.168.0.1: icmp_req=4 ttl=254 time=0.577 ms
64 bytes from 192.168.0.1: icmp_req=5 ttl=254 time=0.650 ms
64 bytes from 192.168.0.1: icmp_req=6 ttl=254 time=0.739 ms
64 bytes from 192.168.0.1: icmp_req=7 ttl=254 time=0.656 ms
64 bytes from 192.168.0.1: icmp_req=8 ttl=254 time=0.652 ms
64 bytes from 192.168.0.1: icmp_req=9 ttl=254 time=0.672 ms
64 bytes from 192.168.0.1: icmp_req=10 ttl=254 time=0.676 ms
64 bytes from 192.168.0.1: icmp_req=11 ttl=254 time=0.700 ms
64 bytes from 192.168.0.1: icmp_req=12 ttl=254 time=0.673 ms
64 bytes from 192.168.0.1: icmp_req=13 ttl=254 time=0.675 ms
64 bytes from 192.168.0.1: icmp_req=14 ttl=254 time=0.602 ms
64 bytes from 192.168.0.1: icmp_req=15 ttl=254 time=0.677 ms

--- 192.168.0.1 ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 13996ms
rtt min/avg/max/mdev = 0.553/0.645/0.739/0.060 ms

```

---

### Post by jdeslaur on 2011-03-21
Just adding to the collective knowledge base, i had some terrible network performance when I had an ubuntu virtualbox with the network settings set to NAT.  I changed it to Bridged and it started working fine.

---

### Post by blueridgedog on 2011-03-21
> **Templaillo Ahi said:**
> EDIT: I just tried wired connection. Works like a charm

I missed that you were on wifi.  Now I feel old.  I had similar issues with a few wireless cards in my PC and ended up buying three to test until I found one that worked.  I ended up with a Netgear RangeMax WPN311 Wireless Network PCI Adapter from ebay for $9.00 that works great.

---

### Post by theteju on 2011-03-21
> **peely said:**
> Have you checked the MTU size on your router is correct for your broadband connection?

The MTU for a given interface can also be set in /etc/network/interfaces.

Unfortunately I have started similar thread on the forum.
[http://ubuntuforums.org/showthread.php?t=1711164](http://ubuntuforums.org/showthread.php?t=1711164)

I am facing slow internet issue on my 10.04 but just now I noticed from my schools network, the speed is perfect on my ubuntu and my XP machine. So is there something I need to set on my router? I never heard of MTU size.

Please show me some direction.

the bandwidth test on my router is exceptionally awesome.. it shows, 10.34 mbps download and .75 mbps upload speed. I can not complain my ISP.

please help. thanks.

---

### Post by Templaillo Ahi on 2011-03-22
Hey guys, just a quick bump. I've been searching a bit and found that the iwl3945 driver has got some issues that remain unfixed. There were some fixes like installing the deprecated ipw3945 driver or older versions of iwl3945 but I haven't got time to test them yet. I'll try that or maybe using ndiswrapper to see if there's a difference and post back the results when I have some time.

@blueridgedog: I'd prefer solving the problem with my current adapter, specially since I know it worked fine on older distros. Besides, budget's pretty tight these days ;) . Anyway, thanks for the suggestion. If I really had no other choice, though, I think I'd be going back to Windows for a while (much to my dislike).

@theteju: Check this thread and see if it helps.
[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)

---

### Post by Templaillo Ahi on 2011-03-27
It's me again, guys. Just wanted to tell you that I got it fixed. It was the driver after all. I updated to 2.6-35-28 and [followed the instructions here.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265/comments/334") Now it's working like it should and I'm a happy person :D

The bug described in that link is specifically for Intel 3945abg (my adapter). I don't know what mapplex's is, but I'd give it a try anyway. Good luck to anyone with the same problem and thanks to all the people who tried to help.

---


---
title: "Installing Router"
date: 2012-01-11
forum: General Help
---

### Post by Torbjorn S.D. on 2012-01-11
Hello!

I have difficulties making my router work. When I try to ping, I don't get any answer. On the other hand there is something in the instructions that I don't really understand and that might be the reason I can't install my router.

The manual says this:

Step1. Launch a web browser on your client PC connected to ZSR0104C SERIES. Then point the Web browser to [http://192.168.1.1](http://192.168.1.1) ([http://192.168.1.1](http://192.168.1.1) is ZSR0104C SERIES default IP address.) If the router IP address was configured with different IP address, use the configured IP address instead of 192.168.1.1. Please make sure your computer IP address is located in the same subnet of the router IP address.


My question is this: What does the last sentence mean and how do I go about in order to make sure that I do what it says? How do I do to make sure that my computer IP address is located in the same subnet of the router IP address?

Best regards and thanks in advance,

---

### Post by collisionystm on 2012-01-11
> **Torbjorn S.D. said:**
> Hello!

I have difficulties making my router work. When I try to ping, I don't get any answer. On the other hand there is something in the instructions that I don't really understand and that might be the reason I can't install my router.

The manual says this:

Step1. Launch a web browser on your client PC connected to ZSR0104C SERIES. Then point the Web browser to [http://192.168.1.1](http://192.168.1.1) ([http://192.168.1.1](http://192.168.1.1) is ZSR0104C SERIES default IP address.) If the router IP address was configured with different IP address, use the configured IP address instead of 192.168.1.1. Please make sure your computer IP address is located in the same subnet of the router IP address.


My question is this: What does the last sentence mean and how do I go about in order to make sure that I do what it says? How do I do to make sure that my computer IP address is located in the same subnet of the router IP address?

Best regards and thanks in advance,


manually set your computer IP to 

192.168.1.10

mask 255.255.255.0


then you can reach the router to set it up. When done, put your network card back to DHCP

---

### Post by Drenriza on 2012-01-11
> Step1. Launch a web browser on your client PC connected to ZSR0104C SERIES. Then point the Web browser to [http://192.168.1.1](http://192.168.1.1) ([http://192.168.1.1](http://192.168.1.1) is ZSR0104C SERIES default IP address.) If the router IP address was configured with different IP address, use the configured IP address instead of 192.168.1.1. Please make sure your computer IP address is located in the same subnet of the router IP address.

Think of it this way.

An ip address is a house number on a street.
And a subnet mask is the name of the street.

What is tells you. Is that, for you to be able to connect to your router. You need to know where it is located. In this case its located at 192.168.1.1 255.255.255.0.

So as suggested above. Change your ip address and subnet mask.
From a command line write
```
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
```

once you have configured your router, do a 
```
sudo ifconfig eth0 down
```
```
sudo ifconfig eth0 up
```

To get a dhcp address from the router.

Hope it helps.

---

### Post by mbuell on 2012-01-11
The previous set of instructions are pretty thorough - and should get you where you need to be. 

I have a question, though - have you tried entering 192.168.1.1 in the navigation bar of your browser? What happens? 

When you get to a web page that essentially says something like "Welcome to your router" with a login screen, you know you are where you need to be. The default password should be in your manual. If you don't have a manual, or someone else has previously set the password, you may have to find the switch to "restore factory settings". Usually a tiny button hidden on the back. 

Unless your computer was set up as part of a corporate network, I think it would be very unusual for you to have a subnet mask other than 255.255.255.0.

---

### Post by gsgleason on 2012-01-11
Make sure your pc is connected to one of the 4 switch ports and not the WAN port.  Make sure you have link lighs on both sides.

Verify you're getting an IP address with 'ifconfig' from a terminal.

---

### Post by Torbjorn S.D. on 2012-01-13
> **mbuell said:**
> The previous set of instructions are pretty thorough - and should get you where you need to be. 

I have a question, though - have you tried entering 192.168.1.1 in the navigation bar of your browser? What happens? 

This is what happens:



This webpage is not available
Chromium's connection attempt to 192.168.1.1 was rejected. The website may be down, or your network may not be properly configured.




Unable to connect
Firefox can't establish a connection to the server at 192.168.1.1.

---

### Post by Learning Linux 2011 on 2012-01-13
Is your computer physically plugged into the router (i.e. not wirelessly)?  Have you ever configured the router?  Has the router *ever* worked?

Open a terminal and type:  ```
 ping 192.168.1.1 
```What happens?

Is there a possibility that your router's IP address is *not *192.168.1.1?

---

### Post by spacecheck on 2012-01-13
As mentioned in post #5 "make sure your pc is connected to one of the 4 switch ports and not the WAN port." The WAN port is often marked "upload".

Good luck!

---

### Post by Torbjorn S.D. on 2012-01-13
> **gsgleason said:**
> Make sure your pc is connected to one of the 4 switch ports and not the WAN port.  Make sure you have link lighs on both sides.

Verify you're getting an IP address with 'ifconfig' from a terminal.




torbjorn@torbjorn-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:8a:a4:41  
          inet addr:84.55.83.77  Bcast:84.55.83.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe8a:a441/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:483940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1081189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80335392 (80.3 MB)  TX bytes:1465734594 (1.4 GB)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:464267 (464.2 KB)  TX bytes:464267 (464.2 KB)




torbjorn@torbjorn-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:8a:a4:41  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe8a:a441/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:485202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1081389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80411112 (80.4 MB)  TX bytes:1465754165 (1.4 GB)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:473035 (473.0 KB)  TX bytes:473035 (473.0 KB)

---

### Post by Torbjorn S.D. on 2012-01-13
> **Learning Linux 2011 said:**
> Is your computer physically plugged into the router (i.e. not wirelessly)?  Have you ever configured the router?  Has the router *ever* worked?

Open a terminal and type:  ```
 ping 192.168.1.1 
```What happens?

Is there a possibility that your router's IP address is *not *192.168.1.1?



When I change the IP-address in my computer to the IP-address of the router, i.e. to 192.168.1.1, this happens:


torbjorn@torbjorn-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.022 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.017 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.011 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.029 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.021 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.019 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.016 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.014 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.018 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.019 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=0.018 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=0.015 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=0.016 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=0.019 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=0.012 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=0.009 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=0.016 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=0.012 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=0.010 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=0.009 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=0.014 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=0.020 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=0.017 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=0.016 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=0.030 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=64 time=0.014 ms
64 bytes from 192.168.1.1: icmp_seq=27 ttl=64 time=0.021 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=64 time=0.024 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=64 time=0.021 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=64 time=0.019 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=64 time=0.016 ms




When I use my old IP-address (the one I got from my ISP) then this happens:

torbjorn@torbjorn-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 84.55.83.77 icmp_seq=4 Destination Host Unreachable
From 84.55.83.77 icmp_seq=5 Destination Host Unreachable
From 84.55.83.77 icmp_seq=6 Destination Host Unreachable
From 84.55.83.77 icmp_seq=7 Destination Host Unreachable
From 84.55.83.77 icmp_seq=9 Destination Host Unreachable
From 84.55.83.77 icmp_seq=10 Destination Host Unreachable
From 84.55.83.77 icmp_seq=11 Destination Host Unreachable
From 84.55.83.77 icmp_seq=13 Destination Host Unreachable
From 84.55.83.77 icmp_seq=14 Destination Host Unreachable
From 84.55.83.77 icmp_seq=15 Destination Host Unreachable
From 84.55.83.77 icmp_seq=16 Destination Host Unreachable
From 84.55.83.77 icmp_seq=17 Destination Host Unreachable
From 84.55.83.77 icmp_seq=18 Destination Host Unreachable
From 84.55.83.77 icmp_seq=20 Destination Host Unreachable
From 84.55.83.77 icmp_seq=21 Destination Host Unreachable
From 84.55.83.77 icmp_seq=22 Destination Host Unreachable
From 84.55.83.77 icmp_seq=23 Destination Host Unreachable
From 84.55.83.77 icmp_seq=24 Destination Host Unreachable
From 84.55.83.77 icmp_seq=25 Destination Host Unreachable



Because of this, I believe that the IP-address is the correct one. Also, this is the IP-address stated in the manual. The router is a Zonet ZSR0104CP. (It says so on the machine.)

A user manual for the ZSR0104C series can be downloaded from this address:

[http://www.info.zonetusa.net/ProductDownload/ZSR0104CP%20Manual.pdf](http://www.info.zonetusa.net/ProductDownload/ZSR0104CP%20Manual.pdf)

Thanks for all the help this far. I feel I am slowly making progress and might be able to get it all working in a few days.

---

### Post by Torbjorn S.D. on 2012-01-13
I have clicked on the "Reload Button" in order to get the  "Factory Default Settings". It still doesn't work. My main problem is that I can't configure the router.

---

### Post by Torbjorn S.D. on 2012-01-13
> **mbuell said:**
> 
If you don't have a manual, or someone else has previously set the password, you may have to find the switch to "restore factory settings". Usually a tiny button hidden on the back. 


I've pushed the button you've described. I want to point out that I can't find my copy of the manual and that I am using a manual that I downloaded from the Internet. The site I downloaded it from is the manufacturer's site. Here's a deep link: 

[http://www.info.zonetusa.net/ProductDownload/ZSR0104CP%20Manual.pdf](http://www.info.zonetusa.net/ProductDownload/ZSR0104CP%20Manual.pdf)


> **mbuell said:**
> 
Unless your computer was set up as part of a corporate network, I think it would be very unusual for you to have a subnet mask other than 255.255.255.0.


I am a home user and I am not part of a corporate network. The subnet mask that I've been given by my ISP is 255.255.255.0.

---

### Post by spacecheck on 2012-01-13
> **Torbjorn S.D. said:**
> I have clicked on the "Reload Button" in order to get the  "Factory Default Settings". It still doesn't work. My main problem is that I can't configure the router.
Well, now that you have reset the router, and can get really fast pings from it at the new factory address of 192.168.1.1 all you need to do is put that address into the web browser (with java script enabled) and enter the standard password (look in the manual) and begin setting up the router according to the ISP specifications.

Try it and see what happens.

Good luck!

---

### Post by Torbjorn S.D. on 2012-01-13
> **Learning Linux 2011 said:**
> Is your computer physically plugged into the router (i.e. not wirelessly)?  Have you ever configured the router?  Has the router *ever* worked?
[/I]192.168.1.1?


My computer is physically plugged into the router. It is not wirelessly plugged into it.

I have never configured the router.

The router has never worked.

I have never tried the router out until now. I bought it a year ago or several years ago but got very depressed and didn't try it out until now, so the "ONE (1) Year Limited Manufacturer Warranty" isn't valid anymore.

---

### Post by spacecheck on 2012-01-13
> **Torbjorn S.D. said:**
> My computer is physically plugged into the router. It is not wirelessly plugged into it.

I have never configured the router.

The router has never worked.

I have never tried the router out until now. I bought it a year ago or several years ago but got very depressed and didn't try it out until now, so the "ONE (1) Year Limited Manufacturer Warranty" isn't valid anymore.

Cheer up, looks like it is working now, since it answers your ping!

Now all you should need to do is enter the data given you by your ISP (probably Ownit Broadband) into your router, including Ownit's DNS addresses and perhaps some account data & account password and you should be all set. Except, now that you reset the router, you'll surely want to change the router's username and password to one that is not the standard, selecting a long secure password using a mixture of several upper & lower case letters interspersed with several numbers.

If it works, you should get access and can go ahead and use the thread tools to mark this thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

If not, you can report back for further assistance.

Good luck!

---

### Post by spacecheck on 2012-01-13
You see, the IP address you get from the ISP gets assigned to the router as the external network address.

Then, you either use the standard internal address (192.168.1.1) as the local subnet gateway address, or you change it in the router to another address (for example 192.168.10.1).

If you don't change it, you can set the computer to automatically draw an address per DHCP and the router should assign the PC an address somewhere within the 192.168.**[COLOR=Red]1[/COLOR]**.xxx (xxx=2-254) address range. Or you can manually set the address (192.168.**[COLOR=Red]1[/COLOR]**.10, for example), netmask (255.255.255.0), and gateway (192.168.1.1)

If you change the router's internal address to 192.168.**[COLOR=Red]10[/COLOR]**.1 (for example), the PC should be set to pull an address per DHCP from that address and the router should assign the PC an address somewhere within the  192.168.10.xxx (xxx=2-254) address range. Or you can manually set the  address (192.168.**[COLOR=Red]10[/COLOR]**.10, for example), netmask (255.255.255.0), and  gateway (192.168.**[COLOR=Red]10[/COLOR]**.1).

You cannot use the ISP-provided IP-address for both router *AND* PC. You assign it to the router and then assign a local subnet to operate hidden behind the router.

You ask the PC to connect to the web, the PC passes the request to the router, the router transcribes it (NAT -network address translation) to suit the external address and sends the translated request on through to the ISP, which acts upon it locally (ISP's intranet) or forwards it on into the Internet. Responses are returned in a reverse manner.

Hopefully everything will work out well.

Good luck!

---

### Post by mbuell on 2012-01-14
> **Torbjorn S.D. said:**
> I've pushed the button you've described. I want to point out that I can't find my copy of the manual and that I am using a manual that I downloaded from the Internet. The site I downloaded it from is the manufacturer's site. Here's a deep link: 

[http://www.info.zonetusa.net/ProductDownload/ZSR0104CP%20Manual.pdf](http://www.info.zonetusa.net/ProductDownload/ZSR0104CP%20Manual.pdf)




I am a home user and I am not part of a corporate network. The subnet mask that I've been given by my ISP is 255.255.255.0.

I went through all the replies - and I'm not sure we are there yet. So I would like to ask you to do another small exercise, because we are on the right track. But first - I want to clear something up - the subnet mask that your IP gives you and the one you use on your side of the router are two different things. The same will be true of your IP addresses. Once you get the router working - it will assign all IP addresses on YOUR side of the router - and it will use it's own subnet mask for this task. Your IP will give your router an IP address for OUTSIDE. From inside - where you are, the router will always be 192.168.1.1. 

On to the exercise. It looks like you found the proper manual - good on ya! I did not see where you pinged the router and got a response - but I see you reset it. Ok. Now I think you should go to the manual you found and find Chapter 2 (page is labeled page #5 at the bottom). You may want to print out this thread to continue. I think you should disconnect all machines from your internet provider and then start following the setup procedure that starts on page #6. You will reset the router again, but this won't hurt anything, so go ahead and do it. You will connect your machine to the router. Do NOT connect anything to anything else. Just your computer and the router. This much should take you about 10 minutes or less. If step #4 on page #7 fails repeatedly, then the router is bad. 

But I think you will get to the admin screen. When you successfully complete the connection to the admin screen, log out and just turn the router off. 

The next step is not Chapter 3 - Install. You might do all that process, only to still find you can not connect to the internet - even if you do everything right in the setup. This can happen because your of your IP's modem settings. Obviously, I do not know anything about those modem settings - but I have seen this happen. Sometimes you have to reset the modem to act as a "bridge" - which only means that it will pass the signal directly through without trying to do anything. Some modems do some of the basic router actions - assigning you an internal IP address, that sort of thing. And we usually don't want two dumb machines trying to act smart. It might be a good idea to call your IP BEFORE you get started with Chapter 3 to discuss this process with them. Tell them what you are doing - and ask if there is anything you need to do with your modem to make this work. 

Now pick up your manual at Chapter 3 - installation. Now you plug in your IP connection (probably coming out of a modem of some sort). Plug it into the router WAN port, and your computer into port 1, 2, 3, or 4 just like you did for the previous test. 

You will login to the router and run through the wizard to set the router up. 

Do not forget to change the default password. I prefer a properly long and randomized one - and write it down somewhere. Just don't store the written down version someplace where anybody else would look to find it. Personally, I have a super-encrypted file I use to store all my passwords. It gets copied to my backups. Since it is encrypted, I don't worry - and I can find it easily. 

Maybe by the time I've written this long post, you will have found the answer. But I hope it helps.

---

### Post by spacecheck on 2012-01-14
In post 9 and 10 you can see where the IP of *the computer* was changed to 192.168.1.1 
[http://ubuntuforums.org/showpost.php?p=11609026&postcount=9](http://ubuntuforums.org/showpost.php?p=11609026&postcount=9)
> I did not see where you pinged the router and got a response
You can see that he actually changed the PC address to what *should be* the router address, so he is basically only pinging the local host, but NOT the router. When he tries the old address, he is no longer on that subnet, so he will get no response from anywhere.

I did not recognize earlier, before my earlier post, that he had mistakenly given his PC the router address.

Since he already used the reset button to reset the router to the default address 198.168.1.1, all he should now need do on the PC  is either remove the assigned address and set it to automatically connect per DHCP, or set the PC address to 192.168.1.2 (or three, or four, etc.) and the net mask to 255.255.255.0.

He should then be able to reach the router's webadmin page (if his cable is not inserted into the upload/WAN socket, and the device is plugged into the power supply and is functional).

Then he could begin entering ISP (and account) data,  for his router to begin acting as a DHCP client to get external IP address and Internet access. After this, the router need only be set as the default gateway. Or, once the router is configured, reset the PC as an automatic DHCP client.

Be sure to correct me, if I have missed something else.

Good luck!

---

### Post by mbuell on 2012-01-15
@ spacecheck - nope, you didn't miss anything. What you picked up - he pinged his own box - was also what I picked up. 

What you have suggested to get up and going is almost exactly what I just posted - so I feel validated. The only extra thing I did was take it back a step to Hardware & Networking 101 - cut out all the variables and move forward one step at a time. 

The manual he linked to matches the model he gave us, and the instruction set there is ok. Not super great, but pretty good. 

:)

---

### Post by spacecheck on 2012-01-16
@mbuell - > nope, you didn't miss anything. Great ! Was a bit unsure, having not immediately clicked to his having pinged his own box, instead of his router, but I was also too lazy to examine his handbook for further clarity (ooops! some self-critique has leaked out, gotta seal the hole quick!).

Thanks for the update. The OP has not taken any opportunity to respond, despite traces of online activity, so perhaps the problem has been resolved.

Have fun!

---

### Post by Torbjorn S.D. on 2012-01-17
> **spacecheck said:**
> @mbuell

Thanks for the update. The OP has not taken any opportunity to respond, despite traces of online activity, so perhaps the problem has been resolved.



I have not solved the problem. I will write more responds today.

---

### Post by mbuell on 2012-01-20
> **Torbjorn S.D. said:**
> I have not solved the problem. I will write more responds today.

Torbjorn - we had good luck with the first exercise I gave you. Let's go for the second one, too. Can't tell for sure from here - since I do not see what you see - but I think if you have not already done the 2nd exercise I talked about - that it will get you closer to resolving the issue. 

Regards;

hiero

---

### Post by stevennlv on 2012-01-20
Just two cents to add here:

Most of these guys helping obviously know a lot more than I do but, 192.168.1.xxx is no longer always the login address for new routers any more. I haven't read your manual but, I got a new router last year. I tried the old 192.168.1.1 address in my browser and the connection was rejected. When I checked the manual I found that the login address was actually 

[http://routerlogin.net/start.htm](http://routerlogin.net/start.htm)

, maybe yours has an address like that?

---

### Post by lisati on 2012-01-20
Agreed, sometimes the details vary. My current modem, like its immediate predecessor from the same manufacturer, uses 192.168.1.254 to access its browser-based configuration page, but the name on the network is different.

---


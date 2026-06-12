---
title: "Wireless says I am connected but I'm not!"
date: 2010-01-10
forum: General Help
---

### Post by DougieFresh4U on 2010-01-10
I am running Xubuntu Karmic. I used the wireless adapter I am trying to use now, to update/upgrade from Hardy/Intrepid/Jaunt and finally made ut to Karmic, using this wireless adapter. Now when i boot machine, the wireless bars are showing I am connected.
Please any help would be great. Need more info, please let me know.
Thanks

---

### Post by michy99 on 2010-01-10
It may be that you are connected to the router but there is a problem with the modem. Does a wired connection work?

---

### Post by DougieFresh4U on 2010-01-10
Wired doesn't show up but when I plug it in, I see the little light blinking in the back of machine.
The same 'wired' connection works quite well on my iMac, as that is what I am using.
Some times the wireless has 'connected' for like one or two minutes, but rarely.

---

### Post by DougieFresh4U on 2010-01-11
Please, any one have any suggestions?
When I check 'edit connections' it says connected 'now' but I am getting no activity, I don't understand this!

---

### Post by pedro_orange on 2010-01-11
> **DougieFresh4U said:**
> I am running Xubuntu Karmic. I used the wireless adapter I am trying to use now, to update/upgrade from Hardy/Intrepid/Jaunt and finally made ut to Karmic, using this wireless adapter. Now when i boot machine, the wireless bars are showing I am connected.
Please any help would be great. Need more info, please let me know.
Thanks

Lol. Sorry but you've not actually described your problem at all or what you've done to attempt to remedy it. 
I will hazard a guess and presume network-manager is telling you that you're connected to your wireless access point but are unable to access the Internet? 

First of all, do you have an IP Address?

> ifconfig -a

If you do; great. It's probably the router. If you don't - you need one. 

> iwconfig

Can help you with connecting to the wireless networks.

When you're checking your wired connection, check it from the operating system. Unless the hardware is broken, then the blinking light on the port itself isn't really going to tell you anything. Again ifconfig can help when you've got the ethernet cable plugged in. Ensure that eth0 is enabled in network-manager. 

Hope this helps.

---

### Post by DougieFresh4U on 2010-01-11
Sorry if I have not explained my problem clearly.
Yes I have an 'address' and I can use the 'wired' cable on my iMac with no problem. the wireless is showing as 'connected' in the upper right corner of my desktop, as the bars fluctuate from 10% to 100% connection, but I can not access any thing on the internet.
Also, where do I find network manager in Xubuntu Karmic as I have looked and can't find it

---

### Post by muteXe on 2010-01-11
What kind of encryption do you have on your router for wireless?  Have you tried switching that off temporarily and seeing if it's an encryption issue?

---

### Post by DougieFresh4U on 2010-01-11
I have 'WPA & WPA2 Personal' and turning that off didn't work.
Every I have checked says I am connected . Under 'edit connections' it says I am connected 'now'

Edit: just checked 'Edit connections' and under 'Last Used' it says '5 minuted ago'
in spite of all it is saying, I have not been able to 'surf' the internet at all.

---

### Post by bkratz on 2010-01-11
Can you ping a website by name? If not can you ping one by IP address?

---

### Post by DougieFresh4U on 2010-01-11
> **bkratz said:**
> Can you ping a website by name? If not can you ping one by IP address?

Can you  help me on that as i am not sure how?
Thanks for all the replies.

---

### Post by bkratz on 2010-01-11
> **DougieFresh4U said:**
> Can you  help me on that as i am not sure how?
Thanks for all the replies.

Look at the first section of the following ( you will need to use the terminal for what is proposed)

[http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html#more-99](http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html#more-99)

---

### Post by DougieFresh4U on 2010-01-11
> **bkratz said:**
> Look at the first section of the following ( you will need to use the terminal for what is proposed)

[http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html#more-99](http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html#more-99)
Thanks. i am trying a live-cd at the moment.
also, i used the alternate install cd if that makes a difference.

---

### Post by Monotoko on 2010-01-11
To ping, you will need to use the terminal

To ping an address:

```
ping www.google.co.uk
```

to ping an IP:

```
ping 216.239.59.99
```

Hope this helps

---

### Post by DougieFresh4U on 2010-01-11
Using live-cd now and it is working excellent.
So I shall attempt a reinstall.
Thanks to all who replied.
as much as I would like to solve this issue, I think a 'fresh' install would work better, besides I do not care for Xubuntu to much as this is Ubuntu Karmic cd

EDIT: going to mark 'solved' so every one can get on with  helping members who really need the help
Thanks

---


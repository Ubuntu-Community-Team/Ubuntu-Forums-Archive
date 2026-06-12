---
title: "Should I swich back to Windows for better networking"
date: 2010-09-21
forum: General Help
---

### Post by skew on 2010-09-21
I have a dial-up 56k (no broadband available here) modem connection via ppp0 and a home LAN connection to two other systems through a DD-WRT set up router using eth0 wired and eth1 wireless. ppp and eth don't work to together. Something about DNS and resolv.conf resetting the DNS. I don't understand why it does this or how that system works or why it can't be worked around, but apparently it can't.   I can dial into the Internet but if i was connected to the LAN before doing so I can't connect to any sites. The reverse with the LAN is also true. I have to shut down one or the other interface for the other interface to function correctly.  
 
   I've asked for help in these forums, specifically networking several times but seem to have hit the back hole of help when it come to issues for which their isn't a solution. I assume they think that if they ignore me I'll just go away, so I've moved to this forum hoping for better results.

 In regards to my title question; if I switch to Window7(ugh!) or XP(groan!) will I be able to do these things. I'm sure there is someone with a dual boot system who can enlighten me to this. 

   I've been using Ubuntu since Dapper and I did years ago have an Ethernet and ppp0 dial-up connection working together with ICS. I don't understand why doesn't it work now?

   OF COURSE if you have solution to my problem so it will work with my Ubuntu Lucid systems I'd be forever in your debit! I really don't want to return to using windows. Would you?

Thanks

---

### Post by Mark Phelps on 2010-09-21
Your reference to DD-WRT is likely a major part of your NOT getting help in these forums. Anytime you take a commercial piece of equipment and you replace the software with something obtained from a third-party, you are then faced with having to rely on that third-party for support.

Did you check the DD-WRT forums to see if they can help you?

As to getting better help in THIS forum -- maybe.  It probably gets wider readership than the Networking forum, but that doesn't mean that you'll get better support.

---

### Post by HermanAB on 2010-09-21
Howdy, if your DNS settings keep getting changed, disable your dhclient program, or configure the dhcp server properly.

If you cannot connect to other sites, then your default route is probably not set correctly.

Go to tldp.org and read the routing howtos.

---

### Post by endotherm on 2010-09-21
based on your problem description, no I would not assume that windows would fare any better, but it may be worth a shot if you really want to. 

I wonder if the problem doesn't have somthing to do with avahi.

---

### Post by skew on 2010-09-21
> **HermanAB said:**
> Howdy, if your DNS settings keep getting changed, disable your dhclient program, or configure the dhcp server properly.

If you cannot connect to other sites, then your default route is probably not set correctly.

Go to tldp.org and read the routing howtos.

Thanks for replying. How do you disable the dhclient? Where can I find info on configuring the dchp that a noob like me would understand? In the mean time I'll check your link thanks!

---

### Post by Slim Odds on 2010-09-21
> **skew said:**
> Thanks for replying. How do you disable the dhclient? Where can I find info on configuring the dchp that a noob like me would understand? In the mean time I'll check your link thanks!

You might try using a static IP address for your LAN.

It's been many years.... but before I was able to get DSL I used a modem to connect via dial up to the internet and serve my local LAN. It even auto-dialed on demand when any computer on the network requested a non-local IP address.

I do not remember how to do it, but I know it can be done.

---

### Post by skew on 2010-09-21
> **endotherm said:**
> based on your problem description, no I would not assume that windows would fare any better, but it may be worth a shot if you really want to. 

I wonder if the problem doesn't have somthing to do with avahi.

Thank you. I'll check it out and disable it and see where that leads.

Actually I should have checked first before replying. I don't have avahi on this box.

---

### Post by skew on 2010-09-21
> **Slim Odds said:**
> You might try using a static IP address for your LAN.

It's been many years.... but before I was able to get DSL I used a modem to connect via dial up to the internet and serve my local LAN. It even auto-dialed on demand when any computer on the network requested a non-local IP address.

I do not remember how to do it, but I know it can be done.

Pity you don't remember. That sounds just like just what I am looking for. All the computers on my system have static IP address but my ISP assigns a dynamic IP when I dial in (if that matters). I'll keep hammering away at it. In the mean time If you just happen to remember how you did it let me know.

---

### Post by skew on 2010-09-21
> **Mark Phelps said:**
> 

Did you check the DD-WRT forums to see if they can help you?


I did that. It seems they have people asking the same question.
heres one reply

"Is possible as long drivers are available.
Does it work in linux?"

[http://www.dd-wrt.com/phpBB2/viewtopic.php?t=79328&highlight=56k](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=79328&highlight=56k)

Which is why I came here...

I'm still searching there so we'll see what I can turn up.

---

### Post by pbrane on 2010-09-21
if you can get on your dialup and ping a site, write down the IP address, e.g., google.com is 74.125.159.105 from where I'm at. then when you have the problem with not connecting to sites try connecting with the IP address not the host name and see if that works. If it does then you have a DNS issue. I'm not sure how to get around that yet. When you use dialup your ISP will pass you their DNS server info during a DHCP session. But if you are on the LAN then your router gives you it's DNS ( or not ) during that DHCP session. Your resolv.conf file is dynamic, it's usually over-written by NetworkManager IIRC. You might be able to hard code your ISPs DNS setting in your router. If the DNS IPs are the same then it shouldn't matter.

[http://ubuntuforums.org/showthread.php?t=297834]("http://ubuntuforums.org/showthread.php?t=297834")

Another idea is to hardcode your DNS in your network connection itself. I think ppp0 has a network config that will allow you to do that.

I don't think the issue is DD-WRT, I think this would happen with the vendor firmware too.

---

### Post by skew on 2010-09-21
> **pbrane said:**
> if you can get on your dialup and ping a site, write down the IP address, e.g., google.com is 74.125.159.105 from where I'm at. then when you have the problem with not connecting to sites try connecting with the IP address not the host name and see if that works. If it does then you have a DNS issue. I'm not sure how to get around that yet. When you use dialup your ISP will pass you their DNS server info during a DHCP session. But if you are on the LAN then your router gives you it's DNS ( or not ) during that DHCP session. Your resolv.conf file is dynamic, it's usually over-written by NetworkManager IIRC. You might be able to hard code your ISPs DNS setting in your router. If the DNS IPs are the same then it shouldn't matter.

[http://ubuntuforums.org/showthread.php?t=297834]("http://ubuntuforums.org/showthread.php?t=297834")

Another idea is to hardcode your DNS in your network connection itself. I think ppp0 has a network config that will allow you to do that.

I don't think the issue is DD-WRT, I think this would happen with the vendor firmware too.

 Well I took your advice and tried the ping test which confirms it's a DNS issue.  It's a shame I can't lock down the resolv.conf file to my ISP's DNS's.  As for your suggestion to "***hard code your ISPs DNS setting in your router***" I'll have to look into that.  I don't know right now if that's possible, actually I don't even know if I have enough know-how to be sure that I'm messing about with the correct settings. 

 Also in regard to your ***"hardcode your DNS in your network connection itself. I think ppp0 has a network config that will allow you to do that"***  If you have anymore information as to how I can go about doing this, it'd be greatly appreciated. Would you know what the ppp network config file is called? 

In the time being I'll try setting up the router with my ISP's DNS's.

Wish me luck I think I'm gonna need it.   

I greatly appreciate your assistance Pbrane thanks! And everyone else who wrote as well. I finally feel like I'm starting to get somewhere. I was spinning my wheel before this. Cheers all! :)

---

### Post by Slim Odds on 2010-09-21
> **pbrane said:**
> if you can get on your dialup and ping a site, write down the IP address, e.g., google.com is 74.125.159.105 from where I'm at. then when you have the problem with not connecting to sites try connecting with the IP address not the host name and see if that works. If it does then you have a DNS issue. I'm not sure how to get around that yet. When you use dialup your ISP will pass you their DNS server info during a DHCP session. But if you are on the LAN then your router gives you it's DNS ( or not ) during that DHCP session. Your resolv.conf file is dynamic, it's usually over-written by NetworkManager IIRC. You might be able to hard code your ISPs DNS setting in your router. If the DNS IPs are the same then it shouldn't matter.

[http://ubuntuforums.org/showthread.php?t=297834](http://ubuntuforums.org/showthread.php?t=297834)

Another idea is to hardcode your DNS in your network connection itself. I think ppp0 has a network config that will allow you to do that.

I don't think the issue is DD-WRT, I think this would happen with the vendor firmware too.

There are some scripts in the /etc/network tree that get called when interfaces come up and go down (like ppp). I'm a little rusty on these, but I'm sure that the info is out there on the Net.

---


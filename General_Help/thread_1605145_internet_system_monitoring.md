---
title: "internet system monitoring"
date: 2010-10-24
forum: General Help
---

### Post by choochoousmc on 2010-10-24
in Ubuntu, How can you tell if your connection is being monitored?
Have  a home system, me and girlfriend are only users.
Lately ALLl websites are taking longer to download.
she claims her system and bank accounts were compromised.
So am wondering if the connection is being monitored.

Lots of tools for "windows" to help determine, but what about linux / ubuntu?

---

### Post by efflandt on 2010-10-25
Is she running Windows?  If her accounts were compromised, her computer may be infected and the slowdown may be that worm or virus trying to spread itself (if not a trojan using it as s spam relay).

But if you do have 2 computers, I imagine you have them connected to a router with switch ports and you cannot really listen in on her traffic from your computer.  Normally a hub is not recommended, but if both of you connected to a hub and then to the router, you could eavesdrop on her traffic using **tcpdump**.

A bit more complicated way if you have 2 network interfaces on your computer would be to configure your computer like a router and route her computer through yours.  But I will pass on explaining that because I do not know if you have multiple computers or are working from the same one.

---

### Post by eival on 2010-10-25
the router is the best monitor, it will show every IP connection to every device.

just a general best bet is to block all UDP ranges other than the ones used by your ISP and any online games you play on your computer(if nessisary), the easiest way to find out your ISP's IP range is to use the Network Tools in System then reset your router, then just simply open a webpage and look for a UDP connection thats using port 53, copy that IP and use the WHOIS tool to see if its your ISP, if so, copy down the full IP ranges listed and create a UDP block in your router allowing only those ranges for any computer connected to that router, unless anyone plays PC games then you'll have to make the nessiary adjustments.

---

### Post by choochoousmc on 2010-10-25
> **eival said:**
> the router is the best monitor, it will show every IP connection to every device.

just a general best bet is to block all UDP ranges other than the ones used by your ISP and any online games you play on your computer(if nessisary), the easiest way to find out your ISP's IP range is to use the Network Tools in System then reset your router, then just simply open a webpage and look for a UDP connection thats using port 53, copy that IP and use the WHOIS tool to see if its your ISP, if so, copy down the full IP ranges listed and create a UDP block in your router allowing only those ranges for any computer connected to that router, unless anyone plays PC games then you'll have to make the nessiary adjustments.

Ok guys thanks.
Little more explaining.
I didn't mean we were using a hub.
Have a brand new netgear router (about 2 month old)
she claims problem on  her WIN XP machine started 4 -5 months back. She crashed her XP machine and now has a new 7 machine.
I am using Ubuntu 10.10 for about 3 weeks.
Never noticed the slowdown until a couple days ago.
Was wondering if the bank or LEA is monitoring.
The internet connection is in my name not hers.
wouldn't they need my ok to monitor it? I mean unless they were covertly monitoring us for wrong doing?

Little confused on your help above, could you define the steps a little better.
Went to network in systems and it does provide any info about ports or ranges.
However in the notification icon  that shows we are connected it does show the IP  #'s
ip address broadcast   subnet, default  primary etc.  But no high low ranges and can't edit from there.

---

### Post by katykat on 2010-10-25
UDP connection thats using port 53, copy that IP and use the WHOIS tool to see if its your ISP, if so, copy down the full IP ranges listed and create a UDP block in your router allowing only those ranges for any computer connected to that router, unless anyone plays PC games then you'll have to make the nessiary adjustments.

=======================================================


Can you clarify?

Port 53 UDP is DNS.

My DNS server 68.xxx.yyy is well outside my ISP range 72.xxx. -74.xxx.


I can limit the range simple enough in my own netgear router , but it looks like it would take out DNS....

---

### Post by eival on 2010-10-25
> **katykat said:**
> UDP connection thats using port 53, copy that IP and use the WHOIS tool to see if its your ISP, if so, copy down the full IP ranges listed and create a UDP block in your router allowing only those ranges for any computer connected to that router, unless anyone plays PC games then you'll have to make the nessiary adjustments.

=======================================================


Can you clarify?

Port 53 UDP is DNS.

My DNS server 68.xxx.yyy is well outside my ISP range 72.xxx. -74.xxx.


I can limit the range simple enough in my own netgear router , but it looks like it would take out DNS....


perhaps your ISP has separate ranges, mine happens to have all IPs between 2 ranges.

if you already know your exact DNS IP range then thats all you need to leave open. unless you use apps or games that need UDP connections.

---

### Post by eival on 2010-10-26
> **choochoousmc said:**
> Ok guys thanks.
Little more explaining.
I didn't mean we were using a hub.
Have a brand new netgear router (about 2 month old)
she claims problem on  her WIN XP machine started 4 -5 months back. She crashed her XP machine and now has a new 7 machine.
I am using Ubuntu 10.10 for about 3 weeks.
Never noticed the slowdown until a couple days ago.
Was wondering if the bank or LEA is monitoring.
The internet connection is in my name not hers.
wouldn't they need my ok to monitor it? I mean unless they were covertly monitoring us for wrong doing?

Little confused on your help above, could you define the steps a little better.
Went to network in systems and it does provide any info about ports or ranges.
However in the notification icon  that shows we are connected it does show the IP  #'s
ip address broadcast   subnet, default  primary etc.  But no high low ranges and can't edit from there.

it can just be an issue with your ISP, they all have slowdowns from time to time, unless your ISP has DOCSIS 3.0 technology.

run a test on speedtest.net and make sure you are getting what you pay for.

also your best bet is to not do online banking with the windows computer at all, or atleast setup a dual boot or virtual machine to run linux and do the banking in that.

or buy a good internet security suite, id suggest Kaspersky, Bitdefender is also normally top 2 each year but i prefered Kaspersky's indepth settings myself, then again if you dont need windows on that other computer just install linux and you'll prolly fix any issues you current have:popcorn:

---

### Post by choochoousmc on 2010-11-27
thanks all.
I have an acer aspire with ubuntu 10.10.
Been tired of windows for several years, but waited until Linux in general became more user friendly.
I also have a windows vista computer that I use now and then.
G/F has a windows machine now.
we are on a netgear router.
But now for the past 2 - 3 weeks we are back up to speed. So don't know what happened.

---


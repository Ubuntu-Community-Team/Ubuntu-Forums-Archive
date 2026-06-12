---
title: "cable modem for two computers at the same time without router"
date: 2012-04-24
forum: General Help
---

### Post by BSG Fan on 2012-04-24
I have two computers, and I have using the same (only) **Cable Modem** surfboard cable modem sb5101 for the last year to supply internet to both different towers-computers. That using the Lan-ethernet cable to my computer and the USB cable to my wife's computer. Both cables worked together without problems for almost a year.

Since 3 days ago, only the internet goes to one computer, the one with the Lan-ethernet cable.

But now, by no way both cables on work together.

I wonder why. :confused:

I called the internet cable provider end they told me it can be that my wife's pc may need the drivers.  So, I reformatted her computer but the problem persists.

I was told by a guy, that maybe the internet provider blocked the IP address and I may need a router.  But, how is possible that I never used a router before and the company didn't mention me anything about blocking my IP so it can be used just for one computer?

What i do to re-establish internet to the other computer using the same Cable modem?

Thanks.

---

### Post by Habitual on 2012-04-24
USB cable alone to your computer work?

---

### Post by mr clark25 on 2012-04-24
if the computer with the cable modem runs linux, it wouldnt be that hard to use an ethernet cable to connect the two, and then setup IPtables to work accordingly. i dont know very much about IPtables, but many others here do.

---

### Post by oldfred on 2012-04-24
I recently purchased a new inexpensive wifi -n router for about $20 on sale. It does not have many features but works. Why not get a router? 

The USB connection is limiting the connection speed to that computer anyway.

Teach me to buy it several months ago. It is now $15.

[http://www.microcenter.com/single_product_results.phtml?product_id=0316231](http://www.microcenter.com/single_product_results.phtml?product_id=0316231)

---

### Post by techsupport on 2012-04-24
In windows they used to have a Share Internet option where if you had two NIC cards on one computer (ethernet adaptors) you could plug the -other- computer into the first computer that had a broadband enternet connection to the internet and share it. 

I've seen it done with Linux, turning a computer into a NAS router like that, but hopefully someone here knows.  It should be possible.

> **BSG Fan said:**
> I have two computers, and I have using the same (only) **Cable Modem** surfboard cable modem sb5101 for the last year to supply internet to both different towers-computers. That using the Lan-ethernet cable to my computer and the USB cable to my wife's computer. Both cables worked together without problems for almost a year.

Since 3 days ago, only the internet goes to one computer, the one with the Lan-ethernet cable.

But now, by no way both cables on work together.

I wonder why. :confused:

I called the internet cable provider end they told me it can be that my wife's pc may need the drivers.  So, I reformatted her computer but the problem persists.

I was told by a guy, that maybe the internet provider blocked the IP address and I may need a router.  But, how is possible that I never used a router before and the company didn't mention me anything about blocking my IP so it can be used just for one computer?

What i do to re-establish internet to the other computer using the same Cable modem?

Thanks.

---

### Post by Mark Phelps on 2012-04-24
> **BSG Fan said:**
> What i do to re-establish internet to the other computer using the same Cable modem? Thanks.

What I would try is switching the connections to the cable modem -- to see if it is just the other PC that is being blocked, or if it is access using the USB connection.

I know that some ISPs use Mac address validation such that switching the cable modem from one PC to another can cause service to be denied, but I don't know how they would do that with a USB connection instead of a network connection.

As to two IP addresses, that is a likely culprit.  Every ISP I've dealt with in the last five years has demanded that you purchase some kind of family plan for them to issue you more than one IP addres -- and in that case, "hiding" behind a router will solve that problem.

---

### Post by oldfred on 2012-04-24
Years ago when I did not have a router, it took 20 minutes for the cable network to register a different computer. It was so frustrating, I ended up just getting a router.

---

### Post by lisati on 2012-04-24
My thought is that if you can afford it, a router might be the way to go, as it can help simplify things.

I'm also wondering if having one computer connected via USB and the other via ethernet might be difficult: some modems might be configured to use one or the other but not both. [citation needed]

Failing that, I have seen threads in the forum where the Ubuntu equivalent of Windows' Internet Connection Sharing has been successfully configured. One link to check out might be [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by BSG Fan on 2012-04-26
Reading your replies.
I will check, wait

:guitar:

---

### Post by BSG Fan on 2012-04-26
okay guys
in the computer (B) where I have no Internet, I tried the **sudo killall dnsmasq**  after ignoring the IPv6 option.

Now It seems that computer B has internet but at the same time has not Internet.
There is something missing...
what can be?





[I]Active Network connection:
General:
Interface: Ethernet (eth0)
Hardware address: 00:1E:8C:C4:18:12
Driver: forcedth
Speed: 100mb/s
security: None

IPv4
IP address: the one it has
Broadcast address: the one it has
Subnet Mask: the one it has.

IPv6
Ignored[/I]

---

### Post by BSG Fan on 2012-04-26
Guys, I succeed!!!!!

I was trying in computer B another type of wired connection and I did this:

Wired
Device MAC address: I selected the one it suggested me.
Cloned MAC address: I copied the same number has my Computer A

and

I ONLY went to IPv6 Settings:
Method: Automatic, addresses only

I saved it,

and I clicked the new connection in the wired connection icon,

and
YES!!!!!!!!!!!!!!!!!!!!

---


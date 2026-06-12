---
title: "Help me understand how DHCP and Static IP's work"
date: 2011-08-29
forum: General Help
---

### Post by greavette on 2011-08-29
I have a problem understanding just how DHCP and Static IP addresses work exactly.  

If I use DHCP to give out IP addresses, our security router that does this (using Untangle) also has the ability to save IP addresses by MAC address so each time the PC will receive the same IP.  But what if I used a static IP (outside my DHCP pool).  Since our DHCP server doesn't give it out...how do other PC's in our office know that the a PC with a static IP exists?  Does this PC with the static IP broadcast out a message to our network to say it's there? I know I can add the static IP and MAC address to our DHCP server, but I'm trying to solve (and understand) what would happen if our DHCP server (Router) failed...how can I keep our office running until the problem is fixed.

Thanks in advance for any help/insight you may provide.

---

### Post by byb3 on 2011-08-29
Yes you're right, it does essentially broadcast out it's IP address.

When a PC wants to know who has IP address 192.168.1.2, it broadcasts out a packet (known as an ARP broadcast) that asks all PCs on that broadcast domain if that PC has IP address 192.168.1.2.  The PC with that IP address then replies and says 'that's me!'.

Once this has happened, your router should make a note of the IP address and the MAC address which maps to it which means in future it doesn't need to ask.

The only problem with static IPs is that they can become cumbersome to manage if there are too many of them.

---

### Post by seawolf167 on 2011-08-29
The devices will broadcast their IP over LAN. As you mentioned, you want to keep things like servers, printers, etc. on static IP addresses so they can always be found in the same spot. Things like client computers will have dynamic IP addresses, and you may want to setup a short lease time for things like laptops, phones and tablets so you don't run out of addresses and have to set up a subnet. An important point here is that the devices will only broadcast on their own subnet, so if you need more addresses than available, you'll have to add some more routing rules.

---

### Post by greavette on 2011-08-29
Thanks very much for the answers and information.  This greatly helps me understand how networking works.  

We have a very small office with under 50 servers, workstations, printers, devices on our network that would require an IP.  I use Virtual Machines as much as possible to help with failure (I support our office remotely).  so if I wanted to remove a failure point for us if our DHCP server didn't work, I could then use static IP's for all our devices.  If for some reason our router did fail or have problems, I could ensure that my co-workers could continue working without any problems.

After that, the only other point of failure our security router would have would be our DNS server.  

Does the above sound about right?

---

### Post by haqking on 2011-08-29
> **greavette said:**
> Thanks very much for the answers and information.  This greatly helps me understand how networking works.  

We have a very small office with under 50 servers, workstations, printers, devices on our network that would require an IP.  I use Virtual Machines as much as possible to help with failure (I support our office remotely).  so if I wanted to remove a failure point for us if our DHCP server didn't work, I could then use static IP's for all our devices.  If for some reason our router did fail or have problems, I could ensure that my co-workers could continue working without any problems.

After that, the only other point of failure our security router would have would be our DNS server.  

Does the above sound about right?

If they are on the same network and not subnetted then if the DHCP stops working they can still communicate though not as efficiently as they will give themselves a private address of 169.x.x.x in windows this is called APIPA in linux it is called AVAHI

There will be no internet connectivity though and statics such as servers etc, printers will be harder to find but it allows for basic networking and for the stack to load

---

### Post by seawolf167 on 2011-08-29
> **greavette said:**
> I could then use static IP's for all our devices.

This would be an absolute nightmare to setup and manage. All 50+ devices with static IPs? How are you going to handle wireless devices that leave and re-enter the office environment like phones, tablets, laptops, etc.? [see next point]

> **greavette said:**
> so if I wanted to remove a failure point for us if our DHCP server didn't work, I could then use static IP's for all our devices

What is handing out IP addresses? Is it your actual server? What kind of server environment are you using if that is your DHCP server?

Note that a failed DHCP server will result in private addresses being "elected" during the failure time.

If, however, you are using your gateway/router as a DHCP server, those are generally pretty cheap, and would be easiest just to purchase a duplicate device and restore the config settings on the new [duplicate] device with the settings from the existing device. That way you have a backup in place should it ever go down. Then you don't have to manage all those static IPs...

---

### Post by greavette on 2011-08-29
None of our employees use wireless laptops, tablets or phones.  All our workstations use only wired connections to do their work.

All our PC's and servers are on the same network..we don't have any subnets on our network.

Yes, I would agree that using static IP's would initially be hard to setup, but if it removes a point of failure for our office, I think it would be beneficial.

Our Security router uses the Untangle O/S and is our gateway to the internet for our office.  It also has our DHCP server and DNS server.  You are correct in that we could drop in our backup Untangle router (we have one just in case), but this wouldn't be done until the evening when I could get our on-site resource in to be my hands and eyes to making the change.  So in the meantime...assuming worst case scenario with our router going down mid-day during work hours, I want to ensure my co-workers can continue working throughout the day without interuption.  In the evening I will the work to replace our router.

Or are you saying that if I didn't use static IP's in our office and our security router goes down mid-day thereby taking our DHCP server offline...my co-workers could continue to work throughout the day until the evening when I will drop in our backup router.

Thanks!

---

### Post by byb3 on 2011-08-29
> **greavette said:**
> None of our employees use wireless laptops, tablets or phones.  All our workstations use only wired connections to do their work.

All our PC's and servers are on the same network..we don't have any subnets on our network.

Yes, I would agree that using static IP's would initially be hard to setup, but if it removes a point of failure for our office, I think it would be beneficial.

Our Security router uses the Untangle O/S and is our gateway to the internet for our office.  It also has our DHCP server and DNS server.  You are correct in that we could drop in our backup Untangle router (we have one just in case), but this wouldn't be done until the evening when I could get our on-site resource in to be my hands and eyes to making the change.  So in the meantime...assuming worst case scenario with our router going down mid-day during work hours, I want to ensure my co-workers can continue working throughout the day without interuption.  In the evening I will the work to replace our router.

Or are you saying that if I didn't use static IP's in our office and our security router goes down mid-day thereby taking our DHCP server offline...my co-workers could continue to work throughout the day until the evening when I will drop in our backup router.

Thanks!

It really depends on your lease times.  Most are about 7 days by default, so only when the leases started expiring would you see issues.

If you are really concerned about failover, you mentioned you are using virtual machines?  Set yourself up a simple backup DHCP server (512mb will be more than enough) with dhcp3-server installed as a backup solution.  With only 50 machines to manage this shouldn't be too difficult for you.

If you are looking for the simplest solution, I would go with your original idea of statically IP addressing all machines.  For an office of 50 I think this would be ok, but annoying!

---

### Post by bodhi.zazen on 2011-08-29
> **greavette said:**
> I have a problem understanding just how DHCP and Static IP addresses work exactly.  

If I use DHCP to give out IP addresses, our security router that does this (using Untangle) also has the ability to save IP addresses by MAC address so each time the PC will receive the same IP.  But what if I used a static IP (outside my DHCP pool).  Since our DHCP server doesn't give it out...how do other PC's in our office know that the a PC with a static IP exists?  Does this PC with the static IP broadcast out a message to our network to say it's there? I know I can add the static IP and MAC address to our DHCP server, but I'm trying to solve (and understand) what would happen if our DHCP server (Router) failed...how can I keep our office running until the problem is fixed.

Thanks in advance for any help/insight you may provide.

I would only mention that dhcp and dns are two separate issues.

A dhcp server assigns ip addresses to clients and eases the work of a sysadmin.

Other options vary by router, some routers will allow you to configure static ip by mac or assign the same ip to the same mac , others will not, so sometimes you would need to manually configure each and every client ... Enter dhcp server.

DNS is name resolution and is done by a dns server.

Take a look at something like dnsmask, will do both dns and dhcp.

The alternate to a DNS server sort of varies by OS. Windows uses WINS for example. On LInux you can use Avahi, but in my experience avahi is a bit bumpy.

---

### Post by greavette on 2011-08-29
Yes, we make extensive use of Virtual Machines in our office.  This greatly helps with backup and restore of systems.  It also greatly helps us for offsite backup since I backup all our VM's to a tape drive that we swap each week.

I have been thinking of using a backup DHCP and backup DNS server in our office.  Our DNS server is equally important to us since our shares in our office are done using our DNS hostnames.  I've recently discovered Zentyal which has DHCP and DNS capability and this server also runs from a VM (for easy backup/restore).  I have a static IP for our Zentyal server so I could use this (enable the DHCP and DNS modules) if our primary router failed so at least our office could continue to run without problems (for the short term) by connecting to each other and continuing their work.  We would then have an issue with Internet Access and our mail...but those can safely be down for a day or two (if it took that long) while the backup box is installed.

Thank you for the suggestion of dnsmask..I'll read up on this to learn more.

Thanks to all of you for helping me understand how networking works and how best to keep our office running with minimal interruption.

---


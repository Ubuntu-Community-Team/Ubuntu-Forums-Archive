---
title: "Strange IP Address Question."
date: 2010-01-04
forum: General Help
---

### Post by zozza on 2010-01-04
I have a dual boot: XP and Ubuntu.

When I load XP I have an IP address (shown in ipconfig /all) and [www.whatismyip.com](www.whatismyip.com) of 144.82.192.154

When I load Ubuntu I have an IP address (shown in ifconfig and [www.whatismyip.com](www.whatismyip.com)) of 144.82.193.37

These IP addresses seem to be static since I have an Ethernet connection.  I have rebooted several times and get the same addresses in XP and Ubuntu. 

Why are they different?

Thanks!

---

### Post by Groundswell on 2010-01-04
is your network....   web>modem>router>pc
or web>modem>pc
or is it one of those fancy modems with router features?? :wink:

---

### Post by zozza on 2010-01-04
I just connect directly into the Ethernet socket provided by my University.

---

### Post by =not4prophet= on 2010-01-04
you are receiving a dhcp address from your university's network.  Each OS performs it's own request and stores the IP address it receives from the network.  The addresses appear static because Windows and Ubuntu both renew their leases for their respective IP addresses when they boot up and connect to the network.  If you were to turn your computer off and leave it off for a long time (usually longer than 8 days) you would most likely receive new addresses from the network.

---

### Post by zozza on 2010-01-04
Thanks - so therefore technically my IP is dynamic then?

So why does my router renew my IP address much more frequently than the Ethernet connection?

---

### Post by VastOne on 2010-01-04
> **zozza said:**
> Thanks - so therefore technically my IP is dynamic then?

So why does my router renew my IP address much more frequently than the Ethernet connection?

That would be a setting that can be altered in the router settings.  DHCP renew settings are a standard feature even the most basic of routers.

---

### Post by pricetech on 2010-01-04
> **zozza said:**
> I have a dual boot: XP and Ubuntu.

When I load XP I have an IP address (shown in ipconfig /all) and [www.whatismyip.com](www.whatismyip.com) of 144.82.192.154

When I load Ubuntu I have an IP address (shown in ifconfig and [www.whatismyip.com](www.whatismyip.com)) of 144.82.193.37

These IP addresses seem to be static since I have an Ethernet connection.  I have rebooted several times and get the same addresses in XP and Ubuntu. 

Why are they different?

Thanks!

The post that mentions IP renewal is correct.  Both your winders and your Linux will try to renew the IP they had earlier.

The IPs you list are public IPs, so you are connecting directly to the Internet and are receiving IPs from the university's ISP.

---

### Post by jamesisin on 2010-01-04
As mentioned, you have public IP addresses.  You are getting those from your ISP (which sounds like University College London).  Your ISP provides a longish lease-time for DHCP addresses (days, probably, as mentioned above).  Each of your boots is recognized as a different device by your ISP and as such receives its own lease.

---


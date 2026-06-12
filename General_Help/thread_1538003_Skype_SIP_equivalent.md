---
title: "Skype SIP equivalent"
date: 2010-07-24
forum: General Help
---

### Post by Nonno Bassotto on 2010-07-24
I'm trying to replace Skype with a SIP-based solution. There are many programs available, and although some are reported not to work well in Ubuntu, I wil try and find out.

My problem is getting a SIP account. I don't care about calling land lines or mobiles, at least for now. With Skype you can set up an account easily in a few minutes. Instead it seems to me that all SIP operators assume that you will want to make non SIP calls and ask you for details like credit cards for payment.

This would not be a problem for me, once I have found a reliable service I can trust. But at the beginning I'm not happy to disclose such details to every company I should try. Moreover I will have to set up more than one account to make some trial calls.

Is there any to get a free SIP account only to be used for free calls without too much hassle?

---

### Post by gradinaruvasile on 2010-07-24
There is no SIP Skype equivalent.
Its because the SIP protocol isnt reliable when used over the internet. Skpe on the other hand has a very good (SIP-derived i think) communication protocol that is very good at Nat/firewall traversing and also has some very good proprietary codecs that dont need much bandwidth to deliver crystal clear sound quality.
SIP is 100% reliable only in controlled and well routed networks (we use a VPN at office to connect to our Trixbox server).
When using internet servers, the reliability is down the drain - we have firewall set up on the routing server and this effetively kills the SIP protocol - meaning the sound goes out but doesnt come back because it is blocked by the firewall (Skype has no problems).
Other than that every SIP client has its own routing mechanism (and slightly or not so slightly different signalling implementation of the SIP stack) some better than others (SIP Communicator and Linphone are the most reliable of the many i tested). 
This difference leads to potential problems when using 2 different clients.
Also the providers implement the SIP protocol differently, for example ekiga doesnt work well at all for me - sflphone accounts on the other hand do.

I tested many SIP clients and some providers:

-Sflphone has both a SIP/IAX client and servers where you create an account on the fly from their client (it has peer to peer call encryption too). No video.
-I tested SIP2SIP and was working quite good. There is also Iptel.org.

Clients: - i use Sip Communicator mostly because it has good sound quality, good SIP routing and supports tons of protocols (everything as Pigin does then more + SIP with video + call encryption).
- Linphone hasnt got many features but it is very reliable and it is available in the repositories.
- Sflphone has its own PPA over at Launchpad, it has only voice ATM (video is being implemented). It is quite good also.
-Ekiga on the other hand sucks as a SIP client - the sound doesnt always work even in our internal network.

---

### Post by Nonno Bassotto on 2010-07-24
Thank you very much for your advice. I will try some and let you know.

---


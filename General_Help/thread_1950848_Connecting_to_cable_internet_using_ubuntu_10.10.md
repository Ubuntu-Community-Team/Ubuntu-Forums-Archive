---
title: "Connecting to cable internet using ubuntu 10.10"
date: 2012-04-01
forum: General Help
---

### Post by madokie on 2012-04-01
I need help in setting my Ubuntu 10.10 so I can log into the internet using my new cable connection so I can get rid of my overpriced and slow DSL. So far I've not been able to figure out what to do. My cable modem is a motorola sb5100 and it is not wireless.
I tried to set it up manually but I don't know what my gateway is so I didn't get too far without knowing that. I don't even know where to look for that info. The cable help desk told me they can't help me that it was up to me to set my computer so it will access the cable modem. 
I really appreciate any help I can get.
Thank you
David

[http://www.speedguide.net/routers/motorola-sb5100-sb5101-surfboard-5100-docsis-20-6](http://www.speedguide.net/routers/motorola-sb5100-sb5101-surfboard-5100-docsis-20-6)

---

### Post by oldfred on 2012-04-01
Can you connect to this:

[http://192.168.100.1/startup.html](http://192.168.100.1/startup.html)

But cable co does have to initialize system and help desk should tell you if it is working at their end or not.

Before I had router and tried unplugging one computer and plugging in another it took Comcast 20 minutes to recognize new mac address.

---

### Post by madokie on 2012-04-01
My cable box is connected to the internet and my computer says I'm connected to it but I get nothing when I try to use it.
I'd like for someone to help me set up my internet connection manually. You know like where I find the info that I need to do that such as where/what is my gateway and where do I get that info. I've been using ubuntu for a while but I've never tried to do anything like this before.
Thanks
david

---

### Post by oldfred on 2012-04-01
Cable co is DHCP, so it should just connect if physically connected correctly.

And if you have to put something in the help desk has to give that info to you. There is not just one gateway.

---

### Post by critin on 2012-04-01
I know this is very simplistic, and not knowing when cable was installed I'm probably way off here...but, did you try turning off the computer and turning it back on with the modem and router (if used) already turned on?   If it was installed and not restarted, it might not catch it.

The system should automatically find it if it's on when comp. starts.

---

### Post by critin on 2012-04-01
On the link you posted scroll down to find this, 

Device Management Default IP address:  192.168.100.1

On the next page it goes to is some info that might help.
But really, it should be automatic, if not the cable company needs to help you.

*Modems rented from the cable co. always work.*

---

### Post by HiImTye on 2012-04-02
make sure that you are logging into the router using DHCP, I dont remember the old connection manager but it should be similar to the new one. click on the connections icon on the right side of your main gnome toolbar, then go to settings or options or connections or w/e. next, select 'auto eth0' or whatever your connection is there. then go to ipv4 and make sure it is 'automatic DHCP' or whatever equivalent.

after that, it should 'just work' if not then they need to check their router/modem

---


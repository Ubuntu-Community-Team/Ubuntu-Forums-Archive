---
title: "Web Control with Transmission"
date: 2011-04-04
forum: General Help
---

### Post by d00derino on 2011-04-04
Hi all,

I have a job, and I have a media server at home. When I'm at one, I have time to service the other. Less cryptically, I'd like to start downloads via the Internet on my media server while I'm at work and have the time to do so.

However, I cannot get Transmission to work using it's web settings. I go into *Edit > Preferences > Web* and have entered everything in correctly. What's more, when I go to launch the browser, *localhost:9091* works perfectly. Without a hitch.

Before I'm able to set up a DNS so I can start using Transmission from work, I need to get it running on my local network. For some reason, *localhost:9091* fails to be found on any computer other than the one Transmission is on. I know I opened the port correctly in my router, here is the setting:

```

Service Name      Start Port      End Port      Server IP Address 
1 Transmission    9091            9091          192.168.1.4 
```

Hopefully that came out correctly. In transmission, I have enabled IPs 127.0.0.1 (localhost) and 192.168.1.* to use Transmisson web. Like I said, it won't work.

I read/tried installing the daemon. This got me a bit further, prompting me to add IPs into the whitelist in *settings.json* but when I added the same ones I did in the GUI to the *rcp-whitelist* I got the same message telling me to add IPs. 

Unfortunately, most guides online are out of date. I understand that Transmission had an upgrade lately? I wouldn't know, I don't track it very well. Nevertheless, Google was of no help nor was searching these boards, at least using the keywords I did. 

Could someone point me in the right direction, I'd be very grateful.

---


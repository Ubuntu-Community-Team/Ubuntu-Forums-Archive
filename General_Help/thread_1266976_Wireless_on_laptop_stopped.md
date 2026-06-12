---
title: "Wireless on laptop stopped"
date: 2009-09-15
forum: General Help
---

### Post by HolyShnikes on 2009-09-15
Last night while watching football I installed a fresh ubuntu on my laptop computer (used wubi from vista) 64bit edition, version 9.04.

It installed great and ran smooth for the first 30 minutes after the install.  Here is the problem though.  My wireless network I have hidden, and I added it to the network and connected fine.  I put in the SSID and WEP 128bit/passphrase.  It seemed like a very basic setup.  There wasnt anything I remember extra to put in the network window.  

An update page loaded some time later with about 157mb worth of things to download and install.  I looked over the list and remembered doing these for my destkop as well.  So I accepted it and let it install.  The computer rebooted and when it restarted, it wouldnt let me connect to the network.

I noticed that a red x next to the wireless signal bar and when I clicked it it gives me an option to VPN.  From there I go to add a wireless connection.  The options for the simple page had changed and added BSSID and a few more tabs and options.

When I go to the tab to enter my passphrase again and connect it just wont work.  I deleted it and re-added the network but I still have yet to get it working.

I have not tried to reset the router because (I think) it would reset all my settings and I have 3 other computers hooked up to that network, not to mention my iphone and my wifes itouch.  I wouldnt want to reset my wireless network security settings again and have to reconnect all my other computers to it.

Anyone have any idea what I could do to fix this?  Thanks in advance.

---

### Post by HolyShnikes on 2009-09-15
I did forget to mention that I am running on an HP laptop.  The exact model I am unsure of, but I do know it is a dV6000.  Are there any known wireless issues with using this kind of laptop that I should be aware of?  or is my main problem one of a kind?

Thanks.

---

### Post by HolyShnikes on 2009-09-15
I fixed it.  The problem was that I accidentally enabled the alternate madwifi driver while I was updating my graphics driver.  I disabled it and rebooted.  Works fine now. 

It wasn't letting me view the wireless connections, and that was the problem.

---

### Post by Aniso on 2009-09-15
Exact same problem here, using an hp mini 110 with ubuntu netbook remix.  It was working fine but had the red x when I got back from school. In fact the wireless is working fine on another hp mini we have with unr as well. Any help would be greatly appreciated.

---

### Post by Aniso on 2009-09-15
Yep, similar problem here.  Installed some packages last night and it appears somehow the proprietary driver got kicked off. Reactivated and rebooted, now working.  Thanks.

---


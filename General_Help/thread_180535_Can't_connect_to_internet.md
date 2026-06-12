---
title: "Can't connect to internet"
date: 2006-05-22
forum: General Help
---

### Post by veev on 2006-05-22
I just installed Ubuntu. While installing, it said it couldn't find the DHCP server. Once Ubuntu was installed, I just went to the network settings, deactivated and then reactivated my ethernet network connection, and then everything worked fine (i.e. I had internet access). Then I rebooted, and now I can't access the internet. It device driver appears to have no problem finding my network card (which a 3Com..) and having drivers for it. The network settings seem to be fine, it even automatically finds the DHCP server. But when I open firefox, it just sits there waiting for google.com (or any other site) load, and after a few minutes it just times out. How can I go about trouble shooting this? What other info can I post to this forum to get help? Thanks

---

### Post by Al3xanR0 on 2006-05-22
Try pinging sites by ip if you get successful replies then try to ping via name if you are unable to then DNS server entries need to be aaded to you network configuration (/etc/resolv.conf).

---

### Post by handy on 2006-05-22
***I have to turn off ipv6 in firefox before i can browse the web.***

So, try the following:

Enter **about:config** in the address field of firefox.

Then enter **ipv6** in the new **Filter Field:**

Then double click on the one & only line displayed, to change it's boolean value to **True**.

That's all I need to do to browse the web, without those steps I go nowhere!!

All the best! :KS

---


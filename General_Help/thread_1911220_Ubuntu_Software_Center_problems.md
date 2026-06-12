---
title: "Ubuntu Software Center problems"
date: 2012-01-18
forum: General Help
---

### Post by 0011235813 on 2012-01-18
Ubuntu Software Center doesn't seem to be working properly. 

I recently had a connection issue with my wireless router, whereby all my computers where left with an Internet connection that wasn't functioning properly; browsers wouldn't open pages, or the pages that were opened didn't work properly, clients didn't work, etc. etc. 
Bizarrely, Mozilla Thunderbird worked fine. After my Internet went back on, my Ubuntu laptop still couldn't connect; apparently I had accidentally mis-configured DHCP settings in Network Manager. Moving on, all my clients now work; **except** USC. However, ```
apt-get
``` works fine in the terminal. 

My question is; could there be anything preventing USC from working?

---

### Post by KRISHNASHK on 2012-01-18
probably the repository is not added.

---

### Post by HazKO on 2012-01-18
error: unknown filesystem.
grub rescue>
 
what does this mean, i can not start my laptop.. what do i need to do?

---

### Post by 0011235813 on 2012-01-18
> **KRISHNASHK said:**
> probably the repository is not added.

Uh nuh-oh, apt-get works fine and USC previously worked fine before the network error occurred.

---

### Post by phibxr on 2012-01-18
> **0011235813 said:**
> Ubuntu Software Center doesn't seem to be working properly. 

I recently had a connection issue with my wireless router, whereby all my computers where left with an Internet connection that wasn't functioning properly; browsers wouldn't open pages, or the pages that were opened didn't work properly, clients didn't work, etc. etc. 
Bizarrely, Mozilla Thunderbird worked fine. After my Internet went back on, my Ubuntu laptop still couldn't connect; apparently I had accidentally mis-configured DHCP settings in Network Manager. Moving on, all my clients now work; **except** USC. However, ```
apt-get
``` works fine in the terminal. 

My question is; could there be anything preventing USC from working?

Have you checked your DNS-settings?

You might want to enable the Google public DNS just for troubleshooting purposes.

[http://code.google.com/speed/public-dns/]("http://code.google.com/speed/public-dns/")

---

### Post by 0011235813 on 2012-01-18
> **phibxr said:**
> Have you checked your DNS-settings?

You might want to enable the Google public DNS just for troubleshooting purposes.

[http://code.google.com/speed/public-dns/]("http://code.google.com/speed/public-dns/")

I'll try that. I used openDNS previously, but I turned that off because of some issues... I hope Google DNS doesn't randomly block sites.

---

### Post by 0011235813 on 2012-01-21
The problem seems to have disappeared... No idea what was wrong. But it's working fine now. Maybe it was just a temporary network problem.

---


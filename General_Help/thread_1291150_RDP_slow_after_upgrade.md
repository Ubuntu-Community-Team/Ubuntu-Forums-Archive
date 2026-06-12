---
title: "RDP slow after upgrade"
date: 2009-10-14
forum: General Help
---

### Post by Elijah on 2009-10-14
I have two laptops, one of them has an old version of ubuntu and the newer one 9.04

Before the upgrade tsclient RDP was decent, but after reverting to my other laptop (9.04) it was unbearably slow that it logs me off after a few seconds. 


I tried the alternative gnome-rdp but I couldn't get far... 

What can I do with my 9.04 to perform well using rdp?

---

### Post by Giblet5 on 2009-10-14
9.04 is not likely to be the problem.

It is more likely that your network configuration is the cause of the performance issues. That will always be the bottleneck, no matter how fast or slow it seems to be working.

Did you manually configure the network adapter?

Are you using wired or wifi? Are you sure you're using YOUR wifi?

---

### Post by Elijah on 2009-10-14
I used the same wifi connection for both laptops. I tried both side-by-side, the 8.10 one's tsclient works very well. The 9.04 client with the same settings doesn't

---

### Post by Giblet5 on 2009-10-14
> **Elijah said:**
> I used the same wifi connection for both laptops. I tried both side-by-side, the 8.10 one's tsclient works very well. The 9.04 client with the same settings doesn't

I'll still bet $$$$$$ that it's a network config issue.

Did you configure networking or are you using "Automatic" (DHCP) via Network Manager?

Network Manager rarely sets things up correctly, but it IS easy 80% of the time.

On laptops, I use WiCD and provide manual configurations for wifi and wired. I always remove network-manager (laptops OR desktops) because it is poorly documented and flaky.

---

### Post by Elijah on 2009-10-15
It's automatic dhcp. 

Anyways it sped up now, it's strange... that is after I sent a note to my client that I'm having trouble connecting to his servers.. the problem could be from the client's side, whatever it was..

---


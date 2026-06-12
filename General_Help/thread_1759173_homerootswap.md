---
title: "/home/root/swap??"
date: 2011-05-15
forum: General Help
---

### Post by pilulelilule on 2011-05-15
Hi guys,

A bit of help is needed. I've set a side 80GB on a separate partition, i have 4GB of RAM. I know it will ask me to set /home /root and /swap. Can anyone tell me how much should i set each one to be with my partition size and RAM. Thank you!

---

### Post by Hedgehog1 on 2011-05-15
For an 80 gig drive and 4 gigs of RAM, I would suggest the following:


/dev/sda5 '/' (root) 18 gig
/dev/sda6 '/home' all space not taken up by '/' and 'swap'  ~ 55 gig
/dev/sda7 SWAP 4.4 gigs (RAM size + 10%)


***The Hedge***

:KS

---

### Post by pilulelilule on 2011-05-15
thank you

---


---
title: "quick Q about live CD IP's"
date: 2012-05-15
forum: General Help
---

### Post by flyingsliverfin on 2012-05-15
I was wondering, when I boot a live USB/CD on a host computer, does the router assign the same IP number to the computer? Theoretically the CD is just using the computer as a host and it looks the same to the router (right?). DHCP doesn't change every time (i think) so even with DHCP shouldn't the IP not be totally new?
My friend asked and I couldn't answer and thought it might be an interesting question...
:)
Thanks!

---

### Post by rai4shu2 on 2012-05-15
Most routers are configured to have a range of IPs they offer via DHCP server built into them. That IP can be "rented" so to speak by your computer for a certain time. Once that time runs out, that IP reservation expires and could be used by another computer that connects to that DHCP server.

Most reservation times tend to be in the hours, so you only need to worry if it's a busy router.

---


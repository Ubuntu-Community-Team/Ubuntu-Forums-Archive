---
title: "Preventing bootable media running?"
date: 2010-07-22
forum: General Help
---

### Post by RoseRodent on 2010-07-22
This is a bit of an odd one, it's not so much about using Ubuntu but about *not* using Ubuntu. I am just setting up a new computer for my daughter. I have spent days configuring parental controls and lockdowns and such to stop her from being able to view unsuitable content, download programs I don't want, anything that can mess up the computer, etc. etc. At this age I am going to be over her shoulder 100% of the time while she works anyway, but something that occurs to me is that having set up all this control software in Windows, she could actually override the entire thing really easily by booting from a live CD, USB key or similar, she can keep a whole OS in her pocket and I'd never know. You can only watch so much of the time as they grow up. 

Can I prevent a computer from being capable of booting from external media without some kind of password? How would you begin to go about that? 

Thanks.

---

### Post by davavanstone on 2010-07-22
depending on the bios, you could stop media from running by disabling it from booting from certain media... cds and usbs

---

### Post by davavanstone on 2010-07-22
thinking about it, you could block it from a higher level, such as the router??  Some routers are quite powerful when it comes to blocking stuff... very router dependent though, could involve buying new hardware.

Doing this means that regardless of the OS and/or phones connected through wifi, you cannot access unsuitable content.

---

### Post by mcduck on 2010-07-22
Disabling booting from USB and CD drive in BIOS and setting up a BIOS password to prevent her from changing these settings back is pretty much the only thing you can do.

..not that it would be really secure, since resetting the BIOS password only takes 15 seconds to do (or less if the computer has a clear-CMOS -button somewhere). But perhaps you can count on your daughter not knowing how to do that.

Apart from that, the only other option is to physically secure the computer so she can't access the computer itself. Probably not an easy thing to do at home, and not very practical either. But the thing is that pretty much all computer security features become useless at the point when somebody has physical access to the computer itself.

What comes to restricting content through a router, as suggested above, that would only be practical if you are willing to (and your router supports it) create a whitelist of approved web sites, and everything else would become inaccessible. Of course there might be some ready-made whitelists/blacklists available but personally I really wouldn't trust any stranger's judgement about what's suitable for my kids and what isn't, that's really my decision to make..

---


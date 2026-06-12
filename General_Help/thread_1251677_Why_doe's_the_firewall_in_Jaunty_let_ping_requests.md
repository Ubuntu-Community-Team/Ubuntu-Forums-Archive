---
title: "Why doe's the firewall in Jaunty let ping requests in when the manual says there bloc"
date: 2009-08-27
forum: General Help
---

### Post by dj-toonz on 2009-08-27
Hi all, Hope somebody knows about this, after re-installing jaunty onto a new laptop with HSDPA 3.5g built in, I used shields up website to test if everything was ok for this weekend as I'm taking the laptop away with me over bank holiday & everything was ok baring the ping, I've got that sorted any way now by putting a # before the line (i can't remember which now) but just been checking the ubuntu manual for the firewall & it says that ping requests are blocked at default when that's clearly not the case. could somebody explain why it says one thing & a default install of ubuntu lets ping requests though (when I'm @ home I'm not bothered as my netgear router blocks everything) but when I'm either using wifi or the 3.5g connection I'm more worried about) cheers

---

### Post by lovinglinux on 2009-08-28
Do you know that not allowing a ping, which I believe you are referring to dropping it, allows an attacker to determine that your machine is online? There is a delay between the response when pings a dropped and a skilled person will know if your machine is dropping pings.

More important than allowing pings or not is the fact that Ubuntu does not have any listening services by default, which is the same as having all ports closed.

---

### Post by Dullstar on 2009-08-28
> **lovinglinux said:**
> Do you know that not allowing a ping, which I believe you are referring to dropping it, allows an attacker to determine that your machine is online? There is a delay between the response when pings a dropped and a skilled person will know if your machine is dropping pings.

More important than allowing pings or not is the fact that Ubuntu does not have any listening services by default, which is the same as having all ports closed.

Just curious, what are you trying to say there?

---

### Post by lovinglinux on 2009-08-28
> **Dullstar said:**
> Just curious, what are you trying to say there?

That you shouldn't be worried about pings, but about services. No services = ports closed = why bother about pings?

---


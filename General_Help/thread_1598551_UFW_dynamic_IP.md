---
title: "UFW dynamic IP"
date: 2010-10-16
forum: General Help
---

### Post by SpinningAround on 2010-10-16
Is it possible to make UFW allow connection to a specific IP dynamically. I have an ISP where I get a new IP every time i connect through them, I would only like to allow connections to the IP I currently use. Only workaround I can think of is to allow connections to the ISP entire IP range.

---

### Post by dcstar on 2010-10-16
> **SpinningAround said:**
> Is it possible to make UFW allow connection to a specific IP dynamically. I have an ISP where I get a new IP every time i connect through them, I would only like to allow connections to the IP I currently use. Only workaround I can think of is to allow connections to the ISP entire IP range.

Huh?, your ISP only gives you **one** IP address, there is no need to do any filtering of any other IP addresses because **you don't have them**.

---

### Post by SpinningAround on 2010-10-17
> **dcstar said:**
> Huh?, your ISP only gives you **one** IP address, there is no need to do any filtering of any other IP addresses because **you don't have them**.

Sorry, guess that VPN provider would be the correct term, would it still be possible?

---

### Post by gandaran on 2010-10-17
> **SpinningAround said:**
> Sorry, guess that VPN provider would be the correct term, would it still be possible?
use a dynamic dns service like [dyndns]("http://www.dyndns.com/")

---


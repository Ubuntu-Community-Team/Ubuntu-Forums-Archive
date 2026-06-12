---
title: "Postfix - prevent external connections"
date: 2010-03-14
forum: General Help
---

### Post by KayakJim on 2010-03-14
How can I configure Postfix to reject connections coming from anywhere except the local machine?

---

### Post by dcstar on 2010-03-14
> **KayakJim said:**
> How can I configure Postfix to reject connections coming from anywhere except the local machine?

```
sudo dpkg-reconfigure postfix
```
Select Local only.

---

### Post by KayakJim on 2010-03-15
> **dcstar said:**
> ```
sudo dpkg-reconfigure postfix
```
Select Local only.

Thank you for the response David.

I have mine currently setup to send email to a satellite server but want to reject any connections coming in from my system.

Will the above allow for that configuration?

I previously selected "satellite" when I originally installed Postfix.

---

### Post by gmargo on 2010-03-15
Use the firewall to block incoming connections on port 25.

---

### Post by dcstar on 2010-03-16
> **KayakJim said:**
> Thank you for the response David.

I have mine currently setup to send email to a satellite server but want to reject any connections coming in from my system.

Will the above allow for that configuration?

I previously selected "satellite" when I originally installed Postfix.

I don't know. There are numerous posts on how to restrict Postfix to only accept incoming connections from IP ranges, you can do that or simply stop incoming Port 25 traffic with a firewall.

This is only an issue if you run a public IP address on your system.

---


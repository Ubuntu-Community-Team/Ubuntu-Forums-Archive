---
title: "Hiding IP Address in outgoing Email Headers"
date: 2010-02-21
forum: General Help
---

### Post by pokerbirch on 2010-02-21
I just discovered View > "All message headers" in the Evolution email client and am quite concerned that all my out going emails contain my personal IP Address. I know that this is standard email protocol but i'm wondering if it is possible to hide or modify this header information? Or would i be better off using a webmail client?

---

### Post by dcstar on 2010-02-21
> **pokerbirch said:**
> I just discovered View > "All message headers" in the Evolution email client and am quite concerned that all my out going emails contain my personal IP Address. I know that this is standard email protocol but i'm wondering if it is possible to hide or modify this header information? Or would i be better off using a webmail client?

Firstly, most people use a non-routable internal IP address, so it matters not if this gets sent.

If you are part of the 0.1% that use a fully routable Public IP address, then you will have to live with the standard method that all E-mail clients are required to comply with.

---

### Post by pokerbirch on 2010-02-22
> **dcstar said:**
> Firstly, most people use a non-routable internal IP address, so it matters not if this gets sent.
Ok, i assume that you are referring to the internal router address that starts with 192.168... That is not the address i am concerned about. I sent myself an email via different accounts and in the "Received" header i see: ```
Received: from ?192.168.1.67? (x-xx.xxx-xxx.ip.static.xxx.xx.net [xx.xxx.xxx.xx]) by mx.google.com with ESMTPS id
```
The x's replace details of my ISP (including customer number) and my public IP Address as viewed on sites such as [http://www.whatismyip.com/](http://www.whatismyip.com/).

Am i only seeing this information because i have sent the email to myself, or is it transmitted in all my emails? Even if my IP Address IS transmitted publicly, is it *really* a concern when we consider that every website we visit will (need to) know our IP Address?

---

### Post by nixclusive on 2010-02-22
You will need to use the web interface as most smtp servers will add the received from header when you are sending mail through a mail client. GMail is your best bet in this regard.

---

### Post by lisati on 2010-02-22
I use a static address as well. For my email, I'm inclined to leave it in, so that complaints of abuse can be checked out more easily. One time when I was using email to transfer data between two of my machines, I accidentally reported myself as a spammer.

If you're worried you could check places like [http://www.blacklistalert.org/](http://www.blacklistalert.org/) and [whatismyipaddress]("http://whatismyipaddress.com/") - on the rare occasions my IP address has shown up as listed, it hasn't been my fault - the listing was one for an email provider I use.

---

### Post by pokerbirch on 2010-02-22
> **nixclusive said:**
> You will need to use the web interface as most smtp servers will add the received from header when you are sending mail through a mail client. GMail is your best bet in this regard.
Sounds like a nice job for a Python script and pyCurl. ;)

---


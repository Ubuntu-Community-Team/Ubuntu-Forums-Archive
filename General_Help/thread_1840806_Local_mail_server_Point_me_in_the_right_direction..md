---
title: "Local mail server? Point me in the right direction."
date: 2011-09-08
forum: General Help
---

### Post by BikeHelmet on 2011-09-08
Hi there,

Could anyone point me in the right direction? I'm wondering if it's possible to setup a local mail server? It only has to manage email on my LAN.

I've searched google, but I keep hitting results saying Exchange this Exchange that, and everything says I need a domain or MX record.

Isn't there some way to whip this up with postfix? Or some other piece of software? All I want is sending emails locally to local addresses. No external access required.

-BikeHelmet

---

### Post by haqking on 2011-09-08
> **BikeHelmet said:**
> Hi there,

Could anyone point me in the right direction? I'm wondering if it's possible to setup a local mail server? It only has to manage email on my LAN.

I've searched google, but I keep hitting results saying Exchange this Exchange that, and everything says I need a domain or MX record.

Isn't there some way to whip this up with postfix? Or some other piece of software? All I want is sending emails locally to local addresses. No external access required.

-BikeHelmet

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by BikeHelmet on 2011-09-10
> **haqking said:**
> [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
I already had those links - I assume I'm not understanding something.

Maybe these sections are most relevant?

> Local address extension character: +

> [https://help.ubuntu.com/community/PostfixBasicSetupHowto#Adding_your_local_domains_to_postfix](https://help.ubuntu.com/community/PostfixBasicSetupHowto#Adding_your_local_domains_to_postfix)
But I'm still not understanding how I proceed with making a local email server. The examples provided seem to be for internet *and* local. I don't have a domain, and I don't want to send anything to the internet. I just want it for LAN email.

So, I assume I somehow need to tell it that if I send to [email]user1@somedomain.com[/email], it stays local? (because I certainly don't own somedomain.com)

It'd also be acceptable to use an IP address if I had to - but I'm not sure how that'd work. Email user1@192.168.1.100? :p I don't think SMTP quite works like that?

---

### Post by haqking on 2011-09-10
> **BikeHelmet said:**
> I already had those links - I assume I'm not understanding something.

Maybe these sections are most relevant?




But I'm still not understanding how I proceed with making a local email server. The examples provided seem to be for internet *and* local. I don't have a domain, and I don't want to send anything to the internet. I just want it for LAN email.

So, I assume I somehow need to tell it that if I send to [EMAIL="user1@somedomain.com"]user1@somedomain.com[/EMAIL], it stays local? (because I certainly don't own somedomain.com)

It'd also be acceptable to use an IP address if I had to - but I'm not sure how that'd work. Email user1@192.168.1.100? :p I don't think SMTP quite works like that?


oh ok, i suspect sendmail will do what you need then, it is in repos.

See here for more info [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers)

also look at man mail

mail is built in

---

### Post by lisati on 2011-09-10
If you're wanting an email system for your LAN, installing Postfix should be fine: you are not obliged to allow connections from outside your LAN, set up external DNS or anything fancy like that.

---


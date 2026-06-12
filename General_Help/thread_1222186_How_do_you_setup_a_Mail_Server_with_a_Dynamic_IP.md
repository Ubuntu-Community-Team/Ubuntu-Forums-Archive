---
title: "How do you setup a Mail Server with a Dynamic IP?"
date: 2009-07-24
forum: General Help
---

### Post by cmoney12051 on 2009-07-24
right now i'm using no-ip.com to host my stuff and it works great, but i want to now setup a mail server, but im on a dynamic dns and can't get it switched over to a static. Is it at all possible to set up a mail server with a service like no-ip or DynDNS? If so how would you go about doing it. I have ubuntu server as my server and postfix installed. Please help

---

### Post by gamgee911 on 2009-07-24
DynDNS should work.  you'd have to install ddclient

```
sudo apt-get install ddclient
```

then set up as usual, except where you would use an ip, you'd use the address you created at DynDNS (aka for something like ssh you'd use ssh login@url)

---

### Post by NewbieNik on 2009-07-24
To be honest, in all practices you should not do this...for many reasons.
First off, the lag between you acquiring a new address and no-ip updating can be quite slow and that leaves the possibility of missing mail (Although not so much of the senders email server is configured correctly)
Secondly (And more importantly) this lag could tag your system as a SPAM server. There are also some Black-List providers who will assign any Dynamic Addressed email systems as SPAM.

If oyu have an email account with your ISP then get the IP address of their SMTP server and set it as the "smart host" for your mail server with your email credentials, that way your server will then relay mail through the ISPs mail servers using your account.

---

### Post by zzzBrett on 2009-07-24
> **cmoney12051 said:**
> right now i'm using no-ip.com to host my stuff and it works great, but i want to now setup a mail server, but im on a dynamic dns and can't get it switched over to a static. Is it at all possible to set up a mail server with a service like no-ip or DynDNS? If so how would you go about doing it. I have ubuntu server as my server and postfix installed. Please help

If you're doing this for fun / experience, then great -- but if not, i'd recommend Google Apps.  It is free.

---

### Post by cmoney12051 on 2009-07-24
thanks for the advice, im only doing this for fun. Just to test it out, and it would probably only be sending out a few emails a day if that, nothing big or anything, just for me, any more help would be appreciated, thanks so far :)

---

### Post by cmoney12051 on 2009-07-25
well i thought i had got it but now whenever i try to send a message i get this error

> connect to alt4.gmail-smtp-in.l.google.com[IP ADDRESS]:25: Connection timed out

i don't know what is wrong?

---


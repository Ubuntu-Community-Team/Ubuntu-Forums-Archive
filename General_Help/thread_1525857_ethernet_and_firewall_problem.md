---
title: "ethernet and firewall problem"
date: 2010-07-07
forum: General Help
---

### Post by dawemmy on 2010-07-07
Hi there
new to ubuntu, running 9.1
I have been using wireless only, but I just moved into a new apt. and they have a shared wired internet connection.  So I connected the wire to the ethernet port and Voila everything is great.
UNTIL....
I went to my webhost and try to log on to the c-panel (hostmonster)  and it looked normal gong to a redirect to the host I am on (host 166) but then goes into an infinite logging in, redirect, logging in redirect loop finally spitting me out to the original login page.

Hostmonster says it is my firewall or cookies or the firewall is resetting the cookies.

any ideas what this is and how to fix it?
I think hostmonster help might not have the correct idea.

---

### Post by cariboo on 2010-07-07
Are you running a firewall? to check, open a terminal and type:

```
sudo ufw status
```

If the above command shows that iptables is disabled, is your shared connection running through a firewall?

---

### Post by dawemmy on 2010-07-07
the status reads "inactive"
i doubt I will be able to change firewall settings for the shared connection as I live in Taiwan--there's a language barrier and I don't think the guy knows much about the network,  would probably have to call out the phone company.
what things can I try on my end?
and please help me to understand what exactly is going on?
thanks!!:)

---


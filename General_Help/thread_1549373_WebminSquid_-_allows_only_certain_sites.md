---
title: "Webmin/Squid - allows only certain sites?"
date: 2010-08-09
forum: General Help
---

### Post by TechMansoor on 2010-08-09
Using 10.4, got the webmin installed and squid. Got my access control list setup.

Within the acccess control list setup, I can not go to sites like

methodistmd.org or mollimd.org for whatever reason. But I can go to votekirkland as well as google. Why would webmin and/or squid only work with certain sites within the the defined access control list?

Thanks

---

### Post by TechMansoor on 2010-08-09
well..does anyone know any other proxies i can try besides squid?

---

### Post by bodhi.zazen on 2010-08-09
> **TechMansoor said:**
> well..does anyone know any other proxies i can try besides squid?

There are several proxies available, what do you want a proxy for ?

You can use OpenDNS  and DynDNS for blocking some unwanted sites.

You can use privoxy, polipo, dansguardian, bfilter, and I think there is even a tinyproxy.

Personally I prefer privoxy or bfilter as they will perform adblocking. Privioxy will do white and black lists if that is what you want. Dansguardian is more content filtering. polipo is lightweight and fast.

---

### Post by TechMansoor on 2010-08-09
> **bodhi.zazen said:**
> There are several proxies available, what do you want a proxy for ?

You can use OpenDNS  and DynDNS for blocking some unwanted sites.

You can use privoxy, polipo, dansguardian, bfilter, and I think there is even a tinyproxy.

Personally I prefer privoxy or bfilter as they will perform adblocking. Privioxy will do white and black lists if that is what you want. Dansguardian is more content filtering. polipo is lightweight and fast.


I mean it really is as simple as black and white list to say the least that actually works. I was configuring squid in working through webmin but man...all of sudden it just wants to stop going to certain sites which I don't understand.

Which software has an easy setup that is good for black and white listing? Everything should be black listed with the exception of what I specify..should I try privoxy?

---

### Post by TechMansoor on 2010-08-09
also..does privoxy have a web interface?

---

### Post by bodhi.zazen on 2010-08-09
Privoxy has a web interface, but may take you some time to learn how to configure (I found the web interface easy to use).

You will need to configure privoxy to allow you to access the web interface, and the documentation for privoxy can seem overwhelming at first.

Hard to know what your problem is with squid without asking you to post your configuration file(s), and considering that the squid conf file is 4,000 lines or so long, you would need to post the relevant sections.

Simply stating that squid is not working without posting the rule set you are using makes it hard to give much advice.

---

### Post by TechMansoor on 2010-08-09
> **bodhi.zazen said:**
> Privoxy has a web interface, but may take you some time to learn how to configure (I found the web interface easy to use).

You will need to configure privoxy to allow you to access the web interface, and the documentation for privoxy can seem overwhelming at first.

Hard to know what your problem is with squid without asking you to post your configuration file(s), and considering that the squid conf file is 4,000 lines or so long, you would need to post the relevant sections.

Simply stating that squid is not working without posting the rule set you are using makes it hard to give much advice.

Well I'm not working with squid directly, and maybe thats my problem. I'm allowing webmin to make entries to squid.conf file itself. Working within command lines and allowances would just confuse me more. I just installed privoxy but I'd love to really get some help on squid as webmin is a pretty centralized tool that I didn't want to get away from.

What do you suggest I could post that would possibly help me find a resolution to my squid problem?

-Again most of the sites are working, but only a few wouldn't work which I don't understand!!!! Very frustrating...

---

### Post by bodhi.zazen on 2010-08-09
To get squid working, at this point, almost certainly would involve reviewing the http requests, squid logs, and the configuration files / rule sets.

---

### Post by TechMansoor on 2010-08-09
> **bodhi.zazen said:**
> To get squid working, at this point, almost certainly would involve reviewing the http requests, squid logs, and the configuration files / rule sets.

Cool I will get on that right now..is there anything that sticks out in your mind, in which you are obviously a guru at open source proxies, that would prevent certain sites from being displayed while others are displayed?

Is there something in particular I could/should look for possibly?

thanks for all your help sir..

---

### Post by bodhi.zazen on 2010-08-09
Most of the rules are "regular expressions", it can be difficult to sort through regular expressions sometimes, depending on how they are written.

---

### Post by TechMansoor on 2010-08-10
> **bodhi.zazen said:**
> Most of the rules are "regular expressions", it can be difficult to sort through regular expressions sometimes, depending on how they are written.

This is what squid is reporting predominately:
1281452277.583      0 192.168.106.123 TCP_DENIED/403 1501 GET [http://www.methodistmd.org/](http://www.methodistmd.org/) - NONE/- text/html
1281452316.461      0 192.168.106.123 TCP_DENIED/403 1501 GET [http://www.methodistmd.org/](http://www.methodistmd.org/) - NONE/- text/html


what exactly is this saying..? I tried to deduce that 403 was the port methodistmd.org was trying to get out on so i made that a safe port and allowed it via proxy restrictions.

But that still didn't produce anything unfortunately.. :-(..

any ideas?

---

### Post by bodhi.zazen on 2010-08-10
> **TechMansoor said:**
> This is what squid is reporting predominately:
1281452277.583      0 192.168.106.123 TCP_DENIED/403 1501 GET [http://www.methodistmd.org/](http://www.methodistmd.org/) - NONE/- text/html
1281452316.461      0 192.168.106.123 TCP_DENIED/403 1501 GET [http://www.methodistmd.org/](http://www.methodistmd.org/) - NONE/- text/html


what exactly is this saying..? I tried to deduce that 403 was the port methodistmd.org was trying to get out on so i made that a safe port and allowed it via proxy restrictions.

But that still didn't produce anything unfortunately.. :-(..

any ideas?

Well, it confirms squid is blocking the site =)

We need to look at the rule set to determine why.

---

### Post by TechMansoor on 2010-08-10
> **bodhi.zazen said:**
> Well, it confirms squid is blocking the site =)

We need to look at the rule set to determine why.

:-) indeed, definitely confirms that...

I have identified the rule set within webmin in which I didn't need to tamper with such as of yet.

The rule set overrides certain restrictions set by the access control list correct? Here is an image of what I see:
[ATTACH]166084[/ATTACH]

What exactly should I be defining within the ruleset that would simply allow squid to submit to my blacklist/whitelist?

---

### Post by bodhi.zazen on 2010-08-10
Well, as has been the problem all along, I have no idea from webmin how squid is configured.

You will need to roll up your sleeves and look under the hood, at the configuration files and the rules.

See: [https://calomel.org/squid.html](https://calomel.org/squid.html)

[https://calomel.org/squid_adservers.html](https://calomel.org/squid_adservers.html)

---

### Post by TechMansoor on 2010-08-10
> **bodhi.zazen said:**
> Well, as has been the problem all along, I have no idea from webmin how squid is configured.

You will need to roll up your sleeves and look under the hood, at the configuration files and the rules.

See: [https://calomel.org/squid.html](https://calomel.org/squid.html)

[https://calomel.org/squid_adservers.html](https://calomel.org/squid_adservers.html)

Thank you so much for this reference good sir!!!! You have been a phenomenal help...I will post the results of my findings once i get it resolved this week..it has to get resolved this week!!

Thanks again...

---


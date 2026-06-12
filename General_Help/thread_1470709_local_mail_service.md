---
title: "local mail service"
date: 2010-05-03
forum: General Help
---

### Post by bobdobbs on 2010-05-03
Hi all.

I'm using ubuntu 9.10. 
I would like to test email applications on my desktop machine.

A couple of examples: I would like to test php email forms that I'm developing on the webserver that I have installed on my local machine.
Also, I'd like to test the email subsystems of web applications that I install on my desktop. 
For example, I'm testing sugarcrm on my desktop server. Sugar can send emails.

What things to I have to consider here in order to send emails from my local machine ?

---

### Post by dcstar on 2010-05-03
> **bobdobbs said:**
> Hi all.

I'm using ubuntu 9.10. 
I would like to test email applications on my desktop machine.

A couple of examples: I would like to test php email forms that I'm developing on the webserver that I have installed on my local machine.
Also, I'd like to test the email subsystems of web applications that I install on my desktop. 
For example, I'm testing sugarcrm on my desktop server. Sugar can send emails.

What things to I have to consider here in order to send emails from my local machine ?

Just install postfix.

---

### Post by bobdobbs on 2010-05-03
> **dcstar said:**
> Just install postfix.

Postfix looks like the right solution.

However, my home connection doesn't have permanent IP address or a domain name.

Can you offer advice, or point to any resources that might help me set up postfix for a local connection that relies on an ISP for mail forwarding ?

---

### Post by HermanAB on 2010-05-03
Postfix has a setting to forward to your ISP - some googling or manual reading on the postfix website will find it - usually called 'smarthost', but postfix calls it something else.

If you want a very quick and easy solution, get Citadel from citadel.org.  It installs in about 30 minutes.

---

### Post by bobdobbs on 2010-05-03
Postfix did indeed do the job.

I didn't have to read the docs too carfully (though this may cost me in the future).

I simply used my ISP's smtp server's name for the smarthost. I didn't even have to give configuration details.

I configured the settings by using 'dpkg-reconfigure postfix', and was thoughtful about guessing the configuration details.

Thanks.

---

### Post by bobdobbs on 2010-05-03
> **HermanAB said:**
> 
If you want a very quick and easy solution, get Citadel from citadel.org.  It installs in about 30 minutes.

Citidel looks really interesting and kinda cool.
But I've never really understood what the problems are that 'groupware' is supposed to solve.
Probably just because I've never worked in an environment that really had a need for a product like this.

But thanks for pointing it out to me. 
I like checking out interesting software I've never seen before.

---

### Post by teasadm on 2011-01-12
> **bobdobbs said:**
> Hi all.I'm using ubuntu 9.10. I would like to test email applications on my desktop machine.A couple of examples: I would like to test php email forms that I'm developing on the webserver that I have installed on my local machine.Also, I'd like to test the email [[COLOR=#000000]subsystems[/COLOR]](http://www.redcov.net/hu/real-estate/remarkable-expert-method-to-live-in-your-home.html) of web applications that I install on my desktop. For example, I'm testing sugarcrm on my desktop server. Sugar can send emails.What things to I have to consider here in order to send emails from my local machine ?Now I got it, It helps me out of the problem, Thanks for your effort!

---


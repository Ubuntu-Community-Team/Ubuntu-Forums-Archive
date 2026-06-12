---
title: "Ekiga not work on 10.04 (how can I use empathy for sip?)"
date: 2010-06-07
forum: General Help
---

### Post by green69 on 2010-06-07
I have recently installed ubuntu 10.04. The distro seems so much better than that I have before (8.1). Anyway after some days of trying I can say that ekiga doesn't work with 10.04. While I was perfectly able to use ekiga with 8.1, the 10.04 gives me connections problems.... it simply say says "Could not register (Failed)"

Please can anybody help me or teach me how to set a sip account (sip.12voip.com) with empathy??

Thanks

---

### Post by 666f6f on 2010-06-07
Don't know how to setup neither ekiga nor empathy but since you consider using empathy, which is an alternative, have a look at SIP Communicator. That's what I use.

---

### Post by green69 on 2010-06-07
> **666f6f said:**
> Don't know how to setup neither ekiga nor empathy but since you consider using empathy, which is an alternative, have a look at SIP Communicator. That's what I use.

The advantage of empathy is that it can group several IM protocol at once and presumably even SIP ones.

Anyway... how can I install SIP communicator? It is not in ubuntu software center nor in synaptic.

Please, anyone else know hot to set up a SIP protocol in empathy?

---

### Post by 666f6f on 2010-06-07
> **green69 said:**
> The advantage of empathy is that it can group several IM protocol at once and presumably even SIP ones.

SIP Communicator's advantage is that it has a mature SIP stack. Also, it supports multiple protocols as well but it lacks integration with the Gnome environment.

> **green69 said:**
> Anyway... how can I install SIP communicator? It is not in ubuntu software center nor in synaptic.

There are Ubuntu packages available here: [http://www.sip-communicator.org/index.php/Main/Download](http://www.sip-communicator.org/index.php/Main/Download).

---

### Post by davidmohammed on 2010-06-07
> **green69 said:**
> The advantage of empathy is that it can group several IM protocol at once and presumably even SIP ones.

Anyway... how can I install SIP communicator? It is not in ubuntu software center nor in synaptic.

Please, anyone else know hot to set up a SIP protocol in empathy?

to create a new SIP account in empathy - start empathy

from the edit menu choose accounts
 
click Add... button

from the protocol drop down choose SIP and fill in your details

Click Advanced if you are behind a proxy etc.

Hope that helps

---

### Post by green69 on 2010-06-07
> **davidmohammed said:**
> to create a new SIP account in empathy - start empathy

from the edit menu choose accounts
 
click Add... button

from the protocol drop down choose SIP and fill in your details

Click Advanced if you are behind a proxy etc.

Hope that helps

I've already tried that but it gives me network error and I don't know why.
I writed 
username: <my_user_name>@sip.12voip.com     (12voip is the provider)
password: <my_password>

It doesn't work and in ekiga neither. In ubuntu 8.1 with an earlier ekiga version these specification were working...

---

### Post by davidmohammed on 2010-06-07
copied from another thread...

in a terminal install as follows

sudo apt-get install telepathy-sofiasip libtelepathy-farsight0 python-tpfarsight

then reboot and try again adding your SIP account

---

### Post by green69 on 2010-06-07
> **davidmohammed said:**
> copied from another thread...

in a terminal install as follows

sudo apt-get install telepathy-sofiasip libtelepathy-farsight0 python-tpfarsight

then reboot and try again adding your SIP account

Yes. I've already seen that thread. I've dono it but without success. Thank you anyway.

Any other suggestion?

---


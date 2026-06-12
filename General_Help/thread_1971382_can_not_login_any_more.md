---
title: "can not login any more"
date: 2012-05-02
forum: General Help
---

### Post by ottosykora on 2012-05-02
sorry, probably was asked many times before, but brings me to kind of panic now:

Today, once again linux decided it has to do fschk befor it starts.
OK, I left it do, but now I can not start it any more.

I come up to the login screen, enter my password, but then screen goes black and the login screen comes back. each time with the drum sound etc.

And yes, I am entering the correct password and yes I did check if the caps lock os off etc. 
All seems to work correctly, as when I enter deliberately wrong password, I get answer that password is wrong.
When entering correct password, no comment is given back just the login screen comes back.

Any advise as how to get ubuntu back?

---

### Post by oboedad55 on 2012-05-02
> **ottosykora said:**
> sorry, probably was asked many times before, but brings me to kind of panic now:

Today, once again linux decided it has to do fschk befor it starts.
OK, I left it do, but now I can not start it any more.

I come up to the login screen, enter my password, but then screen goes black and the login screen comes back. each time with the drum sound etc.

And yes, I am entering the correct password and yes I did check if the caps lock os off etc. 
All seems to work correctly, as when I enter deliberately wrong password, I get answer that password is wrong.
When entering correct password, no comment is given back just the login screen comes back.

Any advise as how to get ubuntu back?

Hi, need some more info. Ubuntu version, hardware, etc. What else you may have done? Can you login as guest?

---

### Post by ottosykora on 2012-05-02
OH, sorry to bother, yes I was in kind of panic, as just now I have no big time to search for all problems.

The problem is cured. It is on ubuntu 11.04.

Beside the linux wanted to make fschk, i added a line which has not much to do, but it is in the stupid gpg-agent which ubuntu does automatically deliver to make the system less safe.
It does cache the passphrase of the gpg for about 10 minutes and I attempted to switch off that thing. Unfortunately it seems not possible to enter anything into the conf file of that gpg-agent at all, system will simply not start up.

huuh, so all back to normal again, my adrenalin level normalizing.

---


---
title: "Problem with likewise-open"
date: 2010-01-21
forum: General Help
---

### Post by snake_eyes_ on 2010-01-21
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

I am completely lost on how to get likewise-open to work. 

from everything I've read it should work out of the box


I ran ```
apt-get install likewise-open
```then..

```
domainjoin-cli join it.awesome.com Administrator
```and it said "Success"
I rebooted like it said. 

but I am unable to login as an active directory user.

resolv.conf is set to use my AD server as dns.

MY AD DC machine is:  ```
adcwin1.it.awesome.com
```this is what my user is called in AD:

What format should I be using to log in?  DOMAIN\user ?:confused:

```
User logon name: theuser@it.awesome.com
```Let me know what other information you might need... and thanks in advance.

---


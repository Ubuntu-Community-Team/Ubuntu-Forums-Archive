---
title: "Ubuntu 10.04 Likewise works well but it is very slow"
date: 2010-09-01
forum: General Help
---

### Post by QwErTy_LoGiC on 2010-09-01
Hello all,

I am having an issue with likewise-open5 on Ubuntu 10.04 64bit. 

Everything works but it is really slow. At login, after entering the login name, the password prompt appears 5-15 seconds later.

Once it appears and the password is entered, then zap, the login is instantaneous. 

I am just having a hard time figuring why the password prompt is so slow to appear.

Whenever I log in with a local account, everything is snappy.

I'm a bit clueless...

Thanks for any input!

---

### Post by QwErTy_LoGiC on 2010-09-01
OK, I manage to do some further testing and here is what I found

I tried logging on two different ways:

DOMAIN NETBIOS NAME\account = slow
DOMAIN FQDN\account         = fast

So this seems to be related to the resolution of the netbios domain name.

Unfortunately, I don't have a clue as to where I should look to fix this.

Anyone?

---


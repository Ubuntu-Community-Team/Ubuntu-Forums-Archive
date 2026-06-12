---
title: "Glibc_2.4"
date: 2006-06-25
forum: General Help
---

### Post by hubin on 2006-06-25
Hi, forum guys,

I hope this the right place to ask for assistance. I just installed Ubuntu 6.06 and found it was difficult to install GLIBC_2.4, which is required for a program called ECELL. Can anyone show me how to install GLIBC_2.4? Thanks.

....
ImportError: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/python2.4/site-packages/ecell/_ecs.so)


Regards,
Bin

---

### Post by JoWilly on 2006-06-25
[quote=hubin]Hi, forum guys,

I hope this the right place to ask for assistance. I just installed Ubuntu 6.06 and found it was difficult to install GLIBC_2.4, which is required for a program called ECELL. Can anyone show me how to install GLIBC_2.4? Thanks.

....
ImportError: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/python2.4/site-packages/ecell/_ecs.so)


Regards,
Bin[/quote] 
Just get it from the edgy repos (easiest is to temporarily replace dapper with edgy in /etc/apt/sources.list, and then revert back).

I have installed glibc 2.4 and gcc 4.1.1 this way 1 week ago, it works fine, so it seems to be binary compatible.

---

### Post by hubin on 2006-07-04
[QUOTE=JoWilly]Just get it from the edgy repos (easiest is to temporarily replace dapper with edgy in /etc/apt/sources.list, and then revert back).

I have installed glibc 2.4 and gcc 4.1.1 this way 1 week ago, it works fine, so it seems to be binary compatible.[/QUOTE]

Thank you so much. I could install glibc although ECELL cannot work...

---

### Post by secretspicy15 on 2008-05-18
hooray! that worked like a charm, thanks!

(old post, i know, but i'm using an old box running dapper as a server and have been adding programs -- one of which required glibc 2.4...)

---


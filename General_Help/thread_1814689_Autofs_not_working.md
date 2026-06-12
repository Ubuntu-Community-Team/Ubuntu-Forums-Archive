---
title: "Autofs not working"
date: 2011-07-29
forum: General Help
---

### Post by venkatachar on 2011-07-29
I am having entry in auto.master as 

> /de_autofs auto_adefs

and in auto_adefs as below.

> de_genfc -ro everest:/vol/rwssyncvol/&
de_gen2fc -ro everest:/vol/rws2syncvol/&


I restarted the autofs service, but i am unable to cd into /de_autofs/de_genfc.

But i am able to ping everest and also i am able to browse the volume using /net/everest/vol

Am i missing any configuration

---

### Post by papibe on 2011-07-30
I would start testing from the ground up. First, I would check if you can mount the shares manually.

First stop the autofs service:
```
$ sudo service autofs stop
```
Then try:
```
$ sudo mount -t nfs -o ro everest:/vol/rwssyncvol/ /de_genfc
```
Regards.

---


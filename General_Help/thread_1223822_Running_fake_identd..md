---
title: "Running fake identd."
date: 2009-07-26
forum: General Help
---

### Post by harry71194 on 2009-07-26
Edit: hmm, ./identd USER-I-WANT-AS-IDENT worked.





I dunno if this is the correct section, if not, sorry.

I am running [http://freshmeat.net/projects/fakeidentd/](http://freshmeat.net/projects/fakeidentd/)
Fake Identd.
It works amazing. It actually works for me, unline oidentd.
Only problem / dislike: it runs as user `nobody', even through I run it via sudo, or root. ps aux | grep ident gives me:
> h@ubuntu:~$ sudo ps aux | grep ident
nobody    3401  0.0  0.0   2016   336 ?        S<s  16:42   0:00 ./identd
h         3486  0.0  0.1   3336   792 pts/0    S<+  16:52   0:00 grep ident
So, if anyone has any way I can run the ./identd command on "h", or some other random account (nobody as an ident on IRC != good. lots of rooms ban this ident), I would be very happy ^_^
sudo ./identd, and sudo -i (and then ./identd'ing) did not work.

Thanks.

---

### Post by dlmarti on 2009-07-26
Then the IRC server is mis-configured, ident is supposed to run as nobody.  Its a security measure.

---


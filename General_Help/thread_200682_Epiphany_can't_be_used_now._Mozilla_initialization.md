---
title: "Epiphany can't be used now. Mozilla initialization failed"
date: 2006-06-20
forum: General Help
---

### Post by matrooswolf on 2006-06-20
Hi, 

I just installed Epiphany, when trying it out,  I get this error message:

> Epiphany can't be used now. Mozilla initialization failed
(translated from dutch)

Sorry if this has been asked before, but I searched the forum with this error message and didn't find anything.

(my system: athlon 3000, 1GB, using Xgl (with metacity at the moment), everything updated till today)

Any ideas?

---

### Post by matrooswolf on 2006-06-21
Any Epiphany Lovers in the house?

---

### Post by scxtt on 2006-06-21
i use epiphany every now and again - but the only other browser i have installed is (the default) firefox ... do you have mozilla installed?

---

### Post by matrooswolf on 2006-06-21
Thanks for the tip.  Epiphany didn't complain about anything when I installed it, so I thought all dependecies were resolved.  I'll try it.

So I did, but it doesn't make any difference.  I still get the same error.

It is not a matter of life and death.  I use Firefox (and am very happy with it).  I just like to try things out.  

Strange though.  Firefox works, Galeon, Opera, Mozilla-browser, ...  Only Epiphany doesn't

---

### Post by scxtt on 2006-06-21
i meant it more in a way of mozilla is conflicting w/ epiphany (i don't have mozilla installed @ all) since epiphany/firefox/mozilla are all 'gecko' browsers ... i was thinking something similar to 'hey, an instance of mozilla is running already' instead of adding another gecko browser to the mix ...

almost sounds like a dependency issue, upgrade or fresh install?

---

### Post by matrooswolf on 2006-06-21
Thanks.  I was thinking the same, but apparently it is a conflict between firefox and epiphany.

I just found that there was a bug filed for this:
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/30791](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/30791)

> As of the latest "Dapper" install, Epiphany does not run. It has been working
before but recent changes stopped it. This is running with Epiphany v
0.5.1-1build2 and Firefox v 1.4.99+1.5rc3.dfsg-1ubuntu3.

"""Epiphany can't be used now. Mozilla initialization failed."""

Firefox itself runs fine, so I'm guessing it's an API mismatch or something. No
extra information is given running from the command line, just the same dialog
message.

But it hasn't been resolved yet.  Status is: needs more info.

There's maybe a solution in there, but as it is not a matter of life and death, I am going to abandon Epiphany for now ...

For the record:
epiphany 2.14.2.1-0ubuntu1
firefox 1.5.dfsg+1.5.0.4-0ubuntu6.06

---

### Post by scxtt on 2006-06-21
odd, they both work fine for me ...

---


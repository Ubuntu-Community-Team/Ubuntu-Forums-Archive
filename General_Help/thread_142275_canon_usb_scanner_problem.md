---
title: "canon usb scanner problem"
date: 2006-03-10
forum: General Help
---

### Post by nanotube on 2006-03-10
trying to get my canoscan fb620u USB scanner to work with xsane.

so... when i run sane-find-scanner, i get the following output:

```
  found USB scanner (vendor=0x04a9 [Canon], product=0x2202 [Scanner ]) at libusb:004:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
```

but when i try "scanimage -L" i get:

```
 No scanners were identified. If you were expecting something different, check that the scanner is plugged in, turned on and detected by the sane-find-scanner tool (if appropriate). Please read the documentation which came with this software (README, FAQ, manpages).
```

the scanner device is present in /proc/bus/usb/004/003, but there is no /dev/scanner or any similar devices.

my scanner is canoscan FB620U, and i know it is not specifically supported, but i wanted to try it with the canon630U backend just to see if i could make it work - but scanimage completely refuses to play with it. 

So, does anyone have any advice on how to force scanimage to at least try using that scanner?

i'd appreciate any help. thanks! :)

---

### Post by Sendervictorius on 2006-03-10
The canoscan fb620u is not supported by the current Canon backend.
Checkout this site:
[http://www.fenypont.hu/jecs/SANE%20Supported%20Scanners%20-%20Canon.htm](http://www.fenypont.hu/jecs/SANE%20Supported%20Scanners%20-%20Canon.htm)

---

### Post by nanotube on 2006-03-11
hey sendervictorious,

i know it is not supported. i was just wondering if it is possible to force the canon630u backend to at least attempt to do something.  cuz i mean, how different can fb620u be from fb630u, right? :)

oh and btw, that link you sent is very informative, but the site is really slow. a faster mirror is on the original sane site, here: [http://www.sane-project.org/cgi-bin/driver.pl](http://www.sane-project.org/cgi-bin/driver.pl)
(just posting it here for possible future reference by someone else).

so... got any ideas? :)

---

### Post by nanotube on 2006-03-15
bump? :)

---

### Post by gertjan_hofman on 2007-08-09
I have the same problem (i.e. sane-find-scanner is ok, xsane is not) on my Agfa scanner....which used to work fine under dapper (and possibly edgy). So I am not sure if it's just that your scanner is not supported or that this is related to other USB scanner bugs reported for feisty

---


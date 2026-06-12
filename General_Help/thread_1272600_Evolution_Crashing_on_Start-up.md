---
title: "Evolution Crashing on Start-up"
date: 2009-09-22
forum: General Help
---

### Post by thepossiblehuman on 2009-09-22
Whenever I open evolution I get this error in the syslog and evolution crashes within 2 seconds:

kernel: [ 2145.324747] evolution[7182]: segfault at 0 ip b6b2f3d7 sp b24fd174 error 4 in libglib-2.0.so.0.2000.1[b6ad2000+b6000]


I tried reinstalling the libglib libraries, but I get the same error.  

Unfortunately, I'm used to wrassling with Evolution and Exchange accounts.  If you don't have a fix, could you let me know how to launch the Configuration Wizard from terminal, so I can at least rip the account out again and start from scratch?  Thanks!

---

### Post by thepossiblehuman on 2009-09-22
I just tried launching from terminal, and here is the output:

```

** (evolution:9240): DEBUG: mailto URL command: evolution %s
** (evolution:9240): DEBUG: mailto URL program: evolution

(evolution:9240): evolution-shell-WARNING **: Invalid URI: %s

(evolution:9240): camel-exchange-provider-WARNING **: Unable to load Exchage summary for folder personal: no such table: personal


(evolution:9240): GLib-CRITICAL **: g_base64_encode: assertion `len > 0' failed
Segmentation fault 
```

---

### Post by thepossiblehuman on 2009-09-22
So I just ran a complete removal of evolution, and then reinstalled.  I'm still getting the error.

---

### Post by thepossiblehuman on 2009-09-22
I basically ripped out everything I could and got it working.  ;)

---

### Post by lajfi on 2009-10-19
you say you "ripped out everything you could"...
could you be more specific?

i am getting this:
 evolution[5848]: segfault at 0 ip b6adc3d7 sp b1afd174 error 4 in libglib-2.0.so.0.2000.1[b6a7f000+b6000]

---


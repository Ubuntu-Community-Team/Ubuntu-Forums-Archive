---
title: "About X and NVIDIA graphics card"
date: 2009-09-12
forum: General Help
---

### Post by hihihi100 on 2009-09-12
Hi there:

         Following the instructions found at this forum, in order to install a NVIDIA graphics card (185.18.36) I exited X, and pasted the codes: this is what happened next:

Stopping firestarter firewall, reloading postfix configuration
Stopping firestarter firewall, reloading postfix configuration
Stopping firestarter firewall, reloading postfix configuration
Stopping firestarter firewall, reloading postfix configuration
Stopping firestarter firewall, reloading postfix configuration
Stopping firestarter firewall, reloading postfix configuration
Stopping firestarter firewall, reloading postfix configuration
Stopping firestarter firewall, reloading postfix configuration

          (Yes, 8 times, and then)

reloading common

unix printing sustem: cupsd

* reloading system log daemon (no problems with this one)
* stopping firestarter firewall (no problems with this one)
* reloading postfix configuration (no problems with this one)
* reloading system log daemon (PROBLEMS: the screen stops there, it gets stucked, i cannot use "exit", after waiting for 25 minutes, i just rebooted the whole computer)

           Is this normal?
     
           Good news is that after the reboot I was able to fully install the graphics card driver, bad news is after I turn on the computer, an error message appears, saying that i have to run it in low graphics mode, and that I may need to update and then:

(EE) NVIDIA(0): failed to initialize the NVIDIA kernel module, see the
(EE) NVIDIA(0): system kernel log for additional error messages
(EE) NVIDIA(0): consult the NVIDIA README
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration

          So i accept (that I have to run the computer on low graphics mode), and:

There appears to be n X server running on display: 0 Should another display number by (sic) tried?

           I say yes, to avoid the repetition of the previous step, and:

The server was started on display: 1

           Any tips please?

---


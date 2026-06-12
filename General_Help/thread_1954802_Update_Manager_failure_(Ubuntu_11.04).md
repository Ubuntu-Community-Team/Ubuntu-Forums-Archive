---
title: "Update Manager failure (Ubuntu 11.04)"
date: 2012-04-08
forum: General Help
---

### Post by jla1947 on 2012-04-08
Update Manager tells me I have 145 updates pending. I click on install, provide password at prompt, applying changes screen pops up, and then an error screen appears with the message - Failed to download package files, check your internet connection.
The internet connection is fine; I can browse the internet with Firefox no problem. Any help or advise is welcome. Thanks :)

---

### Post by cody1233 on 2012-04-08
Any proxy server settings on?

---

### Post by jla1947 on 2012-04-08
> **cody1233 said:**
> Any proxy server settings on?

No. This machine is one of three that I own and is the only one having the problem. the others have Ubuntu 11.10. There has always been one version or another of Ubuntu on this machine for the past four years, and this is the first time I've ever had a problem.

---

### Post by hughr2005 on 2012-04-08
check your network settings at /etc/networking/interfaces. I had a similar problem a few days ago, and this helped. Try setting a static IP.

---

### Post by jla1947 on 2012-04-08
Believe I solved the problem. Booted the machine to the command line and  did an apt-get clean. Then I ran an apt-get update which errors out. At that point I didn't know exactly what to do (about the errors) so I simply rebooted the system fully to the GUI and opened and ran Update Manager. For whatever reason it is now working as it should and is presently updateing the system normally. Thanks for all who volunteered their help.

---

### Post by fast_ian on 2012-06-20
> **jla1947 said:**
> Believe I solved the problem. Booted the machine to the command line and  did an apt-get clean. Then I ran an apt-get update which errors out.

Thanks for this! My 11.04 machine did exactly the same when trying to install a new package - Told me to "check my internet connection", which is fine.

FWIW, I didn't bother rebooting - Just "sudo apt-get clean" followed by "sudo apt-get update" in a terminal - No errors but package manager is all alive again and working as advertised :)

Cheers,
Ian

---


---
title: "Firestarter Internet Connection sharing"
date: 2011-05-23
forum: General Help
---

### Post by steveodeevo on 2011-05-23
I noticed this weekend that my firewall box running firestarter started behaving a bit sketchy, which in light of the network issues I have had since updating to natty and having to delete and reconfigure the network is probably not all that unexpected.

On further reading about firestarter I found that it seems to dislike changes to the network configurations which seem to cause this behaviour, and also it is no longer being developed and so is probably not the best solution to share internet from anymore.

At the time I wanted to get online quickly, so my solution was to boot an win2K virtual box vhd I had kicking around with one virtual network set to NAT and the other pointed at my internal network, and then just shared the internet using that.

Whilst this works great for playing online games etc, my real question is how secure is this?  It is sat behind the linux box still as its using NAT, and I have ufw installed on that so I am thinking it should still be behind the firewall, but thought I would ask on here and see what people think.

---

### Post by steveodeevo on 2011-05-26
I took the insanity a step further today, when I decided to ditch the win2k ICS vhd and go for an ubuntu 10.04 vhd running firestarter instead.

My reasoning (if it can be called that) is I can't wipe the PC its on as it runs a testing webserver and other important things, and as it seems to have completely killed firestarter somehow since the update and I don't have time to re-install, I figure run a ubuntu 10.04 vhd which I know works with firestarter on it which for now would still be secure, if a kind of strange fix to my problems.

---


---
title: "Disabling irq #17 and adding boot option"
date: 2012-04-07
forum: General Help
---

### Post by samopn on 2012-04-07
Hi
When I boot up Ubuntu 10.4 I get a message "disabling IRQ #17". Once up everything seems to work without problems.

The boot log says that I should boot with the irqpoll option but I don't know how to do this.  I'm fairly new to Ubuntu

Can someone please point me to how I set this boot option.

Thanks

Sam

---

### Post by dino99 on 2012-04-07
hi Sam,

right now, add irqpoll on the line that have "quiet splash":

sudo gedit /etc/default/grub

change that line to get : quiet splash irqpoll , then save and close gedit. Then you need to update grub again:

sudo update-grub

but you might report that issue to get a fix, into a terminal, run:

ubuntu-bug linux

you'll be asked to open and account on Launchpad, then describe this issue a little.

note: check the irq settings into the bios, maybe you can change something there.

---

### Post by aaronLund on 2012-11-29
subscriibing

---


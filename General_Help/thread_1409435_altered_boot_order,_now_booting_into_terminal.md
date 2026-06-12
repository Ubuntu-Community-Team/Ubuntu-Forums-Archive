---
title: "altered boot order, now booting into terminal"
date: 2010-02-17
forum: General Help
---

### Post by tlxreed on 2010-02-17
Hi all,

Sorry if my language is a bit inexact. Ubuntu 9 has run so well I haven't bothered to learn much about it.

Anyhoos, I wanted to change the default order that shows up in the BIOS of my laptop so that Ubuntu was the default instead of Vista. I'm doing a dual boot setup.

I found a help file via Google on Ubuntu.com's help section. It advised to use a terminal command to open a particular file and change a number from 0 to 1.

Having done so, when I boot in Ubuntu I see the following error during boot:
cannot access etc/udev/rules.d/z80_user.rules

I'm thinking perhaps the permissions are now wrong on this file. The boot continues and opens up a recovery menu. Once through that as a normal boot, for example, I end up in the terminal, not in the GUI bootup.

Any suggestions how to set things right would be appreciated.

---

### Post by tom4everitt on 2010-02-17
Two questions, answering one will pretty much answer both:

1. What was that file you were editing. Was it /boot/grub/grub.cfg? /boot/grub/menu.lst? /etc/defaults/grub? Or just post the link to the guide you were using...

2. Are you using ubuntu 9.04 or ubuntu 9.10. It makes a difference :)

---

### Post by tlxreed on 2010-02-18
Well, I googled the topic some more and found some relevant posts. I am on Ubuntu 9.10.

I logged into the terminal session, started nano, opened grub.lst and set the default OS from 1 back to 0 the way it was before.

Back in service, booting back into the GUI.

:p

---


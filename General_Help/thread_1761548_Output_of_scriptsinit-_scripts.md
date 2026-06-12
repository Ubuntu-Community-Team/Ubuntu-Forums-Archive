---
title: "Output of /scripts/init-* scripts"
date: 2011-05-18
forum: General Help
---

### Post by XanTrax on 2011-05-18
Hi,

My *nix experience is pretty solid but I have noticed as Ubuntu  progresses and attempts to become more mainstream, things like console output at boot, debug output, and verbose messaging is falling by the wayside and becoming harder and harder to track down on how to enable.

That being said, with the implementation of the latest grub, it took me a little while to figure out that /etc/default/grub was the file I had to edit to turn on boot messages (I am accustomed to the single /boot/grub/menu.lst file)

So, now I am stuck on the /scripts/init-bottom and /scripts/init-top scripts.  I would like to see the output of these when I boot (I like to know if an error occurred at boot) but it appears that there is no intuitive way to just "turn on" the output for these.

Does anyone know where I can enable the stdout/stderr from these?

Thank you


EDIT: I was able to get more verbose output by turning on verbose output in /etc/default/console-setup -- still looking at the previously mentioned output of /scripts/* -- I believe its grub related...

---


---
title: "Help X dead todayon Jaunty"
date: 2009-10-22
forum: General Help
---

### Post by tpl on 2009-10-22
Running Jaunty  Kernel 15 with an ATI Radeon X800 and a flat screen. The PC also has Intel on board video

Yesterday and before all was well.
This am start up machine and thevideo shows as if the timing/resolution was incorrect. Copies of the word UBUNTU across the screen and a sort of row or two of red pixels at the top.
No mouse pointer, no keyboard activity possible

OS is working as I can start my Karmic machine and connect to shares on the Jaunty machine.

1st try. CHange monitor and reboot no change
2nd try  Remove ATI card and plug monitor into the Intel VGA port.  Different display now blocks of white over 2/3 screen.

Boot from the last "recovery version " I have, Kernel 13   try DPKG to do whatever it does with mending packages. Says it can install Kernel 16  but then says it cannot get the packages ( Network appears to be up as I can ping remote addresses)

Everything runs in text mode. If I restart Samba I can see my home directory etc from my Karmic machine.

However if I try to copy files from the machine with non-working video to the Karmic machine  I get permission erros.

So. Best solution is to get X working on the Jaunty machine
  2nd best is to be able to copy a wholepile of files across to the karmic machine and then I can continu working.

Please someoen give me an idea of what to try next.

Xorg.conf looks normal

---


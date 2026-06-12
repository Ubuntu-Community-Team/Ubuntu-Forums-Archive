---
title: "Connect 2 PC via null modem &amp; Serial Console Use"
date: 2009-06-26
forum: General Help
---

### Post by HazByn on 2009-06-26
hi all,

i have 2 pc connected via null modem cable (serial cable).i configured these pc using this method. [http://www.securitypronews.com/articles/operatingsystems/spn-22-20030722HowtoConnectTwoPCviaSLIPUsingANullModemCableonLinux.html]("http://www.securitypronews.com/articles/operatingsystems/spn-22-20030722HowtoConnectTwoPCviaSLIPUsingANullModemCableonLinux.html") then i can ping these pc's and i want to reboot / suspend / hibernate the pc but dont know how..then i try [http://www.debuntu.org/how-to-set-up-a-serial-console-on-ubuntu]("http://www.debuntu.org/how-to-set-up-a-serial-console-on-ubuntu") and finally i'm totally lost..so could u guys show me the correct path..im lost.thanks in advance.

---

### Post by dcstar on 2009-06-26
> **HazByn said:**
> hi all,

i have 2 pc connected via null modem cable (serial cable).i configured these pc using this method. [http://www.securitypronews.com/articles/operatingsystems/spn-22-20030722HowtoConnectTwoPCviaSLIPUsingANullModemCableonLinux.html]("http://www.securitypronews.com/articles/operatingsystems/spn-22-20030722HowtoConnectTwoPCviaSLIPUsingANullModemCableonLinux.html") then i can ping these pc's and i want to reboot / suspend / hibernate the pc but dont know how..then i try [http://www.debuntu.org/how-to-set-up-a-serial-console-on-ubuntu]("http://www.debuntu.org/how-to-set-up-a-serial-console-on-ubuntu") and finally i'm totally lost..so could u guys show me the correct path..im lost.thanks in advance.

Unless these PCs both have no Ethernet cards, why are you bothering to use serial connections?

---

### Post by HazByn on 2009-06-28
Hi Dcstar

i just wanted to know more about linux especially ubuntu.I wanted to take an exam about hardware thingy.Could u help me on this.TIA.

---

### Post by namaku0 on 2009-06-29
Why wouldn't you use SSH to connect to the target PC
and then do anything from there (including reboot &
shutdown)?

---

### Post by t4thfavor on 2009-06-29
I have done this for no aparent reason as well, I setup console rediretion in the bios the first time, and then set it as an option in the kernel the second. There is lots of info on serial consoles. Though I still prefer ssh, unless I am practicing networking...

specifically which part of the above tutoriials are you lost on?

---

### Post by HazByn on 2009-06-29
hi all,:KS

i setup 2 machine.A is server and B is client.i tried connect via SLIP (in the tutorial) then when i tried to **ssh user@ip of B** i got connection refused.then i tried minicom (install in A) and i dont know how to force shutdown / reboot / suspend on B (client).

then i tried the 2nd tutorial and my ubuntu 9.04 got some error when boot up.so how do i suspend/boot/shutdown from A to B using via null modem cable.TIA.:confused:

---


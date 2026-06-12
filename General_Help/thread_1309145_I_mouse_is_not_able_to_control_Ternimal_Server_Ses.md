---
title: "I mouse is not able to control Ternimal Server Session."
date: 2009-11-01
forum: General Help
---

### Post by Rex-Hsu on 2009-11-01
Hi,
I have a desktop that using Windows 7 Professional.
I had already enable the Terminal Service on that desktop machine.
But when I try to use Ubuntu 9.10 to connect the machine.
An issue happen...My cannot control the machine with my TouchPad on Laptop.
But the keyboard still worked correctly. Does any have idea about this?

My Laptop is SONY VAIO FW45.

Thanks
Rex

---

### Post by simpleeddie on 2009-11-01
sorry if i insult your english, please take no offence, but I'm not quite sure I understand what you mean. Any chance you could go into a bit more detail?

What exactly are you trying to do? Are you trying to remotely access the windows 7 machine using you laptop with ubuntu?

or does your ubuntu mouse/touchpad not work at all, offline and online.

---

### Post by Rex-Hsu on 2009-11-01
Sorry for my english is not so good.
I means I cannot control my mouse cursor in a remote desktop session.

Here is the repro step:
1. Enable Terminal Service on Windows 7

2. Connect the remote desktop from Ubuntu 9.10 via "Terminal Server Client" with RDP protocol.
[COLOR=Red][B]Result: I cannot use mouse in remote desktop session. It got no response.
            Note: I just try with RDPv5, this issue still repro.
[/B][/COLOR]
3. Use keyboard to terminate the remote desktop session.
**[COLOR=Blue]Result: Mouse work again on my local desktop.[/COLOR]**

Thanks
Rex

---


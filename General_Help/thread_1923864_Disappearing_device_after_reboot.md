---
title: "Disappearing device after reboot"
date: 2012-02-11
forum: General Help
---

### Post by AimlessDave on 2012-02-11
Hi - I've been trying to configure a Mythbuntu box. I've had several problems, some ongoing, some now solved, but this one is baffling me.

I'm using a Hauppauge Win-TV Nova T Stick. I've been reading all sorts of things on how to get the IR working, and nothing seemed to help. However, it seems that moving the device to a new USB port and rebooting causes the IR to work - until the next reboot, when it is dead again. Even if I do nothing but load up and reboot, the remote will not work next time. IRW goes from showing keystrokes, to showing nothing.

The tuner itself is unaffected, and works whichever USB socket the stick is put into. I've used cat /proc/bus/input/devices to check the input number, which remains unchanged.

Any thoughts?

Cheers,

-dave

edit: it seems that if I pull the stick out whilst the IR is working, shutdown, and replace it into the same socket, it will work next time. It's only if it shuts down with the stick in a given socket that will stop it from working next time.

---


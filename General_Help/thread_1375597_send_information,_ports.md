---
title: "send information, ports"
date: 2010-01-08
forum: General Help
---

### Post by cucuru on 2010-01-08
hello, I'm very confused with what I have to do. I want to send some information using an arbitrary port in my computer (5544), how can I do that?

Does it exist any device configurated? I mean, I know how to use the serial port, it is dev/tty2.

If it doesnt exist, do you know how can I do it?

Thank you. Regards

---

### Post by Lars Noodén on 2010-01-08
You have to have something listenting at that port.

You can use [netcat](http://linux.die.net/man/1/nc) to send or receive data on a specific port.

---


---
title: "Is there any way to make X use tty8?"
date: 2011-05-23
forum: General Help
---

### Post by willsomebody on 2011-05-23
Hello,

I am a somewhat experienced linux user, but have never dealt with virtual terminals. I have been experiencing this bug [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/765136](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/765136) on my laptop and I have noticed that after X crashes, it tends to not crash again until I reboot. People more knowledgeable than I have noticed that GDM comes back up on tty8 after a crash. My question is then, can I make GDM start on tty8 at every boot/login?

Thanks in advance,
will

---

### Post by TeoBigusGeekus on 2011-05-23
[This]("http://www.linuxquestions.org/questions/linux-general-1/open-second-gui-on-tty8-451239/") perhaps?

---

### Post by conradin on 2011-05-23
I think its just coincidence gdm comes back up on tty8 as its the next logical path after its default on tty7.

what probably happens is tty7 crashes, hangs, goes zombie, or fails some other way. That then makes that terminal session useless, another session is launched to kill the crashed session, effectively starting the X-server , gdm, and what ever it was crashing on tty7. then the X-server is restarted and it works. 

--Thats just a basic overview of what I think is happening. I think if you defaulted to tty8 you would have the same problem loading and end up at tty9.

A method I would consider is boot to a lower run-level, then call login, and X-server initializations. Im not sure where the hang is taking place, but re-initializing the x-server seems to work.

---


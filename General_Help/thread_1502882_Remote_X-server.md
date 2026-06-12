---
title: "Remote X-server?"
date: 2010-06-06
forum: General Help
---

### Post by s.v.z on 2010-06-06
Hi everyone. I`ve got an ATX PC with no monitor and no OS and a laptop with Lucid. I`ve been told that it is possible to install Linux on PC and start its X-server from the laptop so that I can see what`s going on there. If this is possible, can you help me with it? Actually, I`ve got no idea about what I should do =) **Lets assume I can get a monitor for some time to configure the PC.**

---

### Post by spiky001 on 2010-06-06
yes this is possible I have a headless pc all controlled via laptop, you will need a monitor to set it up tho

---

### Post by s.v.z on 2010-06-06
oops =)

---

### Post by CharlesA on 2010-06-06
You can forward X over SSH, or just use VNC to view an X session.

Is that what you are asking about?

---

### Post by lisati on 2010-06-06
Threads merged

---

### Post by BoneKracker on 2010-06-06
First you've got to get the OS installed on there, and that's a separate challenge without a monitor.

---

### Post by s.v.z on 2010-06-06
Lets assume I can get a monitor for some time, to configure the PC. What I don`t know is how to "forward X over SSH" or anything else..

One more thing: I want to be able to see fullscreen applications as well (I know that Radmin has some trouble with it) in case I want to play games or something..

---

### Post by spiky001 on 2010-06-06
1st install os then you will need to set up remote desktop (vnc) that will allow you to view and control from remote location via network. Once that is done you can proceed further with other software depneding on what you are using pc for

---

### Post by s.v.z on 2010-06-06
Probably this is not the right thread to ask, but how shall I setup a PC to PC Ethernet connection? Guess, it won't work if I just stick the cord into both of them =)

---

### Post by spiky001 on 2010-06-06
yes that works

---

### Post by s.v.z on 2010-06-06
Ok, thanks. I'll give it a try as soon as I can lay my hands on a monitor =) Guess, I should mark the thread solved for now.

---

### Post by BoneKracker on 2010-06-06
[http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html](http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html)

[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

[http://tuxtraining.com/2008/10/27/forwarding-x-over-ssh-in-3-simple-steps](http://tuxtraining.com/2008/10/27/forwarding-x-over-ssh-in-3-simple-steps)

[http://www.ssh.com/support/documentation/online/ssh/adminguide/32/X11_Forwarding.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/32/X11_Forwarding.html)

---

### Post by BoneKracker on 2010-06-06
> **spiky001 said:**
> yes that works

Does it?  I always thought you needed a crossover cable.

Every day's a good day you learn something new.

---

### Post by spiky001 on 2010-06-06
well mine worked I did think that as well but it works fine My windows needs a cross over

---

### Post by s.v.z on 2010-06-06
Thanks for the links.

The question was not about the cable, but whether I need to configure anything to make it work.

---

### Post by spiky001 on 2010-06-06
you need to set network manager to share with other pc's set this in wired connection ip4 settings drop down list shared with other pc

---

### Post by s.v.z on 2010-06-06
Ok, thanks for help. I think I'll get back to it when I have a monitor.

---


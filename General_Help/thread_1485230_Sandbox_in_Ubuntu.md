---
title: "Sandbox in Ubuntu?"
date: 2010-05-16
forum: General Help
---

### Post by dementic on 2010-05-16
Hello, 

I would like to know if it's possible to execute some programs in a "sandbox" a protected space that the program can not escape. That means the program cannot directly interact with the system (leaves no traces outside the sandbox)

Like [www.sandboxie.com](www.sandboxie.com) on Windows. It's really useful

---

### Post by John Bean on 2010-05-16
I use virtualbox and an appropriate installed OS to run dubious programs. Take snapshot / run program / revert snapshot / job done.

---

### Post by dementic on 2010-05-16
Thank you, I thought about it but you have to install a second OS and start it each time. The sandbox is just a layer between the system and the program which filter the commands asked by the program. It's execution is really fast.

But if there are no other ways to do that, I will use VirtualBox.

---

### Post by John Bean on 2010-05-16
> **dementic said:**
> Thank you, I thought about it but you have to install a second OS and start it each time.

True, but it doesn't have to be the same as your main OS nor does it have to be started (ie booted)  each time - you can not only take a snapshot of a running system at any time but can also save its current state when you exit, restarting exactly where it left off next time you run it. I never reboot any of my VMs.

---

### Post by dementic on 2010-05-16
Ok, thanks I will give it a try with WinXP

---

### Post by ibuclaw on 2010-05-16
If you are looking for virtual technologies, OpenVZ or LXC are kinda along the lines of what you are hinting.

Otherwise, Apparmor - which is installed by default in Ubuntu - should be good enough to sandbox an application (prevent it from writing/reading to the system where you don't explicitly allow it to).

Regards
Iain

---

### Post by dementic on 2010-05-17
Thank you, I will investigate how to run apparmor properly (it seems pretty complicated)

---

### Post by ibuclaw on 2010-05-17
If you join #ubuntu-beginners on Freenode IRC and poke me, I could give you a quick rundown of how it all works. As explaining it here would be a bit awkward.

Regards

---

### Post by BackwardsDown on 2010-05-17
Why not create an extra user and run it under that user? That's what Linux is good at.

---

### Post by sfgairborne on 2013-04-05
There are sandboxes which will run in Linux.  That said, I've been out of the Linux/UNIX sysadmin field for some years now, and have no idea what would be the most up-to-date software to run.  Last time I ran a sandbox in Linux, I had to compile the source code myself.  I would assume there is a quicker, easier way to do it now...

---

### Post by oldos2er on 2013-04-05
Old thread closed.

---


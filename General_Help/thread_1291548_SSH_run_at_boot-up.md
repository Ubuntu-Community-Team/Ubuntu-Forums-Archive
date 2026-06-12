---
title: "SSH run at boot-up"
date: 2009-10-14
forum: General Help
---

### Post by GeoMoon5 on 2009-10-14
How do I get SSH server to automatically run when the Ubuntu computer boots up? I can't seem to find any relevant discussions on this topic.

I'm running Ubuntu server 8.10. 

Also, is there a straight forward way to program the Ubuntu computer to automatically turn back on after a power failure?



Thanks in advance for any help.

---

### Post by abyrne on 2009-10-14
OpenSSH should already start at boot-up.

And the power-failure thing would be in the BIOS of the computer. Mine says "Reboot PC after AC power loss". Look for something like that in your BIOS

---

### Post by GeoMoon5 on 2009-10-14
The motherboard BIOS setting solution worked!

As for the SSH server problem, mine does not automatically run when the machine boots up. I still need help with that.

I saw no setting in the configuration file that I can flip on or off that causes the SSH server to automatically run upon boot up.

   : /

---

### Post by tuxxy on 2009-10-14
Try and see if its set to run in system > administration > services

---

### Post by GeoMoon5 on 2009-10-14
Hmmm, I don't have any directories with those names. I think the directories you named are in the desktop version of Ubuntu. I'm running the server edition, so there's no graphical user interface.

---

### Post by GeoMoon5 on 2009-10-14
Well it looks like using OpenSSH-server is what I needed to do. I must have already installed OpenSSH-server last time I had easy access to the server, cause it was already installed. Looks like it starts up automatically just like it should, too. Glad that's taken care of.
Still strange that the SSH configuration files I found didn't seem to give an option for running OpenSSH-server automatically at startup, though. What if I wanted OpenSSh-server to not automatically run at startup?

I found this thread that might be helpful to others in my situation.

[http://ubuntuforums.org/showthread.php?t=373993]("http://ubuntuforums.org/showthread.php?t=373993")

---


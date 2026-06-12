---
title: "HDD clicking noise ONLY in Ubuntu"
date: 2011-07-06
forum: General Help
---

### Post by honkanen on 2011-07-06
I have a Dell Dimension 5150 desktop and I dual boot Ubuntu with Windows 7.  I haven't used Ubuntu in such a long time and thought I'd attempt to work out some of the bugs so I can use it without screaming and kicking the thing. ;-)  

Anyways, when I start the computer and from the GRUB screen, select Ubuntu, the HDD immediately starts a loud clicking noise.  It boots fine into Ubuntu and then I hear the HDD clicking noise whenever the CPU seems to be working on a task.  When I reboot and from GRUB, select Windows, I don't hear a peep out of the computer. It's normal (dead quiet), no matter what I do in Windows.

After reading some of the threads on this site, I noticed that most of this occurs with users on laptops.  I also saw people telling us to stop the syslogd daemon by: *"sudo service syslog stop"*  *OR  [FONT=Courier New]"sudo hdparm -B254 /dev/sda[/FONT]".  *I can't seem to find the syslog daemon though, let alone how to stop it from running.  

Any ideas what may be causing this clicking noise?

Thanks!

---


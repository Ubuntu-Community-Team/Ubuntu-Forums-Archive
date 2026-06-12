---
title: "Messing with sudoers file"
date: 2012-01-06
forum: General Help
---

### Post by bol on 2012-01-06
Having workes extensively with Linux a decade ago (Slackware and Linux Kernels in the 1-series) and recently having installed Ubuntu 10.04LTS, I of course overestimated what I remembered and started meddling with /etc/sudoers.d and created a file sudoers (with a content that was not what the system expected) so now, when I attempt to sudo, I recieve "sudo: parse error in /etc/sudoers.d/sudoers near line 1; sudo: no valid sudoers found, quitting". And since I did remember to change the permissions of the newly created sudoers file to 440 I can't remove it.

Have I then locked myself out permanently - or at least from sudo and its derivates such as gksu?

Is there anythng short of reinstalling?

Thanks in advance for any possible solutions!

Bo L

---

### Post by 1clue on 2012-01-06
Not sure if the Ubuntu installation CD is good for this, but many CDs are available you can boot from and fix your installation.  Boot from the CD, mount the / partition into /mnt and go edit the /mnt/etc/whatever file.  Save it, quit and boot back into the normal OS.

---

### Post by Buntumatic on 2012-01-06
> **Bo.Lewin@gmail.com said:**
> Having workes extensively with Linux a decade ago (Slackware and Linux Kernels in the 1-series) 
Bo L

I started using Linux in 1996 and the kernel was 2.0, went 2.2 in 1997 or 1998. What's the point of posting this BS?

Regarding your problem, there are numerous solutions an "old hand" should know. Like passing init=/bin/bash to your bootloader. 

Look, that's OK asking for help, just don't try tell us you know anything about Linux.

---

### Post by lechien73 on 2012-01-06
Hello & welcome to the forums,

You can reboot Ubuntu into "Recovery Mode", and fix the sudoers file from there:

[LIST]
[*]Reboot the machine
[*]After the power on self-test screen, press and hold the Shift key
[*]When the Grub boot menu comes up, select to boot Ubuntu in Recovery Mode.
[*]At the Recovery Mode menu, choose to drop to a root shell.
[/LIST]

You can then use visudo to correct the errors in the sudoers file.

---

### Post by bol on 2012-01-07
Thanks to all! (and please forgive me if I violated informal rules; The purpose of mentioning experience long time ago with Linux was simply to explain why someone could be stupid enough to mess with the sudoers file in a 'fool-proof'-distriution like Ubuntu).

One learns from one's mistakes and now I learned that I actually had a root-shell available at the boot prompt! 

Thanks again!

Bo L

---


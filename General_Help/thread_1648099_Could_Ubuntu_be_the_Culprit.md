---
title: "Could Ubuntu be the Culprit?"
date: 2010-12-18
forum: General Help
---

### Post by nu2this2 on 2010-12-18
Very strange happenings going on here. Have three computers that dual boot with Ubuntu and WindowsXP. All three have failed in the identical manner!

While reading a web site in Windows,the computer screen becomes frozen then a messege flashes momentarily stating "A problem has occurred" then the computer shuts down and will not reboot. Attempting to reboot results in a black screen with an unresponsive cursor in the upper right hand corner of the screen.

Any ideas?

---

### Post by lotharmat on 2010-12-18
Was Windows installed in the same manner using the same installation media?

My thoughts would be a corrupt windows install.

---

### Post by sikander3786 on 2010-12-18
All the OS even if installed on the same Computer, run independent of each other so Ubuntu can't be involved in failing Windows Web Browser or crashing it.

Regarding the blinking cursor issue, is Ubuntu installed inside Windows using the Wubi installer or it is on its own separate partition? Do you see the Grub menu when you turn on your PC?

Are you able to boot any of the OS i.e, Windows or Ubuntu after the hard reset?

---

### Post by nu2this2 on 2010-12-18
Ubuntu was loaded from a live cd. Aportion of the c drive was allocated for use.

I do not see  the Grub menu when I try to boot.

When I insert my windows restore disc the screen indicates press "R" for restore options. Pressing R does nothing, the screen remains the same.

---

### Post by sikander3786 on 2010-12-18
> I do not see the Grub menu when I try to boot.

Then how do you gain access to Windows?

---

### Post by nu2this2 on 2010-12-18
> **sikander3786 said:**
> Then how do you gain access to Windows?


I can't, the screen is as I described.

---

### Post by Rubi1200 on 2010-12-18
Windows problems are caused by Windows issues.

That being said, I think we need to have a better overview of your setup to be able to help you.

Boot the computer with the LiveCD and choose to try not install Ubuntu.

Then, run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

Also, we need to know the full specifications for the machine in question.

Thanks.

---

### Post by The Cog on 2010-12-18
I wonder if a windows virus was trying to hide in the area between the MBR and the first partition, where part of GRUB resides. My guess is that without having GRUB on there, all your PCs would have been rooted by now.

Normally, I would suggest using the alternate installer CD to "rescue" Ubuntu and reinstall GRUB (sudo grub-install /dev/sda) but I suspect that next time you start windows again, the virus will try to hide again and re-damage GRUB. Still, it might be worth a try.

---


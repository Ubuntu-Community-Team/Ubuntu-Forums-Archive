---
title: "Can not see boot menu."
date: 2011-09-20
forum: General Help
---

### Post by SantanuBarai on 2011-09-20
]My monitor is not showing my OS choice menu.

I have 14 inch CRT monitor. Newly installed Ubuntu 11.04. When (I guess) the OS choice menu is appearing, that is after showing the BIOS menu my monitor displays nothing,except "HZ ?". Then it automatically boots up in Ubuntu after 10s. So I cannot get into my Win 7. What to do?

---

### Post by raja.genupula on 2011-09-20
you mean your system directly booting to ubuntu with out showing grub to you .
press shift Key while your system booting, to get grub menu  . from there you can get your windows system . 


all the best

---

### Post by SantanuBarai on 2011-09-20
Thanks for your reply. But the problem was not that. How ever it is now solved. I just install GRUB, and as soon as I restart the boot menu comes up.

---

### Post by garvinrick4 on 2011-09-20
After install if when you booted into Ubuntu for first you have to:
```
sudo update-grub
```
as to run a package called "os-prober" as to put Windows install in as a menuentry and in config file.
Should have been done at install?

Would never had booted into ubuntu without grub installed.
So next time or anyone new to Ubuntu reading,  boot into Ubuntu and update-grub as a first choice.

If not showing grub menu it is defaulted not to show if only one install in config file. So if you hold
shift down before grub hits it will then show. OP would then have seen a menu with only Ubuntu
because system had not run update-grub.

Below is a couple of links to keep handy for all things grub. Enjoy your Ubuntu

[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
[Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275") 
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by raja.genupula on 2011-09-20
> **SantanuBarai said:**
> Thanks for your reply. But the problem was not that. How ever it is now solved. I just install GRUB, and as soon as I restart the boot menu comes up.
that really a good news , please mark your thread as solved .

---


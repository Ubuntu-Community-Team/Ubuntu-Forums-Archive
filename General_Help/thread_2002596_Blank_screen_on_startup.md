---
title: "Blank screen on startup"
date: 2012-06-12
forum: General Help
---

### Post by Cicer on 2012-06-12
I have an encrypted drive and after upgrading to 12.04 I have found that about 30% of the time when I start up, ubuntu properly displays the text prompt for me to enter my password to unencrypt the drive. The rest of the time it lands at the prompt but the screen is blank and my external monitor registers as having no input. I can still type my password though and then the monitors come alive and take me to enter my user password.

I'm not sure where to start looking to fix this. Could it be a grub setting?

---

### Post by werty1st on 2012-11-27
I have the same problem after upgrade to 12.10 from 12.04 x64.

i removed the amd prop. drivers and installed the radeon driver.

i found out that there is a graphical luks password prompt if i switch through ctrl+alt+f1 to f7

if i press esc the screen wakes up and shows a textprompt.

---

### Post by werty1st on 2012-11-27
i found the problem.

i had to remove all the extra parameters from the grub_cmdline:

"/etc/default/grub"
new-> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
old-> #GRUB_CMDLINE_LINUX_DEFAULT="kopt=root=/dev/mapper/vgubuntu-root ..."

then run update-grub

ps: you can test your new setting by editing the grub parameters at boot press "e" and remove the extra commands and then continue with F10.

---

### Post by werty1st on 2013-01-09
I am sorry but this was not the problem. i have this issue on 2 machines now.

the screen goes into standby while the system waits for the user to enter the luks password. 100% of the time.

---

### Post by werty1st on 2013-01-09
i solved the problem combining 2 recommendations from this post:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802")

frist

get the supportet resolution:
> When you run vbeinfo, grub reports a preferred resolution at the end.

:!: vbeinfo must be run from the grub console. :!:

then enter one of the resolutions reported by vbeinfo in your */etc/default/grub*:
GRUB_GFXMODE=1600x1200

second
> So, I just copied /usr/share/grub/*.pf2 to /boot/grub and ran update-grub again. Voila, I got my gfxmode and a working unicode font, too.

**cp /usr/share/grub/*.pf2 /boot/grub**
and run
**update-grub**

---


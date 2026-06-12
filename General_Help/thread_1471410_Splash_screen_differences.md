---
title: "Splash screen differences?"
date: 2010-05-03
forum: General Help
---

### Post by toxic9813 on 2010-05-03
When I installed Ubuntu 9.10 on my machine, the splash screen was full resolution (1280x1024) and when I upgraded to the 10.04 alpha 3, it was a text-based splash screen. Same with the Beta1+2. Now, with the final LTS, my splash screen is displayed at 640x480, and is a bit glitchy, with flickering and occasionally it's split in two pieces. I know it's a little thing, but I like showing off my cool OS to people ;)

The reason why I bring this up is because when I was building a computer for my friend, I formatted the old XP and installed a fresh 10.04 LTS, the resolution of the splash screen is at max 1280x1024, and is has the nice glowing dots underneath "ubuntu". As far as I know, the computers are exactly the same. Any ideas?

Thanks

---

### Post by P4man on 2010-05-03
If you dont mind risking bricking your system, have a look here:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

YMMV.

---

### Post by toxic9813 on 2010-05-03
That may help. I have all the symptoms described, but I still may need more help.

---

### Post by toxic9813 on 2010-05-03
Okay, noob remark here: I don't understand the solution very well.

---

### Post by P4man on 2010-05-03
which part/step dont you understand?

---

### Post by Fuel90 on 2010-05-03
I had the same problem, but only after I installed the "ATI/AMD proprietary FGLRX graphics driver"
So I just disabled the driver and the problem was fixed :D

The driver would also cause my system to "hang" every time I would maximize a window or open a window from the task bar or even open any program.

---

### Post by toxic9813 on 2010-05-03
> **P4man said:**
> which part/step dont you understand?


Well I figured it out *slightly*. I know where to go, but I don't feel like I'm doing it right :|

[FONT=Arial Black]* Edit */etc/default/grub* to make sure we boot with uvesafb  framebuffer. For the mode_option parameter change to your native screen  resolution you see from running the above comment (if not just set to  1024×768-24 which is safest. Oh, Netbook user – please exercise some  common-sense here)  Non relevant lines are omitted for clarity.

...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset  video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap"
...
GRUB_GFXMODE=1366x768
[/FONT] 
 [FONT=Arial Black] [/FONT]
 [FONT=Arial Black] [/FONT]
 [FONT=Arial Black]* Edit */etc/initramfs-tools/modules * to include uvesafb by  adding the following line.

uvesafb mode_option=1366x768-24 mtrr=3 scroll=ywrap
[/FONT] 
 [FONT=Arial Black] [/FONT]
 [FONT=Arial Black] [/FONT]
 [FONT=Arial Black]* Force the use of framebuffer:
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash[/FONT]

---

### Post by toxic9813 on 2010-05-03
I found this, and am now rebooting ;)

[http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html#comment-41037671](http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html#comment-41037671)

---

### Post by rahilm on 2010-05-03
> **P4man said:**
> If you dont mind risking bricking your system, have a look here:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

YMMV.
You know what?? those guys were right.. it does break your system.
now i can't see the splash screen at all and my cursor is invisible until i open a terminal and run any sudo command...

i'll try to roll back changes.

---

### Post by toxic9813 on 2010-05-03
It broke my OS. Well, I have live CD's up the wazoo to reinstall from.

:cry:  ](*,)

---


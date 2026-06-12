---
title: "System stucks until I move the mouse or press a key"
date: 2010-10-11
forum: General Help
---

### Post by marius410 on 2010-10-11
Hello everybody,

I just tried to install Ubuntu 10.10 x86 on my netbook (Lenovo S12 - Intel at all) but this is just horrible. The system is dead after a few seconds but after I moved the mouse or pressed a key it goes on normally for a few seconds and then it stucks again and so on. 

Ubuntu 10.04 had the same problem but it was not that extreme! Maybe it stucks after 2-3 minutes but not after 3-5 seconds! And after I installed all the updates it runs just fine.

What can I do? I really love Ubuntu and it's a pitty that I cannot use it.

Thanks :)

Greetz from Germany.

---

### Post by Peter09 on 2010-10-11
Have you seen this?

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by marius410 on 2010-10-11
Sorry, but I do not know how this can help me. Grafics are running perfectly. Not only the display stucks, everything stucks (hard drives for example). 

I've read everything at wiki.ubuntuusers.de but it cannot help me.

---

### Post by ssam on 2010-10-13
you are probably suffering from
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/643822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/643822)

when you are boot the live cd there should be an option to add an option the to boot command line. i think you press F6 then escape (see [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) ). you need to add "nolapic_timer" (without the quotes), to the end of the command.

---

### Post by marius410 on 2010-10-13
Thank you very much. That helps.

But I have already installed Ubuntu now by moving the mouse the complete time and solved my problem at another way.

I added clocksource=jiffies to /etc/default/grub and now it runs perfectly too.

I am going to use your way for my next new installation :)

---

### Post by dj_pajak on 2010-10-13
I have the same problem in Ubuntu 10.10. Sometimes everything stops - animations, progress bars, content of windows - only moving the mouse and pressing buttons on keyboard and mouse helps. But when I stop moving or pressing everything stops again. Sometimes I have to keep pressed key so that system can shut down.
Adding clocksource=jiffies to /etc/default/grub doesn't help me, but after changing 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"' on 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer"' is OK :)

On Ubuntu 10.04 everything was OK.

---


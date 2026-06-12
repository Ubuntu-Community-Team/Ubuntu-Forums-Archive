---
title: "GRUB BASH-like screen on boot"
date: 2010-04-28
forum: General Help
---

### Post by nlhma on 2010-04-28
Hi,

I installed Ubuntu 9.10 with Wubi on a Windows XP machine. Everything is fine until today's update, now when I choose to boot with ubuntu, a screen shows up saying [Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

Any pointers what I should do?

Thank you.

---

### Post by nlhma on 2010-04-29
Please help me solve this problem.

---

### Post by dino99 on 2010-04-29
you are into a sub-menu, dont remember what to do but look at hot-keys at bottom line.

---

### Post by nlhma on 2010-04-29
I don't see any hot keys at the bottom line. Only that message and then a bash-like terminal for grub. The commands available are badram, boot, cat, chainloader, configfile, cpuid, dump, echo, exit, export, halt, help, initrd, insmod, linux, list_env, load_env, loopback, ls, lsmod, parser_rescue, parser.sh, reader.normal, reader.rescue, reboot, rmmod, root, save_env, search, set, sleep, source, terminal_input.console, terminal_output.console, test, unset.


One more note is that I am still able to boot my Windows XP normally. Could you guys let me know what caused the problem and how to solve it?

---

### Post by dino99 on 2010-04-29
> **nlhma said:**
> I don't see any hot keys at the bottom line. Only that message and then a bash-like terminal for grub. The commands available are badram, boot, cat, chainloader, configfile, cpuid, dump, echo, exit, export, halt, help, initrd, insmod, linux, list_env, load_env, loopback, ls, lsmod, parser_rescue, parser.sh, reader.normal, reader.rescue, reboot, rmmod, root, save_env, search, set, sleep, source, terminal_input.console, terminal_output.console, test, unset.


One more note is that I am still able to boot my Windows XP normally. Could you guys let me know what caused the problem and how to solve it?

try exit as you are into a sub-menu

---

### Post by nlhma on 2010-04-29
I have already tried that. It says cannot boot from any device.

---

### Post by dino99 on 2010-04-29
so try the hard way:

boot with a cd or usbstick
then chroot to your ubuntu partition following this sample:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

( of course, give the real path, its a sample)

when done, from there you can do everything on the ubuntu partition: updating, calling synaptic, ...

so, remove/purge grub with synaptic, then reinstall it on your main ubuntu partition (something like /dev/sda), then:

sudo grub-mkconfig && update-grub

exit and reboot

note: i've reread your first post and seen that its an wubi install, so dont know if that work in that case, why have you not made a real install ? (just install grub on the ubuntu partition to not overwrite the windows loader)

---


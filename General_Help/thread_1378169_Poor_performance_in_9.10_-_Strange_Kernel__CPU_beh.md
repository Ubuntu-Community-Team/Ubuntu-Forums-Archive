---
title: "Poor performance in 9.10 - Strange Kernel / CPU behavior - HPET"
date: 2010-01-11
forum: General Help
---

### Post by alloneword on 2010-01-11
Hello All,

I did a clean install of 9.10 on the weekend just passed and had some very strange issues.

After installing (formated / preserved /home) my PC ran fine and stable for about 2 - 3 hours. I updated some drivers, and ran software update. It was all fine, flash was even working full screen!

(For all those too busy to read the rest, hpet was doing something funky, and cause the CPU to grind to a halt. I went to a later kernel, and disabled hpet in the grub config. At no point did I do an 'upgrade' all were clean installs.)

Then it all just ground to a halt. My speed step'ed CPU refused to get off 800MHz, and everything that tried to do anything ran at about 100% cpu. I mean anything. Moving the mouse was an issue.

After much googleing I uninstalled the restricted Nvidia drivers. Somewhere (which I can't find in my history) said the drivers were clashing with the CPU and not letting it speed step properly.

This seemed to solve it for about 10min when it all went bad again. 

Instead of stuffing around for too long I decided to just reinstall and format the '/' partition again.

Once again, everything seemed smooth and happy for about an hour or two.

Then it started again. This time I disabled ONDEMAND with rcconf. And updated the kernel with a new .deb.

Once again, it all seemed good for an hour or so, then it all fell apart.

I upgraded the kernel to a new RC of a the next one, (.deb) and tail'ed /var/log/messages and waited for it to slow down.

At no point did rebooting / shutting down help. Kernel upgrade seemed to be the only thing that brought back the performance.

With messages in an open terminal I surfed the web, and watched some videos till it all came to a grind halt again, and saw the following:

Jan 10 12:00:28 tumblr kernel: [ 1467.529864] CE: hpet increasing min_delta_ns to 22500 nsec
Jan 10 12:00:35 tumblr kernel: [ 1475.401091] CE: hpet increasing min_delta_ns to 33750 nsec
Jan 10 12:00:37 tumblr kernel: [ 1476.674491] CE: hpet increasing min_delta_ns to 50624 nsec


Some googling later I added hpet=disable to the grub config.

The PC is running fine now, all be it with ONDEMAND still off.

If it is helpful to track this to an issue that may affect other people, trouble shooting info is attached.

Hardware:

Dell Latitude E6400 Laptop
Core 2 Duo 2.4GHz
Nvidia Quadro NVS 160M 

Current kernel is: 2.6.33-020633rc3-generic

I now have this when I boot (which I am fine with): 
Jan 11 20:38:39 tumblr kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.33-020633rc3-generic root=UUID=e6094019-9249-4f29-a2de-80a120ebdd0b ro hpet=disable
Jan 11 20:38:39 tumblr kernel: [    1.169023] hpet_acpi_add: no address or irqs in _CRS



Cheers, Tim.

---

### Post by 9tails on 2010-02-19
Weird. In my case 9.10 worked fine for a long time.

Now that I'm trying lucid (alpha 2) I suddenly noticed those same hpet warnings:

```
CE: hpet increasing min_delta_ns to 15000 nsec
CE: hpet increasing min_delta_ns to 22500 nsec
etc.
```

I know that hpet can be disabled by adding hpet=disable to the default kernel parameter, but if it is a bug in kernels < 2.6.33 I really hope it gets fixed :???:

---


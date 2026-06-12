---
title: "Graphic Card overheating (even without X!)"
date: 2011-08-23
forum: General Help
---

### Post by Sifro on 2011-08-23
Hello,

ubuntu natty has huge problems in handling my graphic card, a nvidia geforce 7600gt.

It was very hard to install the base system: i downloaded the Minimal ISO and began a text-based install, but i couldn't get to the end because the graphic card failed before the end because of overheating. It was incredibly hot and my BIOS signals after rebooting confirmed that.

I tried again, cooling it down manually with ice, and i managed to boot the installed system. After a few minutes, it failed again (the ice was melted...). Please note that i didn't even install X, i was running a terminal!

With Windows everything works fine. I can even play some games, and my card is always pretty cool.

What should i do?

Thanks!

---

### Post by el_koraco on 2011-08-23
You're gonna need the proprietary driver to get your card to cool down. In the meantime, since you have a minimal install, try booting it long enough to install the packages cpufrequtils, acpi, and acpi-support. This might get you cooled down for long enough to install X, and then the Nvidia driver.

---

### Post by kaldor on 2011-08-23
First, have you tried using the proprietary NVIDIA driver? The default (Nouveau) drivers lack power management and users often report heat issues. When using the proprietary NVIDIA driver my laptop idles at ~50 degrees. With the default driver, it goes beyond 90 degrees.

Edit: oh hi. Beaten to it :)

---

### Post by Sifro on 2011-08-23
Thanks to both of you.

So after doing a minimal install, what should I do first?
Install acpi or install proprietary drivers?

Would it be different if i use a complete ubuntu install CD?

Thanks

---

### Post by kaldor on 2011-08-23
Well, to install the proprietary drivers in a GUI, you'd use the Jockey utility which is installed by default. Since you're doing this in a TTY, you'll need to do it like this...


Remove Nouveau (if installed):

```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```


Install the driver:

```
sudo apt-get install nvidia-current
```

Should work, but I've never done it from a terminal on Ubuntu.

---

### Post by realzippy on 2011-08-23
> **Sifro said:**
> 
I tried again, cooling it down manually with ice, and i managed to boot the installed system. After a few minutes, it failed again (the ice was melted...).


..thats a interesting way to kill a graphic card.(..or did you use ice made from distilled water??)

Check if the card's fan spin.
Unplug card:
Check if there is dirt/dust in the heat-sink.
Check if heat-sink fits correctly/is tight...

---

### Post by Sifro on 2011-08-23
The card is fine, in fact it works on windows, the fan works, the heatsink is tight.
... and obviously i didnt put ice *directly* on it, lol.

Now i'll try installing the nvidia drivers, but i need to refill my ice supplies first :D

---

### Post by Sifro on 2011-08-23
solved with nvidia current

---


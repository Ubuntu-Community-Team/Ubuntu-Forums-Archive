---
title: "Keyboard misses keypresses"
date: 2009-08-12
forum: General Help
---

### Post by spinez on 2009-08-12
I just installed 9.04 (as well as 8.10 later) on my laptop and am having weird keyboard issues on both installations.  

When I am typing, especially when typing pretty fast, the system is missing about 10% of my keypresses.  I have no idea where to even begin looking but on Windows XP, Vista, or Win7 on this same machine, I -never- have this problem.  

The system is more than capable.. 

Core2Duo @ 2.53GHz
4GB RAM
Nvidia 9800GT video
200mb 7200rpm hdd

If you guys can help me out that would be great.  I'm also considering installing the latest Fedora and/or Gentoo and seeing if the same problem persists.

---

### Post by P4man on 2009-08-12
Wild guess: you have an Acer laptop ?

Slightly less wild guess: you have a laptop with a crummy ACPI implementation, and linux doesn't play nice with it. 

To test my theory, when you get to the grub menu, select the ubuntu line, then press "e" to edit. Select the second line with your kernel parameters, press "e" again and add "acpi=off". It should look something like this:

```
/boot/vmlinuz-2.6.28-14-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash acpi=off
```

press enter to confirm, then "b" to boot. This change is not permanent, it will only affect 1 boot. Just see if it solves the problem or not (though it will disable a lot of useful powermanagement stuff).

---

### Post by spinez on 2009-08-12
It's not an Acer.  It's a taiwanese brand called Sager that is built off of Clevo.  I would think their ACPI implementation would be solid, but it's a good guess.  I'll try that next time I reboot and see what happens. 

Thanks for the suggestion.

---

### Post by P4man on 2009-08-12
FWIW, here is someone else with a sager machine having .. well. lots of weird problems running ubuntu that I would guess are  acpi related:

[http://ubuntuforums.org/showthread.php?t=1232587](http://ubuntuforums.org/showthread.php?t=1232587)

It doesn't really matter if its sager's fault, or the kernel developers, it does look like the two don't get along very well :s. Anyway, im jumping the gun here, lets see what happens when you boot with acpi turned off.

---

### Post by P4man on 2009-08-21
have a look at this:
[http://ubuntuforums.org/showpost.php?p=7824338&postcount=5](http://ubuntuforums.org/showpost.php?p=7824338&postcount=5)

---


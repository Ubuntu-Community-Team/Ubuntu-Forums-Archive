---
title: "How to fix my GRUB bootloader after I uninstalled Fedora 15!"
date: 2011-08-05
forum: General Help
---

### Post by x-D on 2011-08-05
Hey, basically what happened to me, is that I installed Fedora 15 alongside Ubuntu, only to discover that it doesn't play nice with Ubuntu and this means that even though I formatted the Fedora Partition and made it into a new one, (i needed around a 7gb space for video editing files etc, so it is optimised for this). Anyway, that's off topic. Even though all traces of Fedora are gone, everyone time I go to boot from the HardDrive, it goes into Fedora's starting screen (the blue one with the loading icon) and then says it failed and gives a little command line.

What I'm really asking is how to sort it out, so that Ubuntu will load and that the Fedora version of GRUB is gone, or something like that.

Can anyone help me?

---

### Post by x-D on 2011-08-05
Just fixed it all... what I did is...

After a bit of searching the net, I found a little program called 'Boot-Repair'. What it does, is it reinstalls your GRUB Bootloader, and here, for me, it deleted the Fedora one and replaced it with a new up-to-date Ubuntu one. Thanks to whoever created that Utility for saving my life! :guitar:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair 
```

```

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu
```

This will get you Boot-Repair! :)

x-D :P

---


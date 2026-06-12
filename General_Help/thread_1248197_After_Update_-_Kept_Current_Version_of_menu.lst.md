---
title: "After Update - Kept Current Version of menu.lst"
date: 2009-08-23
forum: General Help
---

### Post by novafluxx on 2009-08-23
I chose to keep the current version of menu.lst, because I didn't feel like editing it again, then the only problem is not I'm only offered to boot -14 from the GRUB menu, and not -15.

I booted it up and did uname -a and I am indeed still running -14 and not -15.

How can I fix this?:P

---

### Post by drs305 on 2009-08-23
If you don't want to manually edit menu.lst, install StartUp-Manager. It's a GUI app that tweaks a lot of grub settings. SUM will let you set the default kernel as well as how many to display on the menu.

Read about how to install and use it by clicking the "SUM" link in my signature line.

---

### Post by novafluxx on 2009-08-23
This is exactly what I need. I'd love to know HOW TO do it manually, but this will certainly for for day-to-day editing (as if I need to edit it daily lol)

I thought something like this was included with Ubuntu by default

---

### Post by drs305 on 2009-08-23
> **novafluxx said:**
> This is exactly what I need. I'd love to know HOW TO do it manually, but this will certainly for for day-to-day editing (as if I need to edit it daily lol)

There's a section on editing grub manually if you must... ;-)

---

### Post by novafluxx on 2009-08-23
The -15 kernel isn't listed as an option... :-/

Looks like I'm stuck again

---

### Post by drs305 on 2009-08-23
> **novafluxx said:**
> The -15 kernel isn't listed as an option... :-/

Looks like I'm stuck again

If it installed it should be in /boot.
```

find /boot -type f -name "vmlinuz*"

```

Or look in Synaptic under "linux-image-2.6..."

---

### Post by michy99 on 2009-08-23
Try running this in a terminal:```
sudo update-grub
```

---

### Post by novafluxx on 2009-08-23
> **drs305 said:**
> If it installed it should be in /boot.
```

find /boot -type f -name "vmlinuz*"

```

Or look in Synaptic under "linux-image-2.6..."

/boot/vmlinuz-2.6.28-15-generic is listed by running that command. So it is installed, but not listed as an option in SUM.

---

### Post by drs305 on 2009-08-23
> **novafluxx said:**
> /boot/vmlinuz-2.6.28-15-generic is listed by running that command. So it is installed, but not listed as an option in SUM.

Then update-grub as michy99 mentioned. It should then appear in grub and StartUp-Manager options.

---

### Post by novafluxx on 2009-08-23
Ah, I ran update-grub as mentioned, it finished. I checked SUM, no change, I ran update-grub again, this time I was presented with the option to use package maintainers version of menu.lst and I used it, and now I'm running -15!

Thanks for the super fast help and your time!

Now I'll edit it to get rid of all those old kernels I no longer want!

---


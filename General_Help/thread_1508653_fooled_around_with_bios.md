---
title: "fooled around with bios"
date: 2010-06-13
forum: General Help
---

### Post by jimbean on 2010-06-13
now ubuntu will not boot to desktop
it goes to grub and i can select some recovery options for kernels
but it just loops back to the desktop prompt, no desktop just prompt
i am not at the machine right now 
all i did was to set all of the bios options to default
ive done this before 
just wondering if there any suggestions so i dont have to reinstall

---

### Post by limestone on 2010-06-13
If you can't remember what you changed in BIOS, there is an BIOS reset to default somewhere in there.

---

### Post by Soul-Sing on 2010-06-13
some bios preferences have a "default option" that will restore your bios settings.

---

### Post by jimbean on 2010-06-13
yeah dont know what i changed but i did reset to default a couple of times

---

### Post by limestone on 2010-06-13
> **jimbean said:**
> yeah dont know what i changed but i did reset to default a couple of times
And that didn't work?? Then you probably did something to GRUB.

---

### Post by jimbean on 2010-06-13
i think it has something to do with the boot script if there is something like that
what do you type to get a gui from the destop prompt

---

### Post by WorMzy on 2010-06-13
If you have more than one hard disk, then it's possible that by resetting the bios, you've caused the disks to be loaded into /dev in a different order, therefore making /dev/sda become /dev/sdb, and vice versa (or something along those lines, if you have more than two disks).

Let me make it clear now, so you won't worry unnecessarily: you won't need to reinstall.

You just need to boot into a live CD or USB of Ubuntu (or any other distro you have lying around), mount your Ubuntu partition, mount /proc and /dev to /media/<Disk label or UUID>/<proc|dev>, chroot to /media/<Disk label or UUID> then run 'sudo update-grub'.

That should fix it right up. Let me know if you need a clearer step-by-step and I'll write one up.

---

### Post by jimbean on 2010-06-13
thankyou i will print this up for tomorrow at work
i made this machine {the 1 that i broke linux on}
so people could serf the internet at work
have a good day :)

---

### Post by wilee-nilee on 2010-06-13
Check the HD type in bios sata or ide, changing that will get you a no boot as well.

---

### Post by warfacegod on 2010-06-13
I you are able to get into Recovery Mode then it's rather unlikely that messing with the BIOS has anything to do with this. When you get to your desktop prompt enter your credentials (username/password). If that doesn't give you a GUI then try startx.

If you can get a GUI with either then I'd say you need to reinstall gdm.

---


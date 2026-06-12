---
title: "Failsafe graphics mode"
date: 2010-05-26
forum: General Help
---

### Post by Kid A on 2010-05-26
I have quite the peculiar problem here:  Whenever I boot into ubuntu I do not have any internet access and it runs painfully slow.  However when I boot into the failsafe graphics mode under the recovery boot option everything runs fine and dandy.  Naturally I thought this would indicate a graphics issue, but the fact that I have internet in failsafe mode is confusing me.

Running ubuntu 10.04 x86 on an emachines T5216

---

### Post by cariboo on 2010-05-26
It would help if you gave us some hardware info, especially what graphics chip set.

---

### Post by Kid A on 2010-05-27
it's running an ATI Radeon Xpress 200,   Intel Pentium D 805 / 2.66 GHz, 2 GB DDR2.

---

### Post by -humanaut- on 2010-05-27
Try hitting alt+f2 type gtk-jockey and see if theres any available drivers for your card.

---

### Post by Kid A on 2010-05-27
^tried that and it didn't find any drivers. 

also sometimes when i boot ubuntu without failsafe mode i seem to lose the USB peripherals (mouse and keyboard stop responding) about 15-20 seconds in.

---

### Post by Catharsis on 2010-05-27
Hold down Shift while booting to get to grub. Press 'e' and replace "quiet splash" with "nomodeset". Ctrl+x to boot. If that doesn't do anything, replace it with "noapic" instead.

---

### Post by Kid A on 2010-05-27
> **Catharsis said:**
> If that doesn't do anything, replace it with "noapic" instead.

that seemed to do the trick..here is how i changed it to boot with apic disable (for anyone else with a similar issue)

i ran: 
```
sudo gedit /etc/default/grub
```and i found the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```and i changed it to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```
finally i ran:
```
sudo update-grub
```

that seemed to fix my issue and boot ubuntu with apic disabled. 


thank you for the help!

---

### Post by devxdev on 2011-10-18
> **Catharsis said:**
> Hold down Shift while booting to get to grub. Press 'e' and replace "quiet splash" with "nomodeset". Ctrl+x to boot. If that doesn't do anything, replace it with "noapic" instead.

Im sorry that this thread is suuuper old but it solved my problem!

I was having issues getting past checking battery after a fresh install of 11.10 but i entered nomodeset in grub and it worked

Intel i7 990x
nVidia GeForce GTX 460M
Toshiba Quosmio x500

---


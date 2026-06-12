---
title: "laptop doesn't fully shut down"
date: 2009-07-22
forum: General Help
---

### Post by drudogg on 2009-07-22
my hp laptop is working well and i am happy with it so far. a few things are not quite right though.

the main one is the fact that when i tell it to shut down it does the whole process, except actually powering off. it does the bar and a few messages, and then it just says "System halted" and sits there.  

is there anything i can do to remedy this situation? would like it to shut off properly.

---

### Post by snargfish on 2009-07-22
Are you using Karmic alpha?

---

### Post by samborambo on 2009-07-22
try adding "noapic" (not "noacpi") to your kernel parameters on boot. Test it by modifying the kernel string in grub at boot time. If the shutdown works, permanently set it in /boot/grub/menu.lst.

Sam.

---

### Post by Strongman332 on 2009-07-23
i have a similar problem with ubuntu 9.04 on an dell xps m1530 only i just shows the"_" character and sets there

---

### Post by drudogg on 2009-07-23
i am running jaunty, as i have in my sig. sorry i should have specified.

and i will try the apic thing. not sure how to add anythig to grub... anyway, i have had this same system loaded on this laptop before, with no problems. so not sure why it is causing the problem now.

---


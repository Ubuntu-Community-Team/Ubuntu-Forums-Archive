---
title: "&quot;Kernel Panic: no init found&quot; after update!"
date: 2006-04-03
forum: General Help
---

### Post by riwa on 2006-04-03
A computer doesn't start now right after new update. The following message comes up while booting the kernel.
```

[LOTOFNUMS]Kernel Panic - not syncing: No init found. Try passing init= option to kernel.
[LOTOFNUMS]
```

Anyone else with the same problem?

Regards
Richard

---

### Post by taurus on 2006-04-03
Do you have an initrd for your latest kernel?  If you do, then check the entry for your kernel again in /boot/grub/menu.lst.

---

### Post by riwa on 2006-04-03
Well I can't really do anything from there. Goes to grub and stays!

---

### Post by taurus on 2006-04-03
Then use the LiveCD and mount your harddrive and have a look at /boot and /boot/grub/menu.lst!

---

### Post by anstosa on 2007-12-23
im having the same problem and error message after an update. i cant remember the nature of the update but it said that it required a restart so i did and then got the message. i booted off the live cd, mounted my drive, checked out /boot and /boot/grub/menu.lst

everything seems to line up (the initrd file that the grub is looking for is where it should be and named the same thing)

as far as i can tell everything should be working but then again im pretty new with linux. what else should i be looking for?

---

### Post by ptn107 on 2007-12-23
Your entry in */boot/grub/menu.lst* should look similar to the following (except for your grub root and device UUID).  Make sure the *initrd* line exists.
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=25e4ecdf-eee0-40d2-b869-1511e80b3087 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

---

### Post by anstosa on 2007-12-23
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ae7d6bfb-a0b9-4923-b5ce-77f062567a38 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

thats what i have

---

### Post by anstosa on 2007-12-23
any alternate theories on what could be going wrong?

---

### Post by colgt on 2008-02-06
Hi there

I just had this same problem with Gutsy 32bit - I rarely restart the system so when I had to for a kernel update I turned it off to hoover out the inside and put in an extra fan.  During this system maintenance I took the RAM out as well and put back in.  I then got this error when I started the system again - even with older kernel versions on live cd's, so I knew it wasn't due to the kernel update.

It was fixed by changing my ram around - I had obviously put it back in different slots initially.  My motherboard is dual channel but my ram isn't - so it only boots up with the ram in the two slots for the first channel, and now it appears only in a certain order in those slots.  Try opening the case and moving the ram around a bit.  No idea why this happens - must be some integrity issue with the memory controller and the ram.

---


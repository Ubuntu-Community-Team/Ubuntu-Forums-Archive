---
title: "686 kernel won't boot"
date: 2006-02-04
forum: General Help
---

### Post by ThomThom on 2006-02-04
My 686 smp kernel suddenly stopped to boot. the default 386 still works, which I am logged in at the moment.

When I try to boot the 686 kernel the screen says:
"Uncompressing Linux..................Ok, booting the kernel"
then after about 5 seconds it reboots the machine which brings me back to the grup menu.

---

### Post by bonzodog on 2006-02-04
What sort of processor are you running? the 686 smp kernel is a multi processor/multi-core kernel. I suspect you have the wrong one.

---

### Post by ThomThom on 2006-02-04
A Pentium 4 Hyperthreaded
It has worked fine up until now.

---

### Post by ThomThom on 2006-02-04
I found this thread: [http://ubuntuforums.org/showthread.php?t=118534&highlight=Uncompressing+Linux](http://ubuntuforums.org/showthread.php?t=118534&highlight=Uncompressing+Linux)
but what is the boot prompt?

---

### Post by ThomThom on 2006-02-05
noone?

---

### Post by ThomThom on 2006-02-06
bump

---

### Post by Perfect Storm on 2006-02-06
You tried completly removal of the i686 smp and a new installing?

---

### Post by ThomThom on 2006-02-06
no. I'm not even quite sure how I do that. can I use the Synaptic installer for that?

in any case, what is the "boot prompt?"?

---

### Post by ThomThom on 2006-02-08
"boot prompt", anyone?

---

### Post by grep on 2006-02-14
If you are asking what the boot prompt is, it is displayed when you boot your computer from a ubuntu cd.  After the cd boots and begins to load, the menu will appear asking you if you want to install and will give you boot options if you hit f1 when prompted.  The boot prompt is simply "boot:" at the bottom of the screen.  You can simply hit enter to begin a regular install, or add options, like "server", "linux netcfg/disable_dhcp=true", etc.

---

### Post by nanotube on 2006-02-14
the boot prompt as referred to in the thread you linked is the prompt you get by hitting 'e' when you see the grub menu (or was it hitting that other thing... anyway, below the boot menu it will have instructions for you. hit e to edit the boot prompt, or something like that.)

but anyway, at this point, may be easier to reinstall from synaptic (search for "linux-686" by name and you will find it there somewhere, and mark for reinstall)...

---

### Post by ThomThom on 2006-02-15
The thing is that I already tried reinstalling linux-686-smp from synaptic. But no luck. Still got the same message.

---


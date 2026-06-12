---
title: "acpi=off required to boot, but won't shut down"
date: 2010-02-17
forum: General Help
---

### Post by 11bolts on 2010-02-17
I've built several computers and installed Ubuntu on each one, and I've never had problems until my latest build.  Here are the problems:

The computer requires acpi=off to boot, and it won't boot with acpi=ht.  I've searched for this, and there's a widely reproduced acpi troubleshooting guide that says that this means that there's something wrong with the acpi tables themselves, but I haven't found any fixes.

If I go ahead and use acpi=off, then the computer works fine, but it hangs on shutdown.  I've searched for this too, and the consensus seems to be to remove acpi=off from the boot options.  This, of course, is not an option for me.

I'm using Ubuntu 9.04, Kernel 2.6.28-18.  My specs are Asus P6T SE, Intel i7-950, 12GB RAM.

---

### Post by deadalus.globalnode on 2010-02-17
have you tried to shutdown via the terminal? I am no expert but you might try 
#sudo shutdown now -h
If it says 
#shutdown comand not found
then you will have to log in as root and then try again.

---

### Post by 11bolts on 2010-02-17
sudo shutdown -h now yields the same result as the shutdown button on the desktop.  I get a message saying System Halted, and then the system hangs.

---

### Post by efflandt on 2010-02-17
Does it shutdown to the point where is sounds like fans and drive(s) stopped, but is still powered up?  You might try "lapic" boot parameter.  I had to use that on an old PIII 550 machine to get it to power down entirely.

Although, I actually had to use "acpi=force lapic" (acpi worked in that case, but kernel would not automatically use it because BIOS predated 1999).

---

### Post by RedSquirrel on 2010-02-17
> **11bolts said:**
> sudo shutdown -h now yields the same result as the shutdown button on the desktop.  I get a message saying System Halted, and then the system hangs.

At that point, the system has safely shut down and you can press the power button. When you use 'acpi=off', the system cannot turn off by itself; you have to do it manually (with the button).

There might be some other 'acpi=...' that could work for your system and that isn't as drastic as acpi=off, but you'll have to do some research. (Unless of course you've already done that and 'acpi=off' is the only one that works. ;))

---

### Post by 11bolts on 2010-02-18
> At that point, the system has safely shut down and you can press the power button. When you use 'acpi=off', the system cannot turn off by itself; you have to do it manually (with the button).

Ah OK - I guess that explains that.


> There might be some other 'acpi=...' that could work for your system and that isn't as drastic as acpi=off, but you'll have to do some research. (Unless of course you've already done that and 'acpi=off' is the only one that works. )

Well acpi=ht fails, and I've found the following piece of info online: 

[I]"acpi=ht:
the most like "acpi=off", disables all of ACPI except what is needed to enumerate processors. 
If acpi=off works and acpi=ht fails, then the issue is in the ACPI table parsing code itself, or perhaps the SMP code."[/I]

Does anybody know what that means, or how to fix it?

---

### Post by RedSquirrel on 2010-02-18
Have a look around for known issues with that motherboard. You could try a newer kernel, perhaps Karmic (Ubuntu 9.10), or some other OS altogether. A BIOS update might help as well.

---

### Post by puddlejumper on 2010-02-28
I have this same problem on my desktop computer.  On that same computer, windows XP shuts down just fine.

I also have a notebook computer running 9.10.  I purchased it from System 76.  All works fine on this computer.

I have compared the /etc/default/grub files on the computers and found that the notebook has the following line.

UB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux acpi_osi=Linux"

On the desktop system, everything beyond the quiet splash is missing.  Adding the missing stuff to the desktop 9.10 computer didn't change anything.

---

### Post by puddlejumper on 2010-02-28
Oops.  that should have been:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux acpi_osi=Linux"

---

### Post by 98cwitr on 2010-10-17
had the same problem until I added apm power_off=1 to the line :)

GRUB_CMDLINE_LINUX_DEFAULT="acpi=off apm power_off=1 quiet splash"

---


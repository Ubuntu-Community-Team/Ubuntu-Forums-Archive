---
title: "Double Boot Menu"
date: 2010-11-25
forum: General Help
---

### Post by jim_deadlock on 2010-11-25
I had to reinstall via wubi, it all went well and I'm up and running - during the reinstall I was prompted to delete the existing Ubuntu installation, which I did. However, I have a minor niggle - my boot menu now looks like this:

Windows 7
Ubuntu
Ubuntu

Both of the Ubuntu options boot into the new installation, so is there a way to get rid of one of those options? I like to keep things tidy.

---

### Post by dcstar on 2010-11-25
> **jim_deadlock said:**
> I had to reinstall via wubi, it all went well and I'm up and running - during the reinstall I was prompted to delete the existing Ubuntu installation, which I did. However, I have a minor niggle - my boot menu now looks like this:

Windows 7
Ubuntu
Ubuntu

Both of the Ubuntu options boot into the new installation, so is there a way to get rid of one of those options? I like to keep things tidy.

They are probably different kernel versions, use Synaptic to remove the old kernel.

---

### Post by bcbc on 2010-11-26
Check out this link [http://windows.microsoft.com/en-CA/windows-vista/Change-the-default-operating-system-for-startup-multiboot](http://windows.microsoft.com/en-CA/windows-vista/Change-the-default-operating-system-for-startup-multiboot)

It refers to changing the default OS at startup, but it's in the same place where you'd remove one of the options.

---

### Post by jim_deadlock on 2010-11-26
@dcstar: both options boot with the same kernel (I see the grub menu during boot), I'm pretty sure both options boot exactly the same thing.

@bcbc: that windows control panel method does give the option to change the default boot and delay time, but still there is no option there to remove any of the boot options.

---

### Post by bcbc on 2010-11-26
> **jim_deadlock said:**
> @dcstar: both options boot with the same kernel (I see the grub menu during boot), I'm pretty sure both options boot exactly the same thing.

@bcbc: that windows control panel method does give the option to change the default boot and delay time, but still there is no option there to remove any of the boot options.

Try this: [http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

Or there is a non-microsoft program - easybcd - that can do it as well. [http://www.windowsreference.com/windows-vista/easybcd-edit-boot-configuration-data-bcd-in-windows-vista/](http://www.windowsreference.com/windows-vista/easybcd-edit-boot-configuration-data-bcd-in-windows-vista/)

---

### Post by jim_deadlock on 2010-11-26
Fixed, thank you!

---


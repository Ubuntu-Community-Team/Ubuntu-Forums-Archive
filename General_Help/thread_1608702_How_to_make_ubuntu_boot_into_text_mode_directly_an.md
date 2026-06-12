---
title: "How to make ubuntu boot into text mode directly and login automatically?"
date: 2010-10-29
forum: General Help
---

### Post by Andy Chang on 2010-10-29
I'm new to Ubuntu, and I sure know a little about Shell language. But now I need make my ubuntu boot into text mode directly and login automatically, without entering username/password by manual? I had make ubuntu boot into text mode by changing /etc/default/grub file: **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text" ,** but I don't kown how to make system auto login. I'd like ubuntu login with administrator privilege then run some application automatically.
Anybody can help me?
Thanks

---

### Post by 3Miro on 2010-10-29
> **Andy Chang said:**
> I'd like ubuntu login with administrator privilege then run some application automatically.


In Ubuntu, there is no login with administrative privileges. You can do it, but it is hard and messy (it is disabled by default). If you just want to run some programs at boot time, then you can make your own init script.

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by sisco311 on 2010-10-29
What kind of application(s) do you plan to run automatically?

---

### Post by Andy Chang on 2010-10-30
The test tool I want to run is provided by vendor. Vendor told me if I use RAM large than 2GB, I need add **mem=1024M acpi=off** behind **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text", **namely **"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text *mem=1024M acpi=off*" **
Anybody konw why?

---

### Post by sisco311 on 2010-10-30
From [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)

```

mem=nn[KMG]	                
                                [KNL,BOOT] Force usage of a specific amount of memory
				Amount of memory to be used when the kernel is not able
				to see the whole system memory or for test.
				[X86-32] Use together with memmap= to avoid physical
				address space collisions. Without memmap= PCI devices
				could be placed at addresses belonging to unused RAM.

```

```
acpi=[HW,ACPI,X86]        
                                Advanced Configuration and Power Interface
				Format: { force | off | strict | noirq | rsdt }
				force -- enable ACPI if default was off
				off -- disable ACPI if default was on
				noirq -- do not use ACPI for IRQ routing
				strict -- Be less tolerant of platforms that are not
					strictly ACPI specification compliant.
				rsdt -- prefer RSDT over (default) XSDT
				copy_dsdt -- copy DSDT to memory
	
				See also Documentation/power/pm.txt, pci=noacpi
```

---

### Post by Andy Chang on 2010-10-30
Thanks for reply.
My ubuntu is 9.10 64bit version. Is there some reason to set ACPI=off ?
And if set ACPI=off, I can't turn off the PC by typing **shutdown -h now**. I think it's because most of the modern computers use ACPI method to control the power of PC.
So, what am I to do to solve this problem?

---


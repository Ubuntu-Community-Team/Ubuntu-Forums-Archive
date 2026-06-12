---
title: "startup time (before splashscreen)"
date: 2010-10-04
forum: General Help
---

### Post by _michel_ on 2010-10-04
Hello,
I am looking if it might be possible to speed up the startup time of my linux/laptop - that is from hitting power up to the being prompted for username/password.
So I have two questions....
1)  I thought to look into /var/log/dmesg which seem to indicate what is going during boot sequence. It looks like each entry indicates with a timer how long since startup...
Is it the good place to look at?
2) in my /var/log/dmesg (extract below), there is a 8 seconds gap between two ACPI log entries. After googleing this, it seems to be advaned configuration power interface. I am not sure if anyone can explain the 8 seconds... I was thinking to rebuilding (make xconfig) the kernel but quite unsure what the result would be... Does anyone know if this 8 seconds for ACPI is due to any specific cause?

[snip snip]
[    1.260500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.260572] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.260651] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    9.260301] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    9.260410] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[    9.260517] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 11)

[snip snip]

uname -a
Linux ubuntu 2.6.35 #8 SMP Sat Oct 2 14:58:56 EDT 2010 x86_64 GNU/Linux



Thanks,
_michel

---

### Post by searchfgold6789 on 2010-10-05
It probably needs to wait for some process to start up.
I wouldn't mess with it, unless you can change it back if it messes up something.

---

### Post by Quackers on 2010-10-05
How long is the boot taking at the moment?

---

### Post by _michel_ on 2010-10-06
Currently it takes about 40 seconds to get to the login screen...

---

### Post by CharlesA on 2010-10-06
Install bootchart and see if there is anything taking a long time during boot.

---

### Post by _michel_ on 2010-10-07
Thanks all for helping.... CharlesA bootchart  is great :)
I will close this thread

Thanks again

---


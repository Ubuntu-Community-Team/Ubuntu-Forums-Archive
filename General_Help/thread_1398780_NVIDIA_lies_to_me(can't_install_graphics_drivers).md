---
title: "NVIDIA lies to me(can't install graphics drivers)"
date: 2010-02-04
forum: General Help
---

### Post by OffbeatPatriot on 2010-02-04
I downloaded drivers for my graphics card, renamed the file to drivers.run and ran this command,

sudo sh drivers.run

The command line responded with this,

ERROR: this .run file is intended for the
Linux-x86_64 platform, but you appear to be
running on Linux-x86.  Aborting installation.

But if I look under the system tab in System Monitor I see this,

Processor 0: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
Processor 1: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+

What do I do now?

---

### Post by Mister.Vash on 2010-02-04
Did you install the 64 bit version of ubuntu?  If you didn't, then you are running the 32 bit version and would need those drivers.

Run the following command from the bash prompt
```
uname -m
```

It should output
x86_64 for 64 bit
and I believe
i686 for 32 bit

---

### Post by OffbeatPatriot on 2010-02-05
...I told the guy who installed it that it was 64 bit!!!(uname -m returns i686)

I didn't even know it was possible to install a 32 bit OS on a 64 bit processor.  Is there a way to change it without reinstalling?

---

### Post by Grenage on 2010-02-05
No, You'll need to do a fresh install.  Unless you have 3.5+ GB RAM, don't bother.

---

### Post by stinkeye on 2010-02-05
> **OffbeatPatriot said:**
> I downloaded drivers for my graphics card, renamed the file to drivers.run and ran this command,

sudo sh drivers.run

The command line responded with this,

ERROR: this .run file is intended for the
Linux-x86_64 platform, but you appear to be
running on Linux-x86.  Aborting installation.

But if I look under the system tab in System Monitor I see this,

Processor 0: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
Processor 1: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+

What do I do now?
You have an amd processor which is capable of running a 32 bit or 64 bit O/S.
You installed 32 bit ubuntu O/S.

Either download the 32 bit nvidia drivers
or
install 64 bit ubuntu.

or you may be right and nvidia is lying to you.
They do this every now and then just for fun

---

### Post by 3rdalbum on 2010-02-05
Why are you trying to install the driver from the ".run file"? Ubuntu is fully capable of installing the Nvidia driver from its repositories - go to System > Administration > Hardware Drivers to do this. If you need the latest Nvidia driver, don't fret - just do a Google search for "Nvidia PPA" and add this to your System > Administration > Software Sources > Third Party. Then you can install the "nvidia-glx-195" package for the absolute latest driver.

---

### Post by OffbeatPatriot on 2010-02-05
I once had a real bad experience installing the easy way, but it's working out now.

---


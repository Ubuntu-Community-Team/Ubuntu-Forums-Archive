---
title: "Nvida Driver Installed But Not in Use"
date: 2011-05-01
forum: General Help
---

### Post by ftabor on 2011-05-01
I have installed and removed the Nvidia Drivers via System>Admin>Additional drivers. The dialog tells me that the Current driver is Activated but no in use. I can't seem to find the way to get the driver in use.

I'm running 11.04.

---

### Post by Finalfantasykid on 2011-05-01
I am having the exact same problem.  Help would be greatly appreciated.

I am using NVIDIA 550, what about you?

---

### Post by sgage on 2011-05-02
> **ftabor said:**
> I have installed and removed the Nvidia Drivers via System>Admin>Additional drivers. The dialog tells me that the Current driver is Activated but no in use. I can't seem to find the way to get the driver in use.

I'm running 11.04.

My dialog says the same thing, but the drivers are clearly in use, and working fine. Seems this is a problem that has been popping up for a long time.

---

### Post by wgarcia on 2011-05-02
There is a quite active bug on this, just in case you want to sign up and try to add more information if you have:

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

---

### Post by flipper T on 2011-05-02
it was the same in 10.10

not a 11.04 specific issue

the notification is clearly false as i have been running fallout 3 at 1920x1200 res'n with no problem...clearly the driver must be active.

---

### Post by Ronalddig on 2011-05-02
my problem too .

i see after driver install , i use unity ... so it means its in use

i have nvidia 230 M

---

### Post by ftabor on 2011-05-02
Thanks for the replies. I looked at the bug reports at Launchpad and it is the same bug I have. 

According to ```
sudo lshw -C display
[sudo] password for frank: 
  *-display               
       description: VGA compatible controller
       product: C67 [GeForce 7150M / nForce 630M]
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:d0000000-dfffffff memory:f4000000-f4ffffff memory:c0000000-c001ffff
```

I am using the Nvidia drivers.

---


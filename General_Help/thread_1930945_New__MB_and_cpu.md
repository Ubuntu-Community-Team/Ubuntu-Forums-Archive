---
title: "New  MB and cpu"
date: 2012-02-24
forum: General Help
---

### Post by davidself1001 on 2012-02-24
I am building a new PC with new SSD,MB,graphics card and memory.  Is it possible to plug in my existing program drive as a separate partition and have ubuntu recognize and reconfigure for the new hardware or do i have to reinstall from  scratch?

---

### Post by roelforg on 2012-02-24
As it's (for the os) the same as swapping HD between PC's.
I'd say: Hook it up and see what happens.

---

### Post by idonthaverabbies on 2012-02-24
id say it depends on ya chipset  on the motherboard id say it will be good if it is the same chipset or at least i they use the same drivers

---

### Post by roelforg on 2012-02-24
> **idonthaverabbies said:**
> id say it depends on ya chipset  on the motherboard id say it will be good if it is the same chipset or at least i they use the same drivers
Shouldn't matter,
i switched HD's between pc's with different chipsets/video-cards/<insert other hw here> and linux didn't care.
The thing has so much modules (drivers).

EDIT: Well, i did keep emptying /etc/udev/rules.d/70-persistent-net.rules so it would see the NIC as eth0
EDIT2: i only did that right before changing HD (otherwise the boot will take forever whilst it waits for a NIC the pc doesn't have).

---

### Post by idonthaverabbies on 2012-02-24
> **roelforg said:**
> Shouldn't matter,
i switched HD's between pc's with different chipsets/video-cards/<insert other hw here> and linux didn't care.
The thing has so much modules (drivers).

EDIT: Well, i did keep emptying /etc/udev/rules.d/70-persistent-net.rules so it would see the NIC as eth0

thats cool windows sure cares im geting a new hardrive ina few weeks finaly updating
 to ssd. only 64 gigs but that should be good for os

---

### Post by CharlesA on 2012-02-24
I just threw the hard drive from my old server (Dual-core pentium) into the new one (Z68 Mobo with an i7) and it started up fine.
All I did was edit /etc/udev/rules.d/70-persistent-net.rules to turn eth1 back into eth0.

---

### Post by roelforg on 2012-02-24
> **CharlesA said:**
> I just threw the hard drive from my old server (Dual-core pentium) into the new one (Z68 Mobo with an i7) and it started up fine.
All I did was edit /etc/udev/rules.d/70-persistent-net.rules to turn eth1 back into eth0.
I just comment out the lines, udev will figure the rest out on it's own.

---

### Post by CharlesA on 2012-02-24
> **roelforg said:**
> I just comment out the lines, udev will figure the rest out on it's own.
Good idea. I just delete them and reboot.

---

### Post by dcstar on 2012-02-24
> **davidself1001 said:**
> I am building a new PC with new SSD,MB,graphics card and memory.  Is it possible to plug in my existing program drive as a separate partition and have ubuntu recognize and reconfigure for the new hardware or do i have to reinstall from  scratch?

The video drivers are the main obstacle, you may need to remove any proprietary drivers prior to changing and then let them be detected and installed on the new hardware.

I just added a new ATI based PCI-E card to my PC to replace the lower performance ATI on-board hardware and I had to blow away the existing config and reinstall the driver to use the new hardware.

---

### Post by CatKiller on 2012-02-25
The other thing to consider is whether your new processor is 64-bit. If your old install was 32-bit it will still work with your 64-bit processor, but you might see some performance improvements re-installing 64-bit.

---


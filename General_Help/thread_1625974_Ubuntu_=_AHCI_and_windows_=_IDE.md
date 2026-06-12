---
title: "Ubuntu = AHCI and windows = IDE"
date: 2010-11-19
forum: General Help
---

### Post by krelverehan on 2010-11-19
I am having this problem. I had a working, installed version of Win xp on my hdd and I just installed ubuntu 10.10 on a partition I had next to it. Now I guess back when I installed win xp I made it boot under IDE mode. And of course the grub for ubuntu only works in ahci mode.

How can I boot onto my windows partion to change the drivers to allow me to boot under ahci mode (I have seen tutorials on how to do this)? Because if I boot under ide mode my ubuntu grub won't boot and nothing loads :(

I really would just like to find a simpler fix rather than reinstalling my windows partition.

I have a gigabyte 880GM-UD2H mobo.

Thanks!
-KV

---

### Post by Bitrate on 2010-11-19
Why can't you just enable IDE for both operating systems ?  Ubuntu works fine with regular IDE and AHCI doesn't really offer much performance gain unless you have heavy disk workloads. In some cases it's slower than IDE.

---

### Post by krelverehan on 2010-11-19
> **Bitrate said:**
> Why can't you just enable IDE for both operating systems ?  Ubuntu works fine with regular IDE and AHCI doesn't really offer much performance gain unless you have heavy disk workloads. In some cases it's slower than IDE.

How do I get ubuntu to work under IDE?

---

### Post by dcstar on 2010-11-19
> **krelverehan said:**
> 
.........
How can I boot onto my windows partion to change the drivers to allow me to boot under ahci mode (I have seen tutorials on how to do this)? 
.........

Boot off a Live CD and see if you can boot the Windows Partition from that.

---

### Post by dcstar on 2010-11-19
> **krelverehan said:**
> How do I get ubuntu to work under IDE?

Make **100% sure** that your BIOS is set to boot off the Ubuntu disk when you change to IDE mode.

---

### Post by krelverehan on 2010-11-19
> **dcstar said:**
> Make **100% sure** that your BIOS is set to boot off the Ubuntu disk when you change to IDE mode.

Whenever I try to change the BIOS to IDE mode, I get grub rescue...

---

### Post by krelverehan on 2010-11-19
> **dcstar said:**
> Boot off a Live CD and see if you can boot the Windows Partition from that.

If that works, that would be great... How would I go about doing that?

---

### Post by krelverehan on 2010-11-20
I feel like I am so close to finding an answer.

Whenever I boot under IDE mode grub says: "Cannot find patition" and goes right into grub rescue... and if I boot under AHCI mode I can get ubuntu to boot, but I can't access my windows xp partition.

I either need to know how to boot grub under IDE mode, or I need to figure out how to boot my windows partition from the live CD.

Any help would be great!
Thanks again!
-KV

---

### Post by oldfred on 2010-11-20
I had the opposite problem as I never installed the extra drivers in XP, but Ubuntu booted in both modes.

Some have used these terms for BIOS settings:

BIOS should be set for IDE compatibility mode
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility

---


---
title: "Hard lockups in 9.1 on Asus M2A-VM"
date: 2009-11-26
forum: General Help
---

### Post by Shplad on 2009-11-26
Hi Friends:

I just picked up a used PC on which I keep getting random crashes when trying to run Ubuntu 9.1 (32-bit). 
I get (seemingly random) hard lockups after a few seconds to a few minutes after booting. 
Often, moving the mouse seems to trigger the crashes.

BTW, my Linux skills are very beginner level, but I have many years of experience
as a Windows and hardware technician.


The Machine:
Asus M2A-VM motherboard (AMD 690G chipset) BIOS 2302

AMD Athlon 64 x2 5000+ CPU with stock cooler (yuck!)

2x1GB Mushkin Enhanced RAM (2GBEM2-6400)

2x1GB OCZ PC26400 RAM  (OCZ2VU8002GK)

Galaxy GeForce 8400GS (Nvidia) PCIe graphics card

400W Enermax power supply

I got similar crashes when running the LiveCD portion of the Ubuntu 9.1 disc.
However, see below.

What I've tried or checked so far:
======================
MD5 check of Ubuntu CD-checks out fine. I burned a second CD and tried it
just in case-same problems. All CDs were verified after burning on a very stable machine.

Core CPU temps measure about 43deg. and the motherboard temp is about 38. 
While those aren't great, it would likely rule out overheating as the source of the problem.
I will definitely be switching the crappy stock cooler out for a better third party cooler.

Power supply voltages are fine-I checked them. 

The machine runs Windows XP just fine for a couple of hours at a time.

I Googled various solutions using M2A-VM and Ubuntu as search terms. The workaround which seemed to be 
the most appropriate  was adding these kernel options at boot time: 

```
pci=nomsi irqpoll noapic acpi=off
```taken from this thread on these same forums
[http://ubuntuforums.org/showthread.php?t=435075](http://ubuntuforums.org/showthread.php?t=435075)

When I tried this using the LiveCD function, it seemed to work.  Ubuntu ran very quickly from CD, 
and I had no crashing at all.

So I figured if it stopped the problem when booting LiveCD, it might stop the problem
when booting from a hard drive installation of the same OS.

So I tried to implement the same kernel options on the hard drive install. That's where I got stuck. 
The person who originally reported the above solution was using Ubuntu 7.04 and therefore GRUB v1.
But my Ubuntu 9.1 seems to be using GRUB2.

I tried to see if the instructions for GRUB1 would be similar. I hit "e" (or SHIFT) when I saw the GRUB prompt
during bootup,  and highlighted the first boot option in the menu. I used the minimal editing environment 
(or so I thought) to add the kernel options above. But hitting "B" did not boot anything.
It just typed a "B". 

I hit Ctrl-X, as the screen listed to boot, but I'm pretty sure it booted without those kernel options. 
I never found out, as it would just complain and crash every time. I know I should've checked the logs, 
but Linux has so many logs, I didn't know which one to check. I'll gratefully post them, if asked.

I tried changing the kernel options by booting from the CD and editing the correct file on the hard drive,
but I was not sure, even after reading some of the documentation which was the correct file to edit. 

I would appreciate any help with this, starting with how to edit the correct file on the hard drive to 
tell Ubuntu to boot with above kernel options.

I've also seen a number of very long threads here talking about (apparently) random frequent lockups in Ubuntu 9.1
on various types of hardware.  I recognize the pattern as possibly similar to the one I'm experiencing. 
I'm hoping it's not a general problem, as that would mean I'd have to depend on waiting for the changes 
to be fixed in a patch or the next release.



Thanks in advance for any help.


Shplad

---

### Post by TorpedoJavi on 2009-11-28
Try to deactivate Virtualization and the other processor options in the BIOS.

I have the same motherboard, and it works well after deactivate them.

And the second problem that you will have is the video driver. Use "radeonhd", it also works very well.

My ubuntu it's totally stable now. Update ubuntu automatically after install it.

Sorry for my poor English.

---

### Post by Shplad on 2009-11-28
TorpedoJavi:

Thanks for your reply. Virtualization and other processor options are already
disabled.

I'm not using the ATI onboard graphics. As above, I'm using a Galaxy PCIe nvidia-based card.

Any more suggestions?


Shplad




> **TorpedoJavi said:**
> Try to deactivate Virtualization and the other processor options in the BIOS.

I have the same motherboard, and it works well after deactivate them.

And the second problem that you will have is the video driver. Use "radeonhd", it also works very well.

My ubuntu it's totally stable now. Update ubuntu automatically after install it.

Sorry for my poor English.

---

### Post by clhsharky on 2009-11-28
HI

Have you tried pulling 2 sticks of memory, some boards don't like mixed modules, especially across all 4 dimm sockets. Just to rule that out, mixed memory has all way been hit or miss.

Sharky

---

### Post by TorpedoJavi on 2009-11-29
I also put the suspend fuction in S3 only, SATA emulation to AHCI, and deactivate a function that reduces the processor multiplier (I don't remeber that name).

My system is currently using the last ubuntu kernel (autoupdated) and it is totally stable.

You can also try to use the onboard graphics card, removing the Nvida.

My motherboard is the asus m2a-vm hdmi, but I think they have the same main components.

Good luck.

> **Shplad said:**
> TorpedoJavi:

Thanks for your reply. Virtualization and other processor options are already
disabled.

I'm not using the ATI onboard graphics. As above, I'm using a Galaxy PCIe nvidia-based card.

Any more suggestions?


Shplad

---

### Post by TorpedoJavi on 2009-11-29
Oooops, and I forget saying you that my Ubuntu version is 9.10 64 bits. Try the 64 bits version.

---

### Post by Shplad on 2009-12-02
Thanks for all the suggestions. I did end up removing 2 of the 4 dimms. Turns out there were 2 diff. sets of dimms, both
diff brands and diff. timings. Genius.

The machine may have multiple problems though, the likes of which I've never seen in working with PCs.

I'm still eliminating the possibility of hardware problems. Symptoms are intermittent, 
and not even consistently the same symptoms.

I'll try those things and get back to you in a few days.  Thanks for all the help, and I'd appreciate it if you'd
stay with me on this one. I'm seriously losing hair over this. ;-)


Shplad

---


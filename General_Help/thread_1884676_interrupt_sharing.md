---
title: "interrupt sharing?"
date: 2011-11-21
forum: General Help
---

### Post by Cool Javelin on 2011-11-21
Hi hardware experts.

I have a 3 fold question, 

#1, can Ubuntu (specifically 10.10) have more then one device attached to a single interrupt? I have 2 LPT ports, and one port can only be set to IRQ 5 (currently used for my sound device) or IRQ 7 (currently used for my other LPT port.)

#2, how do I go about telling Ubuntu I want to use a different IRQ for a device. For example, I might be able to change my sound to another interrupt, so I would need to inform Ubuntu I have done that.

#3, How do I get a list of interrupts Ubuntu knows about now, so when I add hardware I can avoid conflicts.

I have used lspci, lshw, and hardinfo.

Hardinfo reports the devices, and some DMA channels, but I can't find where it might show me the IRQ usage.

Thanks, Mark.

---

### Post by haqking on 2011-11-21
> **Cool Javelin said:**
> Hi hardware experts.

I have a 3 fold question, 

#1, can Ubuntu (specifically 10.10) have more then one device attached to a single interrupt? I have 2 LPT ports, and one port can only be set to IRQ 5 (currently used for my sound device) or IRQ 7 (currently used for my other LPT port.)

#2, how do I go about telling Ubuntu I want to use a different IRQ for a device. For example, I might be able to change my sound to another interrupt, so I would need to inform Ubuntu I have done that.

#3, How do I get a list of interrupts Ubuntu knows about now, so when I add hardware I can avoid conflicts.

I have used lspci, lshw, and hardinfo.

Hardinfo reports the devices, and some DMA channels, but I can't find where it might show me the IRQ usage.

Thanks, Mark.


IO addresses ```
cat /proc/ioports
```

DMA ```
cat /proc/dma
```

IRQ ```
cat /proc/interrupts
```

As for conflicts, with PCI there shouldnt be any as they are more easily shared.

do you still have ISA devices then ?

---

### Post by Cool Javelin on 2011-11-21
Thanks, haqking.

Yes, I do have one ISA card. My Dell XPS T600 MB has a few PCI slots, and one slot can be either a PCI or ISA.

I attached an ISA parallel/serial controller, and it did not show up in hardinfo. After using the BIOS to reset the PCI table, I now see the 2 new ports. but...

Before resetting the PCI table, my sound card was on IRQ 5 and worked fine.

After doing the reset, I find my sound card changed to IRQ3. IRQ5 is now free but my sound no longer works properly.

In the BIOS I found I could reserve IRQ's and did so for IRQ3 (hopefully for the ISA COM2) and IRQ5 (hoping I could use the ISA LPT2 there. [still don't know how to tell Linux about that])

I did another PCI reset in the BIOS.

Now, the sound is assigned to IRQ9 but still doesn't work.

I think I need to pull the ISA card out, and diagnose the sound issue before going on.

I have lots of older ISA LPT and COM cards and hate the idea of having to go out and buy a PCI card to get past this issue.

I am going to put this thread on pause for a while till I get the sound working.

Those 3 things you mentioned will help.

Thanks again, Mark.

---


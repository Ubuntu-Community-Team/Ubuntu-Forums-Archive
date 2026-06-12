---
title: "(beginner) Ubuntu won't start"
date: 2010-12-22
forum: General Help
---

### Post by ajmcintire on 2010-12-22
After I successfully installed Ubuntu on my machine, I did the updates that came up successfully, it did a successful reboot and then there was a prompt to install proprietary drivers for my Nvidia graphics card on the HP laptop. NVIDIA accelerated graphics driver (version current) [Recommended]
 
Everything was fine for a couple of bootups but not anymore. I can't boot up normally and I get the following in a black screen with white letters:
 
_________________________________________
 
ubuntu 10.10 <computer name> tty1 
<computer name> login: [ 34.725607] irq 17: nobody cared (try booting with the "irqpoll" option)
 
_________________________________________
 
Every once in a while I can boot up normally for some reason but this is what I get now when I try most of the time. Help please...
 
 
System info:
HP laptop
1GB DDR2 667
Intel Meron T7000
Nvidia 256MB
Ubuntu 10.10 (maverick)

---

### Post by ajmcintire on 2010-12-22
Some more information would be that it says on my screen this time exactly (the numbers look a little different but the IRQ number is the same -- whatever that means):
 
_________________________________________
 
ubuntu 10.10 <computer name> tty1 
<computer name> login: [ 30.289654] irq 17: nobody cared (try booting with the "irqpoll" option)
[ 30.289841] handlers:
[ 30.289932] [<c0470160>] (usb_hcd_irq+0x0/0x80)
[ 30.290199] [<f83955c0>] (yenta_interrupt+0x0/0xd0 [yenta_socket])
[30.290478] [<c0450d20>] (ata_sff_interrupt+0x0/0x1f0)
[ 30.290747] Disabling IRQ #17
 
_________________________________________
 
Then, it seems like nothing happens for a long time then I get a bunch of messages to the effect of ".....iwlagn 0000:10:00.0: Error sending REPLY_.....time out after 500ms."

---


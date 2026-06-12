---
title: "Trying to get Ubuntu to boot on laptop with dead onboard graphics."
date: 2011-10-28
forum: General Help
---

### Post by gurum on 2011-10-28
So my Dell XPS m1530 laptop had a faulty Nvidia m8400 GS which decided to completely fail earlier this year. In a completely separate incident, my LCD ribbon cable was faulty and when trying to replace it, I accidentally killed the actual LCD (I think).

Now I'm trying to get any OS to boot on it with an external display. A major problem is that every 3rd character on the monitor is a random character, so it's extremely difficult to read text on screen. This happens from the very beginning of the boot process, and when installing ubuntu it persists until the graphical interface loads.

I actually bought an [expresscard &#8594; PCI-E adapter]("http://www.hwtools.net/adapter/pe4h.html") to use with an XFX HD5670 that I have. I attached a display to the VGA output on my laptop, and another to the VGA output from the HD5670. During boot to installation cds, my display attached to the HD5670 never mirrors the laptop output. 

For Windows, I have never seen my HD5670 output working at all.

For booting to linux distros, the HD5670 output provides different information (sometimes the laptop output will just be a flashing text cursor, while the HD5670 will display an error stack trace), and it feels like the HD5670's output is recognized as the primary display. Output from the HD5670 is flawless, no random characters like the laptop output.

Results of testing with various OSes:

**OS** | Result

**Windows 7 64-bit** | This actually sort of works, but the display is messed up and my external graphics won't work on 64-bit. 

**Windows 7/Vista 32-bit** | When trying to install either of these, I get to the first graphical interface for the setup, but its either frozen or won't recognize my mouse/keyboard 

**Windows XP 32-bit** | Installation for this doesn't get to a GUI, it stays in a commandline interface (which means I get every third character being a random character, which is difficult to read). I think I can make out a "Setup cannot find hard disk drive." 

**Ubuntu 11.04** | Boots to the graphical load screen on the installation disk and this screen shows up very nicely on the HD6750 output. When the graphical installation setup is loaded (liveCD environment), it is only shown on the laptop output (which is fine and probably normal for an OS setup) and installation proceeds perfectly fine. After installing Ubuntu 11.04, I can't boot to it properly - I get a list of module load fail/pass, and it looks a bit different every time; pretty sure that's a modprobe error. I can get to terminal, but I can't start GDM. 

**Ubuntu 11.10, Ubuntu 10.10, Linux Mint 11, Fedora Core 16beta, Arch Linux 2011.09.18** | Won't even get through installation setup. 

[B]
**From this, Ubuntu 11.04 seems to show the most promise, since I've seen the HD5670 output working on it, and I can at least get to terminal.**[/B]

Any help or suggestions would be appreciated. This is a pretty unique problem I think, but I'm going to keep trying to figure out a solution.

Sorry for the huge wall of text, and thank you for taking the time to read all that =). Let me know if I should provide an additional information.

---

### Post by Blaqksheep on 2011-10-28
What does your BIOS have to say about your bolt-on GPU?  Will it boot through if you disconnect the GPU and try it purely with your laptop's output?

---

### Post by gurum on 2011-10-28
Interesting, I hadn't considered removing my m8400... I'll look up how to remove it and try that, thank you!

Edit: whoops, I misread that. My BIOS screen is pretty unreadable because of that random character glitch, but I don't think the HD5670 card is recognized right away. Without the GPU, I just get a flashing text cursor on the laptop output =/.

---

### Post by Blaqksheep on 2011-10-28
The m8400 might not be removable depending on how it's placed.  If it is, try stuff!  I wouldn't do it in this order.  xD

-Both [m8400](http://bizsupport1.austin.hp.com/bc/docs/support/SupportDocument/c01420085/c02069874.jpg) and [HD5670](http://www.amd.com/PublishingImages/Public/Photograph_ProductShots/PNG/40819.png) use PCIe x16 slots.  See if you can't jam the 5670 in the motherboard's primary slot.  That could fix your problem outright, but the size difference will be your killer.

-Try the 5670 **without** the m8400 and see if your mobo can pick it up right away.

-Play cryptographer and decipher the gibberish to read your BIOS.

If you can tell me if you have a PCIe x1 slot I might have another suggestion for you.

---

### Post by gurum on 2011-10-28
Sorry, this is actually the mobile Nvidia 8400M GS for laptops. The HD5670 is a desktop graphics card that I'm running through a PCI-E to expresscard converter. The 8400M is integrated onto the motherboard, so I don't think I can remove it =/.

---

### Post by dariusdwtt on 2011-10-28
What are you trying to achieve? (not meant to sound rude, it would just be good for us to know.)

Honestly, if I were you, I'd take out the HDD, put it into an enclosure, plug it into another PC, and get whatever I need. Then I would take the old laptop and throw it away. I don't believe in the "disposable culture", but some times, some things just aren't worth fixing any more.

Good luck tho, coz if you're anything like me, you probably won't stop till you get it running :P

---

### Post by Blaqksheep on 2011-10-28
Bah, was hoping they were lazy and just crammed it in.

I did have another suggestion, but I'm afraid I've had to swap it for a new one.  I went back and saw a part my brain apparently just ignored.

> Now I'm trying to get any OS to boot on it with an external display. A major problem is that every 3rd character on the monitor is a random character, so it's extremely difficult to read text on screen. **This happens from the very beginning of the boot process, and when installing ubuntu it persists until the graphical interface loads.**

That changes things a bit

Locate the following items:

1)  Motherboard (I have to include it, I don't think you're dumb)
2)  RAM (See above comment)
3)  CMOS Battery (Just a little button cell battery)
4)  BIOS Chip
5)  The nVidia culprit

Try this process as a diagnostic:

1)  Remove the CMOS Battery, wait 5-10 minutes, then replace it.
2)  Ensure that the nVidia card is not connected to anything but the motherboard then connect a monitor to your 5670 and boot.
3)  Enter F2 BIOS Setup.  If it's still unreadable, exit your BIOS and attempt to boot Ubuntu.  If it's readable, go to step 11.
4)  When/if you reach GRUB, go ahead and run Memtest86.
5)  Even if it's unreadable, let it run.  If it reports errors, post them.  If not, reboot and attempt to enter Ubuntu.
6)  If you still can't get to the login screen, shut down.
7)  Remove all of your ram sticks and place only one in and boot.
8)  Enter F2 BIOS Setup and see if there is any anomaly or change.
9)  Repeat step 7 with a different stick until you've tested all of them.  If you only have one, or if it's convenient, place a stick from a different laptop in.
10)  If you can read your BIOS, go to step 11.  If not, go to last step.
11)  Carefully read your BIOS's analysis of your hardware.  If there are any anomalies (showing 3GB RAM when you have 4GB, or showing that you don't have an optical drive) post them here.
12)  Make a list of all of the options you can change and post them here.
13)  Wait for someone to reply.  =P
14)  If all of these tests are inconclusive, it's probably motherboard failure.  If that's the case, then you're looking at a new laptop.  =(

---


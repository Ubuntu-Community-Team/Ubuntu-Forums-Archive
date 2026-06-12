---
title: "Can't select boot device or get to BIOS"
date: 2011-12-19
forum: General Help
---

### Post by Bucky Ball on 2011-12-19
Hi all,

I have posted about this before and no-one had any ideas but the plot thickens and thought this might elicit some new ideas. 

The **original problem** was that when I boot my laptop for the first time (Toshiba Satellite L510, Ubuntu 10.10 ... in this case) I can't choose which Ubuntu kernel to boot, the laptop keyboard is non-responsive, so I have to go with the kernel on top of the list. Once booted in, I can restart and select whatever I want. Strange. Only occurs when I switch on machine. 
 
Anyhow, I have now discovered a **new oddity** which is related to the original problem. I have created a USB install of Peppermint. Thought I'd give it a try. When I restart my machine, regardless of what I press, it goes straight to the grub kernel selection. I can't get to BIOS or select which device to boot from. Naturally, I want to boot from the USB. I get no options (the 'official' Toshiba start up screen telling me which keys to press to get to BIOS and choose device, etc never appears). And, of course, if I go for a complete shutdown and then restart, the old problem persists; I have no access via keyboard. That is dead and we go to the first kernel on the list again (not good as I have a lot of kernels installed).

**Bottom line: **Regardless of startup or restart, machine goes directly to my grub menu list and bypasses the option to go for BIOS or choose a boot device by hitting F12. Ubuntu, or some aspect of it, seems to just take over the show right from boot.

* **New thoughts**: Wondering if anything in my /etc/default/grub might be causing this problem ...

```
GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
GRUB_CMDLINE_LINUX="acpi=copy_dsdt"
```Tried 'Delete' key for the BIOS but nothing. Same as the F12 for choosing boot device; no response. Straight to kernel list. ;(

---

### Post by kngsze on 2011-12-19
Surely if you can't even access BIOS or boot device settings, it would point to a problem with your keyboard/BIOS at start-up - BIOS not detecting the input device properly. As they are pre-boot I can only think it must be there somewhere. Does the BIOS need flashing? I build tons of Tosh's at work and the BIOS's need flashing all the time for little things like this.

Wouldn't like to comment on GRUB side of things as I'm a newbie, but my hardware knowledge is pretty good :)

---

### Post by decrepit on 2011-12-19
Agree with kngsze, I don't see how your problem can be grub/ubuntu related. Your problem is before grub gets into the act.

---

### Post by Bucky Ball on 2011-12-19
> **kngsze said:**
> Surely if you can't even access BIOS or boot device settings, it would point to a problem with your keyboard/BIOS at start-up - BIOS not detecting the input device properly. As they are pre-boot I can only think it must be there somewhere. Does the BIOS need flashing? I build tons of Tosh's at work and the BIOS's need flashing all the time for little things like this.

Wouldn't like to comment on GRUB side of things as I'm a newbie, but my hardware knowledge is pretty good :)

BIOS was latest last time I looked. I'll look again. I just haven't needed to boot into BIOS for ages and just noticed the problem when I needed to boot from USB. It was all normal last time I needed to do it. Odd how the option just disappeared like that which is why I figured it may be one of the Ubuntu installs (I have 11.04, 10.10, and 10.04 LTS and heaps of diff kernels).

---

### Post by Bucky Ball on 2011-12-19
Nope, latest BIOS for this model; 1.40

Rules that out perhaps. Think something happened one install and I just didn't notice. Attempting to find other explanations ...

---

### Post by westie457 on 2011-12-19
Have you tried to reset the Bios by a complete power down of the laptop?

That is shutdown disconnect the power cord, remove the battery and possibly hold the power button down for 30 seconds. 

Reconnect everything then power up.

That might work and is the only thing I can think of to get you to be able to access the bios again.

This is something I had to use when messing around with the Windows 8 developer release a couple of months ago.

---

### Post by Bucky Ball on 2011-12-19
> **westie457 said:**
> ... shutdown disconnect the power cord, remove the battery and possibly hold the power button down for 30 seconds. 

Reconnect everything then power up.

Did the trick. Thanks westie457 for an obscure fix that has taken me forever to figure out from the original issue. I've been pondering this problem and putting up with it for long time. Fixed locked keyboard from a complete cold start and I can get into BIOS/hit F12 to choose boot device. ;)

My trouble now is that when I set to boot from USB, either using the BIOS or F12 method, it boots from the hard drive anyway! Think that is problems with Peppermint installer on the USB dongle and the subject of another thread if required. 

For now, thanks for everyone's input, and consider this thread solved.

---

### Post by westie457 on 2011-12-19
The last Toshiba bios I looked at was similar to the one just fixed. It is quite possible the USB hard drive is listed in the bios under the hard drive section. That is where the change should be made.

---

### Post by worksofcraft on 2011-12-19
You have to go into the bios and enable "legacy USB" support.

Basically Microsoft included USB support in their boot loader and so bios manufacturer's took it out. However Grub doesn't have USB support and needs your bios to do it.

---

### Post by Bucky Ball on 2011-12-19
> **westie457 said:**
> The last Toshiba bios I looked at was similar to the one just fixed. It is quite possible the USB hard drive is listed in the bios under the hard drive section. That is where the change should be made.

Cheers. Fully aware of that.

What is happening is if I restart and set either BIOS or hit F12 and select USB, I go straight to the grub list. If I shut the machine down completely and then power up and select BIOS or F12 then boots fine from USB. Go figure ...

I'm happy with the outcome, this odd glitch certainly not an issue for me, am typing this from Peppermint, and kinda like what I am seeing here. Not sure I love Chromium though and Peppermint is not for the open source purist, but connected to network no probs and everything is working just fine 'out of the box' from the USB dongle. I used UNetbootin to create it.

---


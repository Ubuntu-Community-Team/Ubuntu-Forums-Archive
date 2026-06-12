---
title: "trying to install xfi soundblaster driver"
date: 2009-06-29
forum: General Help
---

### Post by badperson on 2009-06-29
Hi,
I tried compiling and installing the driver from [creative]("http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=17791&prodName=PCI+Express+X-Fi+Titanium+Fatal1ty+Pro+Series")...


The instructions are:
> Quick install


=============

In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install

Does it matter what folder the source files are in? I just crated a sub off my home folder. 

Sorry if this is a basic question. 
bp

---

### Post by linuxmagick on 2009-06-29
I've got a PCI-E Fatal1ty Pro card myself.  Once I downloaded the drivers, I had to do a ```
lspci -v
```

In the output there should be something that looks like:

02:00.0 Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
        Subsystem: Creative Labs Device 0043      

The important part above is the last number (in my case 0043).  You'll need to go into the Creative driver directory and edit the file ctdrv.h.  Then change the line like:

define PCI_SUBSYS_CREATIVE_SB0880      0x0043 (be sure to use the right number from above here)

Once I did that I ran the same commands you have above and it installed nicely.

---

### Post by badperson on 2009-06-29
thanks, that's still not working...do I need to restart?
here's the output for my soundcard:

> 07:00.0 Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
	Subsystem: Creative Labs Device 0043
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
	Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel modules: ctxfi


Here's the line you mentioned:
> #define PCI_SUBSYS_CREATIVE_SB0880	0x0043

---

### Post by linuxmagick on 2009-06-29
If you didn't get any errors during the make install step, then you can either reboot or do ```
sudo modprobe ctxfi
```

---

### Post by badperson on 2009-06-30
That did it!!! I'm so happy, for months, the only thing I didn't like about my linux system was I couldn't get sound, thanks!!
bp:guitar:

---

### Post by linuxmagick on 2009-06-30
Don't mention it.  I'm glad you got it working :)

---

### Post by starbase1 on 2009-07-30
I tried the same thing, (as I have the same problem), but it did not seem to work...

To check, here's my output:

03:00.0 Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
	Subsystem: Creative Labs Device 0043
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at fb9f0000 (64-bit, non-prefetchable) [size=64K]
	Memory at fb600000 (64-bit, non-prefetchable) [size=2M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

And here's what I did with ctdrv.h

/**
 * Copyright (C) 2008, Creative Technology Ltd. All Rights Reserved.
 *
 * This source file is released under GPL v2 license (no other versions).
 * See the COPYING file included in the main directory of this source
 * distribution for the license terms and conditions.
 *
 * @file    ctdrv.h
 * 
 * @breaf   
 * This file contains the definition of the programming interfaces that
 * provided by the driver module. 
 *
 * @author Liu Chun
 * 
 */

#ifndef CTDRV_H
#define CTDRV_H

#define PCI_VENDOR_CREATIVE		0x1102
#define PCI_DEVICE_CREATIVE_20K1	0x0005
#define PCI_DEVICE_CREATIVE_20K2	0x000B
#define PCI_SUBVENDOR_CREATIVE		0x1102
#define PCI_SUBSYS_CREATIVE_SB0760	0x0024
#define PCI_SUBSYS_CREATIVE_SB0880	0x0043
#define PCI_SUBSYS_CREATIVE_HENDRIX	0x6000

#define CT_XFI_DMA_MASK			0xffffffffUL /* 32 bits */

#endif /* CTDRV_H */

Have I made a mistake?
Thanks,
Nick

---

### Post by badperson on 2009-08-13
now my sound isn't working either....
bp

---

### Post by rayman121985 on 2009-08-17
I have a X-Fi extreme audio...I hope this works I will try it tonight! 

::rayman::

---

### Post by badperson on 2009-08-18
I just tried re-installing...no luck. This must have been caused by a conflict with an upgrade...anyone have any ideas? 


Here is the current output from lspci -v
> 07:00.0 Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
	Subsystem: Creative Labs Device 0043
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
	Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>


From my original post above, the lspci -v output had this line which is now missing
> Kernel modules: ctxfi 

is that a module I can install? 

I also found [this link ]("http://www.google.com/cse?cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8&q=Kernel+modules%3A+ctxfi+&sa=Search")which looks like a similar issue, I guess from a kernel upgrade.
bp

---

### Post by Clon89 on 2009-08-25
Thanks linuxmagick :) I changed the code 0x0041 to 0x0043 in the ctdrv.h file and reinstalled. Now I have sound in 9.04 :guitar:

---

### Post by badperson on 2009-08-25
are you updated to the latest kernel? 
bp

---

### Post by badperson on 2009-09-22
Has anyone got this card to work on the newest kernel?
bp

---

### Post by badperson on 2009-11-01
Okay, just a shot in the dark here...I'm upgrading to 9.10 right now. I don't suppose anyone has a titanium x-fi card working in that version, do they? 

Also, I posted this in another thread, but are there any pci-express cards that are known to work in linux and vista?
bp

---

### Post by badperson on 2009-11-01
answering my own question here...the upgrade to 9.10 solved the issue! Man, what a saga with this sound card.

---

### Post by wdiz on 2009-11-01
> **badperson said:**
> answering my own question here...the upgrade to 9.10 solved the issue! Man, what a saga with this sound card.
Does the Optical out working ?
It was working for me with 9.04 with the X-Fi Titanium driver compilation...but with the 9.10 it doesn't.

---

### Post by badperson on 2009-11-01
never tried the optical, I'm just using analog out to speakers...sorry. bp

---


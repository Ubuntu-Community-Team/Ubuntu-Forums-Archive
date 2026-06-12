---
title: "Virtual Box question"
date: 2010-08-01
forum: General Help
---

### Post by NobleSavage on 2010-08-01
If I have 32bit Ubuntu running with VirtualBox can I install a Windows 64bit OS?

Thanks in advance!

---

### Post by Dustin2128 on 2010-08-01
I'm pretty sure you can't, assuming you're running the 32 bit OS on 64 bit hardware. You definitely can't if your processor is 32 bit.

---

### Post by NobleSavage on 2010-08-01
> **Dustin2128 said:**
> I'm pretty sure you can't, assuming you're running the 32 bit OS on 64 bit hardware. You definitely can't if your processor is 32 bit.


Well, I'm about to build a new box and it will have a 64bit processor. I'm trying to decide between installing Ubuntu 32bit or 64bit.  I have a copy of Win 7 pro 64 bit and I'd like to be able to run that in virtual box. 

So it sounds like you are saying I should go with Ubuntu 64 bit.

---

### Post by fuzetsu490 on 2010-08-01
This is from the virtualbox manual. It seems like its possible but definitely more complicated than running it on a 64bit host.

> Starting with Version 2.0, VirtualBox also supports 64-bit guest operating systems.
Starting with Version 2.1, you can even run 64-bit guests on a 32-bit host operating
system, so long as you have sufficient hardware.
In particular, 64-bit guests are supported under the following conditions:
1. You need a 64-bit processor with hardware virtualization support (see chapter
1.2, Software vs. hardware virtualization (VT-x and AMD-V), page 11).
2. You must enable hardware virtualization for the particular VM for which you
want 64-bit support; software virtualization is not supported for 64-bit VMs.
3. If you want to use 64-bit guest support on a 32-bit host operating system, you
must also select a 64-bit operating system for the particular VM. Since supporting
64 bits on 32-bit hosts incurs additional overhead, VirtualBox only enables this
support upon explicit request.
On 64-bit hosts, 64-bit guest support is always enabled, so you can simply install
a 64-bit operating system in the guest.
Warning: On any host, you should enable the I/O APIC for virtual machines
that you intend to use in 64-bit mode. This is especially true for 64-bit Win-
dows VMs. See chapter 3.7.1.2, “Advanced” tab, page 46. In addition, for
64-bit Windows guests, you should make sure that the VM uses the Intel net-
working device, since there is no 64-bit driver support for the AMD PCNet
card; see chapter 6.1, Virtual networking hardware, page 82.

---

### Post by randumnumber on 2010-08-01
If your hardware is 64 bit and you are running the 64 bit ubuntu you can def. run a 64 bit application in VBox. I use the 64bit 10.04 with not issues.

Edit. Looks like post #4 answers this.

---

### Post by Dustin2128 on 2010-08-01
> **NobleSavage said:**
> Well, I'm about to build a new box and it will have a 64bit processor. I'm trying to decide between installing Ubuntu 32bit or 64bit.  I have a copy of Win 7 pro 64 bit and I'd like to be able to run that in virtual box. 

So it sounds like you are saying I should go with Ubuntu 64 bit.
yeah, its not as bad as people are led to believe, nor is it as bad as it used to be. Its 2010, not 2007, use a 64 bit OS on 64 bit hardware.

---

### Post by fuzetsu490 on 2010-08-01
Yeah running 64bit OS on 64bit hardware is the best bet, the only issue i had recently with 64bit Ubuntu was flash but i managed to get it sorted out without too much hassle.

---

### Post by NobleSavage on 2010-08-01
Thanks for all the help. I guess I'll go with the 64bit version of Ubuntu.

---

### Post by Dustin2128 on 2010-08-01
> **NobleSavage said:**
> Thanks for all the help. I guess I'll go with the 64bit version of Ubuntu.
mark solved please.

---


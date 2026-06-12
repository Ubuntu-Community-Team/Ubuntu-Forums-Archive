---
title: "Problem with SATA vs eSATA port!"
date: 2010-06-12
forum: General Help
---

### Post by Krupski on 2010-06-12
Hi all,

I have a strange problem. I've got an Addonics AEIDDSAU multi-flash reader/writer that uses the SATA port [**[COLOR="Blue"]_LINK_[/COLOR]**](http://www.addonics.com/products/flash_memory_reader/AEIDDSAU.asp).

I'm running XUbuntu 10.04, 64 bit on an Intel DQ45CB motherboard. The board has 5 internal SATA-300 ports and one external eSATA-300 port.

Now the problem: The Addonics reader works fine on the eSATA port, but it doesn't work (properly) on an internal SATA port.

By "doesn't work properly" I mean that when connected to the eSATA port, plugging in a memory card causes an immediate detection and the contents of the card pop up in a window (as they should).

When connected to an INTERNAL SATA port, a plugged in card does not show, and using CFDISK to look at the "drive" shows an unformatted 64MiB disk that really doesn't exist.

Being an INTERNAL device, the Addonics reader is rather worthless if it doesn't work on an INTERNAL port, and there's no clean way to bring the eSATA port inside the computer.

By the way, I'm sure this is NOT a "Linux" problem because the reader behaves the same way in Windows XP.

Anyone have any ideas?

Thanks!

-- Roger

---

### Post by quadproc on 2010-06-12
> **Krupski said:**
> ...
Now the problem: The Addonics reader works fine on the eSATA port, but it doesn't work (properly) on an internal SATA port....

Anyone have any ideas?

The only thing that I can think of is that the specifications for levels are slightly different between eSATA and SATA; the eSATA spec provides a little more robust interface.  This suggests to me that your reader does not meet SATA specs.  If so, that would be due to either a design defect or to bad hardware or, (very unlikely) a bad cable.  Sorry, I can't think of anything else.

quadproc

---

### Post by Krupski on 2010-06-12
> **quadproc said:**
> The only thing that I can think of is that the specifications for levels are slightly different between eSATA and SATA; the eSATA spec provides a little more robust interface.  This suggests to me that your reader does not meet SATA specs.  If so, that would be due to either a design defect or to bad hardware or, (very unlikely) a bad cable.  Sorry, I can't think of anything else.

quadproc

Well, I thought of that and I tried a few different SATA cables. All did the same thing. I also tried the connection on a spare hard drive I had lying around and it worked fine, so I know the SATA cable, port, etc... are all OK.

I guess it's possible that I just have a bad unit from Addonics!

Anyway, I have a tech support request into them. I expect good results... I've purchased lots of things from them before and had zero problems.

If I learn anything new I'll post a follow-up.

Thanks for your reply!

-- Roger

---

### Post by dcstar on 2010-06-12
> **Krupski said:**
> 
..........
I'm running XUbuntu 10.04, 64 bit on an Intel DQ45CB motherboard. The board has 5 internal SATA-300 ports and one external eSATA-300 port.

Now the problem: The Addonics reader works fine on the eSATA port, but it doesn't work (properly) on an internal SATA port.
.........
Anyone have any ideas?


You do know that internal MB ports are** not** hot pluggable and require reboots before the hardware is detected correctly?

---

### Post by Ocxic on 2010-06-12
> **dcstar said:**
> You do know that internal MB ports are** not** hot pluggable and require reboots before the hardware is detected correctly?

^-- he's right. normal SATA ports don't allow you to un-plug/plug in stuff while eSATA ports do.

---

### Post by Krupski on 2010-06-13
> **dcstar said:**
> You do know that internal MB ports are** not** hot pluggable and require reboots before the hardware is detected correctly?

Yeah of course I know that. Problem is, even if I connect the Addonics reader to the machine, THEN reboot, the same problem occurs. It shows up as a 64 MiB unformatted disk that doesn't exist.

I suspect that my Addonics reader is bad... still waiting for a reply from the company.

---


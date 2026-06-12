---
title: "Ubuntu 10.10 hangs on syscall_call"
date: 2011-01-08
forum: General Help
---

### Post by leebies on 2011-01-08
Hi,

Just built a new PC with the following hardware and am trying to install Ubuntu 10.10. However it hangs on syscall_call both on Live CD and on Alternative CD. 

If I try Fedorda 14 CD it hangs on: "kernel_thread_helper".

If I try DamnSmallLinux I get: "kernel panic vfs unable to mount root fs"

Here is the hardware I used:

> 
ASUS M4A78LT-M LE AMD 760G Socket AM3 DVI VGA Out 8 CHannel Audio MATX Motherboard 
AMD Athlon II X3 445 3.1 GHz - Socket AM3 1.5 MB cache
Sapphire HD 5450 1GB DDR3 HDMI DVI VGA Out PCI-E Low Profile Graphics Card 
Arctic Power 500W PSU With PCI-E 2x SATA, 20+4 ATX12V 8pin +12V Connectors
Arctic Cooling Freezer 7 Pro rev 2 Socket 775, 1156, 1366, AM2, AM3 Heatpipe CPU Cooler 
4GB (2x2GB) DDR3 1333MHz Memory Kit 1.5V CL9 
Samsung HD103SJ Spinpoint F3 1TB Hard Drive SATAII 7200rpm 32MB Cache 
Samsung SH-B083L 8x BD-ROM with DVD±RW DL SATA Blu-Ray Drive


I have tried taking out the Graphics Card and running from the onboard graphics incase there was a conflict but that generated same issue.

I ran memtest86 and the RAM comes up fine with no errors.

I wonder if its anything to do with the HDD being SATA? But then does a LiveCD even care about the HDD?

Really don't know what to do nex, so would really appreciate some ideas.

Many thanks.

---

### Post by leebies on 2011-01-08
Same issue with Xubuntu 10.10 also.

Here is a list of some of the messages that appear during boot which may help in figuring out what is going on:

> 
Target filesystem doesn't have requested /sbin/init
Segmentation fault
No init found. Try passing init= bootarg.
Segemntation fault
/init: line 326: can't open /root/dev/console: no such file
[ 2.258603] Kernel panic - not syncing: Attempting to kill init!

... several other errors such as

exit_notify
do_exit

Then ending in:

syscall_call+0x7/0xb



Really scratching my head on this one.

My only theory is Sata or Ram settings perhaps but I don't have a clue what I can do to fix.

Thanks for any suggestions in advance!

---

### Post by leebies on 2011-01-08
Continuing my research; adding settings such as "nomodeset" hasn't made any difference either.

I can't actually run or install any Linux based OS that I have tried for these errors or similar occur long before the OS has a chance to get going.

I don't have a Windows (cough) CD hanging around to test if that works. Window's was cast out of this house some time ago!

Heeeelllp. :(

---

### Post by leebies on 2011-01-08
Also to confirm I have tried CDs and DVDs (burned slowly as well and done integrity checks etc).

Even tried booting from USB using unetbootin.

Hmmm

---

### Post by Slim Odds on 2011-01-08
Sometimes, Segmentation Fault can be hardware problems.

I've had system where one of the power supply voltages was low, causing memory problems.

If your power supply adequate for your hardware?

---

### Post by leebies on 2011-01-09
Using a 500w supply.

Processor takes approx 95w
HD Card around 20w (as far as my research suggests)
Fan is hungry at 130w
Ram no more than 10w max I think
HDD 8w when active

Not sure how to find out the power consumtion of the BDRom, or the motherboard as a whole.

The above works out just under 270w. I think that should leave enough room for a BD rom, and a motherboard and a couple of USB devices?

Or do you think I need to be upping my power? Is there a way to see how much power is being drawn?

Any other suggestions?

Many thanks

---

### Post by leebies on 2011-01-09
Hi,

Anyone any ideas? Just FYI I found a XP CD and popped it in. It allowed me through to the partition screen no problem. I haven't gone any further as I dont really fancy XP on my nice shiny new computer.

It would seem however XP can see all hardware with no issues.

Any help greatly appreciated.

Many thanks,

---

### Post by leebies on 2011-01-09
Think it could be ram maybe? Went for a install or xp which I will wipe to see how far it got and after initial copy and reboot I got


PAGE_FAULT_IN_NONPAGED_AREA
STOP: 0×00000050 (0xCD3DD628, 0×00000001, 0x804EFC9A, 0×00000000)

Will try 1 stick of ram then the other and see what happens.

---

### Post by Slim Odds on 2011-01-10
> **leebies said:**
> Think it could be ram maybe? Went for a install or xp which I will wipe to see how far it got and after initial copy and reboot I got


PAGE_FAULT_IN_NONPAGED_AREA
STOP: 0×00000050 (0xCD3DD628, 0×00000001, 0x804EFC9A, 0×00000000)

Will try 1 stick of ram then the other and see what happens.

Yes... as I mentioned.... Segmentation Faults are often hardware related.

P.S. Those Ubuntu Live CD's also have an entry to do a memory test... Try that.

---


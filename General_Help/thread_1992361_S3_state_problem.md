---
title: "S3 state problem"
date: 2012-05-31
forum: General Help
---

### Post by PrvSAT on 2012-05-31
Hello,

Problem: Installed Precise 12.04 and only when comes out of standby, everything is very slow, mouse, everything. It seems that like the RAM was not cleared or something else is running heavily in the background.

Details:
- Installed Ubuntu 10.10, then *updated*. All running well, but after standby it has the problem described above.
- Installed Ubuntu 12.04, *with no update*. All running well, after coming out of standby, the same problem.
- Installed Windows 7 home and after standby there is NO problem, so in Windows 7 everything is OK.

My sys info is:
- Mobo: Intel DG43GT with the latest f/w ([http://www.intel.com/p/en_US/support/hig...ds/dg43gt](http://www.intel.com/p/en_US/support/hig...ds/dg43gt))
- Chipset G43, Video GMA x4500 connected to HDMI
- Dual Core Intel @3GHz
- 2x2Gb Ram @ 800MHz
- 64GB SSD drive

The hard drive is set as AHCI, "smart" enabled", parallel, serial and on-board 1394 are disabled since I have no use. Video mem is set for 256Mb, tried with 128Mb and "max".
Ram config is set to "Auto", PCI Latency=32 (tried with 64 too), HPET=enabled (tried disabled too), Intel Virtualization=enabled (tried disabled too).
ACPI suspend=S3, "Processor Power Management" tried enabled and disabled, UEFI=tried enabled and disabled, all with the same result.
Please help me out.

---

### Post by PrvSAT on 2012-06-01
I have tried installing compiz, tweaking, etc, with no success.
I have read lots of similar posts about this issue, mainly related to Intel system, including some raised bugs with no fix.

Some very similar bugs were raised as early as 2010 and in some cases the reply was that there are tons of bugs issued every day and the developers do not have time to go over each one. So ma I out of luck, nobody could help me in any way?

---

### Post by PrvSAT on 2012-06-04
Using a 64 bit version, it seems that the problem is solved. I read this thing from others having the same issue. Apparently it shows only on systems based on Intel architecture. No disrespect, but the ubuntu dev guys are not at the first screwed up. 

I installed Linux Mint v13 (12.04) based) 64 bit and it solved the problem!
Linux Mint seems to be better supported not like ubuntu where you ask for help in four different forums and only in one it happens to get some help... not to mention that Mint is far better with a professional look and better functionality. Reality: It puts Precise years back. Of course I could modify Precise to look better, but why? Why Ubuntu release guys could not get a better visionary in terms of design?

---


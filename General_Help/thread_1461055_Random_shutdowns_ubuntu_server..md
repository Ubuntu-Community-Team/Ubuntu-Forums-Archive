---
title: "Random shutdowns ubuntu server."
date: 2010-04-23
forum: General Help
---

### Post by niiklas on 2010-04-23
Tonight i have been having random shutdowns on my ubuntu server. With 15-20 minutes in between.

Which logs should i check for info?, i got this from the kern.log

This is my kern.log
[http://data.fuskbugg.se/skalman01/kern.log](http://data.fuskbugg.se/skalman01/kern.log)

Thanks in advance.

/Niklas

---

### Post by Serpher on 2010-04-23
If anything this sounds like a hardware issue. Perhaps keep an eye on the temperature of of your CPU.

---

### Post by Iowan on 2010-04-23
Is the server headless? There are a couple of threads about problems with headless servers that work fine with keyboard and/or monitor attached.

---

### Post by gzarkadas on 2010-04-23
syslog, dmesg, messages, auth.

Your kern.log shows the following possibly interesting things:

> 
<multiple times>
TCP: Treason uncloaked! Peer ... shrinks window ... Repaired.
This is pressumably caused by a bug in the tcp stack and may be a sign of remote attack / may be not. See this link for further details to decide yourself:
[URL="http://www.informedbanking.com/wiki/TCP_Treason_Uncloaked"]http://www.informedbanking.com/wiki/TCP_Treason_Uncloaked
[/URL]
> 
Driver 'sd' needs updating - please use bus_type methods
...[FONT=monospace]
[/FONT]/build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Kernel command line: root=UUID=dcb76cf8-e6a6-40d7-972a-2a1b46a37605 ro quiet splash
...
Checking aperture...
CPU 0: aperture @ 6a00000000 size 32 MB
Aperture too small (32 MB)
No AGP bridge found
Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the BIOS setup
This costs you 64 MB of RAM
Mapping aperture over 65536 KB of RAM @ 4000000
...
SELinux:  Disabled at boot.
AppArmor: AppArmor initialized
Failure registering capabilities with primary security module.
...
ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  D4, should be C7 [20070126][FONT=Verdana]
[/FONT]In short:
-- you may need a driver update for your disks (is it a disk array?)
-- perhaps due to the previous abrupt shutdown, you start with the root filesystem readonly; check if this has been fixed.
-- your bios is probably mis-configured regarding AGP settings
-- SELinux and AppArmor disabled / disfunctioning (perhaps you decided to be so)
-- Possible ACPI corruption due to frequent shutdowns (a clean shutdown and restart after a few seconds may fix this; perhaps it does not need fixing either)

I suggest to check that all of your hardware is ok (malfunctioning hardware is a frequent cause of such troubles), review your BIOS settings, perform a check on all your filesystems and make a backup (if not already) of all your valuable data. 

Then, if reading the info at the link leads to a suspicion of break-in you can search for evidence in the logs and the filesystem (and also review your firewall settings); if it comes out to be a tcp stack bug, you can examine the option to upgrade to a newer kernel version (if it exists).

---

### Post by niiklas on 2010-04-24
Found out that i had a cooling problem, after few minutes of running my cpu started to get higher and higher temperatures. Will fix the cooling, thanks for all help.

---


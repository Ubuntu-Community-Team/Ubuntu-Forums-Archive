---
title: "Caveats for Acer slimlines with nVIDIA GeForce 8200 IGP"
date: 2011-05-05
forum: General Help
---

### Post by bcschmerker on 2011-05-05
I am currently in the process of rebuilding an eMachines®/Acer® EL1210-09 that had been running Microsoft® Windows® 6.0.6002 at the time the stock Hitachi® HDP725016GLA380 3.5" hard disc drive threw in the towel for one or more thermally related circuit failures.  (Current plans call for having Data Recovery Sacramento assess the rebuildability of the HDP7250 after salvaging two specific subdirectories of the C: volume to USB memory chip(s), as apparently [Hitachi Global Storage Technologies](http://www.hitachigst.com/) inherited some quality-control issues from International Business Machines Corporation over the DeskStar platform's magnetoresistive read/write heads and glass platters.)  I recently upgraded the power supply from a LiteOn® PS-5221-06 (+3.3/+5V limit 80W, total 220W cont.) to a Shuttle® PC6300002 (+3.3/+5VDC limit 150W, total 500W), requiring minor case modification; the CPU cooler from a no-name skived aluminum monoblock to a [Scythe® SCSK-1100](http://www.scythe-usa.com/), notched to clear the SATA power plug for the optical drive; and the main memory from the stock 2x1GB to a [Kingston® KVR800D2N6K2/4G PC2-6400 main memory kit](http://www.kingston.com/) (2x2GB).  I may eventually upgrade the CPU from the as-delivered Advance Micro Devices® Athlon 64® LE-1620 to an Athlon® X2 5050e, as both are Socket AM2 units of 45*max*W power dissipation.  As of May 2011 the exclusion case against the [nVIDIA® MCP78S and GeForce® 8200](http://www.nvidia.com/) is on appeal due to the existence of uncommanded shutdowns involving not only nVIDIA® but also Intel® and Advance Micro Devices® chipsets on Elitegroup® motherboards.

Ubuntu® 11.04 Natty being available in Live CD/DVD form, I plan to use either an x86 or AMD64 Edition of one of the available subdistributions from the stock optical drive to test the planar hardware, while a shock mount for either a [Seagate® Momenuts](http://www.seagate.com/) or [Western Digital® Scorpio Black®](http://www.wdc.com/) 2.5"-format hard drive is in fabrication---I see the replacement drive as being in need of cooling air that the stock Hitachi® controller board never got due to a design flaw in the HDD installation which my shock-mount project is intended to also correct.  Another purpose of the Natty tests is to rule out DSDT issues with the Phoenix® Award® BIOS that shipped with the EL1210-09 (see [The DSDT Thread](http://ubuntuforums.org/showthread.php?t=1147474) for details).

What boot parameters, if any, are needed for Kernel 2.6.3x on an nVIDIA®-centric system board using an AMD® Socket AM2 CPU?  And what subdistribution of Ubuntu®, in x86 or AMD64, would be best suited to a system running 4 GB memory, 750*max* GB total hard disc capacity, and a CPU core speed of 2.6*max* GHz?

**Update:**  Due to issues that I encountered finding the appropriate Binaries for handling settings in Natty, I backgraded to 10.04.2-LTS Lucid, AMD64 Edition, and encountered no problems other than are typical with video settings.  The hard drive, a Western Digital® WD5000BEKT, and shock mount are in and up.  *07 Jun 2011 BCS*

---


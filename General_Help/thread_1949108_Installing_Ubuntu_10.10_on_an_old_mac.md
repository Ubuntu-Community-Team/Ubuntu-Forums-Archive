---
title: "Installing Ubuntu 10.10 on an old mac"
date: 2012-03-29
forum: General Help
---

### Post by AaronDaycentChild on 2012-03-29
I'm wondering is it possible to install Ubuntu 11.10 on Mac OSX 10.3.9 (Panther). The system is very old and unusable and I want to put Ubuntu on it to save it. 

I'm having a little bit of trouble. I know I have to create a partition for ubuntu with Disk Utility on the Mac but it wont let me do that. I need rEFIt and the version 0.14 wont work on it. 

Any help?

---

### Post by snowpine on 2012-03-29
It would be helpful if you told us about your Mac hardware, right? :)

Anyway, 10.10 is "end of life" and completely unsupported. 11.10 is the current release, and 12.04 is coming in a few weeks. If you install the 12.04 beta now, it will roll over to the stable release and be supported through April 2017.

---

### Post by AaronDaycentChild on 2012-03-29
> **snowpine said:**
> It would be helpful if you told us about your Mac hardware, right? :)

Anyway, 10.10 is "end of life" and completely unsupported. 11.10 is the current release, and 12.04 is coming in a few weeks. If you install the 12.04 beta now, it will roll over to the stable release and be supported through April 2017.

Awh damn! I mean 11.10. Sorry about that. 

Here's some of the hardware info on my Mac:
 - Processor: 1.6 GHz PowerPC G5
 - Machine Model: Power Mac G5
 - CPU Type: PowerPC 970 (2.2)
 - Number of CPUs: 1
 - CPU Speed: 1.6 GHz
 - L2 Cache (per CPU): 512 KB
 - Memory: 1.5 GB
 - Bus Speed: 800 MHz
 - Boot ROM Version: 5.1.5f2
 - Serial Number: CK412H1SNV9
 - File System Capacity: 74.53 GB

---

### Post by wayover13 on 2012-03-29
I just did this recently. Actually, I started out trying Ubuntu (Lubuntu for PowerPC) but decided during the process to switch over to straight Debian. So I can tell you that it works in principle. Are you trying to dual-boot, or will Linux be the only OS on this machine?

James

---

### Post by AaronDaycentChild on 2012-03-29
> **wayover13 said:**
> I just did this recently. Actually, I started out trying Ubuntu (Lubuntu for PowerPC) but decided during the process to switch over to straight Debian. So I can tell you that it works in principle. Are you trying to dual-boot, or will Linux be the only OS on this machine?

James

I want Linux to be the only OS on the machine. I have to make a partition first from what I've found on the internet. 

How did you do it?

---

### Post by wayover13 on 2012-03-29
As I recall I tried first to use the Lubuntu PowerPC live CD. It was having some trouble with partitioning, I believe, which is, I think, why I decided to go with Debian. Anyway, both Lubuntu for PowerPC and Debian run a partitioning utility when you boot from the respective CD's--Lubuntu's being a fuzzy-feely graphical thing and Debian's being more a command-line type thing. You use that to partition the drive as you want. The only really tricky part there is that you MUST create what's called a "new world boot partition" of about 800 kb. The partitioner should give an automated way to do that. Then make a swap partition of the desired size (3GB in your case, it seems) and devote the rest of the drive to the Ubuntu/Lubuntu/Debian operating system.

I built my Debian system up from scratch, which certainly won't be for everyone. If you want something more automated try Lubuntu for PowerPC (which is likely to remain in an alpha state, btw.) Another option would be to look into MintPPC: they seem to have done a lot of work with New World Macs.

James

PS Looks like the Lubuntu for PowerPC live CD can be downloaded from this page: [http://cdimage.ubuntu.com/lubuntu/daily/current/](http://cdimage.ubuntu.com/lubuntu/daily/current/) --and by the way, that is the 12.04 release candidate.

---


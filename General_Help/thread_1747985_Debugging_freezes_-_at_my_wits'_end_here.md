---
title: "Debugging freezes - at my wits' end here"
date: 2011-05-03
forum: General Help
---

### Post by olesk on 2011-05-03
I'm at my wits' end trying to understand why my Ubuntu Natty installation (upgraded from Maverick) suffers freezes in certain situations. As I also experienced this during Maverick, I don't think this is a Natty specific issue. I'm usually able to pinpoint the source of most issues (I used to work as a systems admin on AIX/Solaris/Linux some years back), but here I'm at a complete loss. 
 
I'm hoping a dicussion here might be of general help to other who are trying to debug freezes on their systems. I'll try to explain my situation and what I did to resolve it, and then hopefully someone can chip in and tell me what I am missing :)
 
**what:** my system experiences occasional freezes - if HDDs are active during freeze, their activity leds remain frozen (they are all in SATA backplanes). Only hard reset will resolve situation
 
**when:** browsing NFS shares on a Mac Mini with Nautilus, mounting parseimages over AFP (full Netatalk installation on Ubuntu box) from Mac Mini (I use the Ubuntu box as TimeMachine backup repository of AFP), after random times when inactive in X but not when using text console (using standard GUI, not Unity), during large file transfers over NFS (this might be a sperate issue, as others have reported issues here, but freezes also occur independetly of NFS, i.e. with no NFS mounts mounted)
 
 

**remedial action attempted:**[LIST=1]
[*]_checked logs_ (syslog,afpd,nfs,kern,dmesg etc.) - nothing (literally nothing to indicate issues - looks clean until freeze), no indication of serious problems
[*]_checked hardware_ - changed network card, verified temperatures and fan speeds to all be in conservative ranges, switched power supply, installed power meter to verify load, added ups to block surges
[*]_changed thumbnailing_ mechanism in Nautilus to use ffmpeg in case thumbnailing were having issues (have been some of nfs shares in the past)
[*]_searched known bugs_ to see if freezes could be related to GPU, but my GeForce 8800 GT seems to have fine support with proprietary drivers installed and despite some resolution issues in earlier versions of Ubuntu, noone else seems to have system freezes with this card - again I use standard Gnome with Kompiz, not Unity
[*]_disabled all unnecessary hardware_ like serial ports, built-in SATA controllers, sound card etc.
[*]_tried samba4_ before downgrading to samba3 (well, I'm trying anything here) ;)
[*]_uninstalled Netatalk_ daemons, leaving me with Samba3 and NFSv4
[*]_disabled any and all power management_ functions
[*]_checked RAM _- all fine there
[*]_checked processes_ - using top/atop/nethogs/istats/iotop I tried finding if anything is hogging all resources, but nope, RAM at 90% usage, no swap usage (got plenty), CPU at low load, disks mostly low load, temps low
[/LIST]**system:** 
2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
 
*00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller (rev 01)*
*00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge (rev 01)*
*00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)*
*00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)*
*00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)*
*00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)*
*00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)*
*00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)*
*00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)*
*00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)*
*00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)*
*00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)*
*00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)*
*00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)*
*00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)*
*00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)*
*01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GT] (rev a2)*
*02:00.0 PCI bridge: Texas Instruments XIO3130 PCI Express Switch (Upstream) (rev 02)*
*03:00.0 PCI bridge: Texas Instruments XIO3130 PCI Express Switch (Downstream) (rev 02)*
*03:01.0 PCI bridge: Texas Instruments XIO3130 PCI Express Switch (Downstream) (rev 02)*
*03:02.0 PCI bridge: Texas Instruments XIO3130 PCI Express Switch (Downstream) (rev 02)*
*04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)*
*05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)*
*07:02.0 Mass storage controller: Promise Technology, Inc. PDC40718 (SATA 300 TX4) (rev 02)*
*07:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)*
 
I'm on a LAN with two Windows 7 boxes, one Mac Mini and one iMac in addition to my Ubuntu server, which is primarily a file server. The Ubuntu box does a bit of Deluge torrent traffic and is intended to run HTTP, AFP, SMB and NFS services as well as act as a Linux desktop for small scale Perl programming.
 
It has two RAID arrays (Linux sw RAID, one level 10 with 4 disks (not 1+0) and one level 1 with 2 disks) whith LVM2 on top. An unfortunate side effect of the freezes has been frequent long rebuilds lately. My root is at a Mushkin SSD disk. CPU an Intel Core2Duo, Asus 5PE mobo, Corsair 2x2GB RAM, no overclocking. 
 
So my question then becomes: where do I go from here? 
 
I realize it's tempting to ask if there *really* is nothing in the logs, but unfortunately that seems to be the case, but I'm happy to post them if anyone wants to take a second look. I am suspecting that something with the network services causes this, as both AFP and NFS issues point in that direction - but what would be the common denominator and why are the logs empty? The other alternative is hardware, but all seems ok, and logs are clean. Network cards could cause it, but I've tried changing them (different chipset & driver) without any improvement, RAM is fine, temperatures ok, SMART reports nothing.

---

### Post by blueturtl on 2011-05-03
Could be a kernel problem. Ubuntu introduces some of their own patches (and thus, their own bugs) that are absent in the mainline kernel. You could try running the system with the mainline kernel and see if the lock-ups disappear. If they do, then it's an Ubuntu problem. If they don't, it could be a general kernel problem.

---

### Post by dragonfly41 on 2011-05-03
Here are some initial thoughts chipped in .. 

Your system configuration is quite complex and as you say ...
> As I also experienced this during Maverick, I don't think this is a Natty specific issue.


[LIST]
[*]Have you tried running without the battery and only mains power to see if the freezes continue?
[*]If you have a USB port expander is it separately powered?
[*]Can you remove USB devices and see if there is any impact?
[*]Can you keep Htop app running on desktop up to the point of any freeze (any common process running)?
[*]Can you run in safe graphics mode?
[*]Do you have a swap partition?
[/LIST]

---

### Post by olesk on 2011-05-03
> **blueturtl said:**
> Could be a kernel problem. Ubuntu introduces some of their own patches (and thus, their own bugs) that are absent in the mainline kernel. You could try running the system with the mainline kernel and see if the lock-ups disappear. If they do, then it's an Ubuntu problem. If they don't, it could be a general kernel problem.
 
Not a bad recommendation. I've been though a bunch of Ubuntu kernels over the last few months, but no mainline kernels. I'll give it a shot and report back if I notice any changes.

---

### Post by olesk on 2011-05-03
> **dragonfly41 said:**
> Here are some initial thoughts chipped in .. 
 
Your system configuration is quite complex and as you say ...
 
 

[LIST]
[*]Have you tried running without the battery and only mains power to see if the freezes continue?
[*]If you have a USB port expander is it separately powered?
[*]Can you remove USB devices and see if there is any impact?
[*]Can you keep Htop app running on desktop up to the point of any freeze (any common process running)?
[*]Can you run in safe graphics mode?
[*]Do you have a swap partition?
[/LIST]
 
The system is a standard desktop (not laptop), but in case you're referring to the UPS I only got that one after the issues started (wish I could recall exactly when they started - would've give me something to work on)), and three other boxes share the same UPS, all of them stable.
 
Removing UBS devices I have tried without any noticeable differences. The mouse/keyboard is on an active KVM switch, but I think that's too plain vanilla to cause a system freeze (and difficult to relate to freezes that seem linked to network activity unless I have the world's most bizarre conflict between my PCI-e NIC and the KVM - that would be a rather interesting bug report :) ).
 
I've been running atop until freeze several times, and the common daemons are all runninng a low load. The processs is long and I've not identified anything "unusual" with regards to loads or presence of strange processes. Trying to kill them off one by one and see what improves stability would help, but would be an extremely long and cumbersome process and prone to unwanted side effects. This was one potential solution I had high hopes for (and one I would always recommend to others suffering freezes).
 
I can run in safe mode (X) and in safe mode (option from grub2) and I think this perhaps is the way forward. See comment below.
 
I have a lot of swap (10GB) sitting on the RAID in one ov the LVs. It's activated and seems to work well, but with 4GB of RAM it's rarely used. During hangs I've typically used pretty much no swap.
 
 

It's quite helpful trying to describe your troubles to others as it helps one think strucuted about one's problem :) Based on the previous suggestion and some more mental gymnastics I think the right way forward could be:[LIST=1]
[*]Try a mainline kernel as suggested earlier. I've tried several kernels, but all Ubuntu kernels. Could be something weird with the Ubunt kernels
[*]Establish whether X/Gnome/Compiz has anything to do with this.
[LIST]
[*]Shut down GDM and stick to console. Activate all daemons (Netatalk/AFP, SMD, NFS) and repeat actions that have previously caused hangs as well as stress test over time
[/LIST]
[*]If problems disappear -> X/Gnome/Compiz might be the sinner. Try repeating the same in GUI safe mode and then start adding stuff until it breaks
[*]If problems persists: X/Gnome/Compiz is not the *only* culprit, but could be the trigger of a deeper problem. Back to square one...
[/LIST]The SATA controllers/Mobo could be the problem, but replacing them is expensive and I'd expect the kernel log to be full of complaints. I'll try the approach outlined above and see if I can narrow it down. I suspect Nautilus of triggering a problem which is not really Nautilus' fault, but reducing the number of possible causes is certainly worthwile. 
I'll also see if I can whip up a little Perl script to parse syslog and find the latest instance of the hangs (i.e. when boot messages are not preceeded with shutdown messages in syslog, indicating a sudden reboot without proper shutdown). Matching that date to updates of hardware or software (kernel in particular) might yield something.
 
Meanwhile, all comments and suggestions are welcome. I still feel I'm some way off from nailig down this issues...

---

### Post by olesk on 2011-05-03
Ok, so I tried in console mode with all network daemons running to first mount an AFP share from my iMac, and from there mount a sparseimage. The Ubuntu box promptly froze hard.

This time however I noticed the following two entries popping up in my console:
[B]NOHZ local_softirq_pending 08
NOHZ local_softirq_pending 08[/B]

This didn't make me much smarter, even after googling it a bit. But I think we can safely say that X/Gnome/Compiz is not the culprit, as X wasn't running. 

I then rebooted with a mainline kernel (2.6.39-020639rc5-generic) and lo' & behold, in the syslog there now suddenly is an entry as follows:
kernel: [  300.040021] [Hardware Error]: Machine check events logged

Now *that* looks pretty bad. Searching around a bit, I found the the *mcelog* package might provide more information, and indeed, running mcelog, gave me the following (I applied some bold):
[I]
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
**Processor context corrupt**
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
failure that caused IERR
STATUS f200084000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0
CPUID Vendor Intel Family 6 Model 15
[B]HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor[/B]
MCE 1
CPU 0 BANK 5
TIME 1304441237 Tue May  3 18:47:17 2011
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE driven
STATUS f200001014000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0
CPUID Vendor Intel Family 6 Model 15[B]
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor[/B]
MCE 2
CPU 1 BANK 5
TIME 1304441237 Tue May  3 18:47:17 2011
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven MCE is observed
STATUS f200001030000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0
CPUID Vendor Intel Family 6 Model 15[/I]

So what on earth does this mean? My CPU is not overclocked. The only thing I can think of ***beyond a fried CPU ***is that I installed *intel-microcode* and *microcode.ctl *recently. I purged both packages, rebooted and tried again. Again with the mainline kernel, without GDM, and again it hangs when I mount the parseimage from my iMac. Dead & gone. Hard reset only option. No log entries of any kind before freeze. 

I guess I just a to face that (from Wikipedia): ***A Machine Check Exception (MCE) is a type of computer hardware error that occurs when a computer's central processing unit detects a hardware problem***. This again should mean that either a) my CPU is bust or b) my RAM is (or c) I had a bizarre random error in RAM, which can happen, which is completely unrelated). Unless someone is better at interpreting these messages than me and come to a different conclusion (if you do, please do let me know!), I'll try first replacing the RAM and then replacing the CPU and check if either helps.

Stay tuned! ;)



[B]Edit: It's not the ram. Put in new DIMMs and same hang result. Will try CPU....
Edit 2: And it's not the CPU - switched to an older CPU but same result
[/B]

---

### Post by no2498 on 2011-05-03
have you installed htop and look at it as all this starts

---

### Post by olesk on 2011-05-03
> **no2498 said:**
> have you installed htop and look at it as all this starts

Yes I did - htop is ideal for this kind of testing - thanks for the tip! Just before the crash the afpd works a bit, but just when browsing the volume. As soon as the initial mount is over it disappears and the crash comes a few seconds later with no real load on any processes.

However, as I was changing the CPU and RAM, I did experience another oddity, which is that my extra SATA adapter failed to recognize its disks a couple of times. I think therefore that what I'm left with now is that either a) the SATA adapter has gone bad or b) the motherboard is toast.

I'll try freeing up the two disks on the external SATA adapter and remove it, to see if that solves my issues. Failing that, I do have an old motherboard that I can use as a last resort, but that's a little more than I can manage to get done tonight, as the moving of the volumes of the SATA adapter will take some time and completely dismantling the cabinet even longer...

---

### Post by Nasair on 2011-05-03
I had some similar issues with freezing (my Kernel was being caused to crash), no idea why they started or what was the root cause. See my link to my thread below. I've had no further issues since a slew of updates last night.
[http://ubuntuforums.org/showthread.php?t=1747154](http://ubuntuforums.org/showthread.php?t=1747154)

Try updating again and see if that helps, it did for me at least.

---

### Post by dragonfly41 on 2011-05-03
This is a very wild guess .. but you've mentioned SATA several times .. and if you go into BIOS do you have an option in SATA device configuration to change to ATA instead of AHCI ..

I had to do this for an earlier Windows installation which froze on me.

But this is just a hunch and could be a red herring.

---

### Post by msekeris on 2011-05-03
I think i actually just ran into the same problem, just upgraded my server to 11.04, Seen about the same errors as you, nothing in logs etc, however i did see the r8169 in a kernel panic, so i started fiddling with nics, figured when i stress the incoming network traffic i get an instant kernel panic.

i also found this tread, [https://bbs.archlinux.org/viewtopic.php?pid=908371](https://bbs.archlinux.org/viewtopic.php?pid=908371) , seems to be very similair.

since you are also using realtek nic's i think that might be the source of it.

Gonna try some different kernels now, ill keep you updated.

update: my previous kernel "2.6.35-28-server" does not panic, well at least not instant. :P

update 2: there seems to be a bug in the realtek driver for some nics in all kernels after 2.6.37-3 i'm now running the current "2.6.38-8-server", installed the propriety realtek drivers and everything seems to be working fine.

---

### Post by olesk on 2011-05-04
> **Nasair said:**
> I had some similar issues with freezing (my Kernel was being caused to crash), no idea why they started or what was the root cause. See my link to my thread below. I've had no further issues since a slew of updates last night.
[http://ubuntuforums.org/showthread.php?t=1747154](http://ubuntuforums.org/showthread.php?t=1747154)
 
Try updating again and see if that helps, it did for me at least.
 
 
I've been doing apt-get update && apt-get upgrade like mad over the last few days actually :) . I was half expecting someone to tell me how silly it is to jump on Natty before the relelase have had a shot at settling down a litle. I've had to do a lot of fixing after each major upgrade in the past, and I was expecting this to be more of the same, but as I also had hangs before the upgrade it is probably not Natty's fault. If I can fix this I'm staying with Natty for *quite* a while ;)

---

### Post by olesk on 2011-05-04
> **msekeris said:**
> I think i actually just ran into the same problem, just upgraded my server to 11.04, Seen about the same errors as you, nothing in logs etc, however i did see the r8169 in a kernel panic, so i started fiddling with nics, figured when i stress the incoming network traffic i get an instant kernel panic.
 
i also found this tread, [https://bbs.archlinux.org/viewtopic.php?pid=908371](https://bbs.archlinux.org/viewtopic.php?pid=908371) , seems to be very similair.
 
since you are also using realtek nic's i think that might be the source of it.
 
Gonna try some different kernels now, ill keep you updated.
 
update: my previous kernel "2.6.35-28-server" does not panic, well at least not instant. :P
 
update 2: there seems to be a bug in the realtek driver for some nics in all kernels after 2.6.37-3 i'm now running the current "2.6.38-8-server", installed the propriety realtek drivers and everything seems to be working fine.
 
If this turns out to be a simple NIC error after having completely dismantled my entire PC I'll commit harakiri with a blunt pencil! One of the reasons I've left the NIC alone (and I guess I should've mentioned this previously) is that I bought [this NIC ]("http://www.exsys.ch/index.php?main_page=product_info&products_id=634&language=en&zenid=b8b5262db78f5f551de0d2737b77bd6f")specifically to avoid probelms I had with the intergrated network. I was under the impression that the Realtec 8111C chipset was nicely & widely supported in Linux. I now see that there are [know issues and solutions]("http://www.jamesonwilliams.com/hardy-r8168") with this card. It seems however that the symptoms that people are describing (including in [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/205374")) are not hangs/freezes and they seem to have disappeared in recent releases, but it's defenitely worth a shot. Will revert to built-in networking (and test a few more kernels) and try again, as well as try the proprietary drivers. Defenitely a good lead! Thanks a lot!
 
PS: I didn't find the bug that mentions issues at kernels later than 2.6.37-3 . do you have the link?

---

### Post by Nasair on 2011-05-04
> **olesk said:**
> I've been doing apt-get update && apt-get upgrade like mad over the last few days actually :) . I was half expecting someone to tell me how silly it is to jump on Natty before the relelase have had a shot at settling down a litle. I've had to do a lot of fixing after each major upgrade in the past, and I was expecting this to be more of the same, but as I also had hangs before the upgrade it is probably not Natty's fault. If I can fix this I'm staying with Natty for *quite* a while ;)

I actually think it might be my Harddrive now, but I didn't have these issues before updating so I wounder if 11.04's newer kernel is just a little more touchy with hardware? IDK, but hopefully I'll get mine narrowed down as well.

---

### Post by msekeris on 2011-05-04
> **olesk said:**
> If this turns out to be a simple NIC error after having completely dismantled my entire PC I'll commit harakiri with a blunt pencil! One of the reasons I've left the NIC alone (and I guess I should've mentioned this previously) is that I bought [this NIC ]("http://www.exsys.ch/index.php?main_page=product_info&products_id=634&language=en&zenid=b8b5262db78f5f551de0d2737b77bd6f")specifically to avoid probelms I had with the intergrated network. I was under the impression that the Realtec 8111C chipset was nicely & widely supported in Linux. I now see that there are [know issues and solutions]("http://www.jamesonwilliams.com/hardy-r8168") with this card. It seems however that the symptoms that people are describing (including in [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/205374")) are not hangs/freezes and they seem to have disappeared in recent releases, but it's defenitely worth a shot. Will revert to built-in networking (and test a few more kernels) and try again, as well as try the proprietary drivers. Defenitely a good lead! Thanks a lot!
 
PS: I didn't find the bug that mentions issues at kernels later than 2.6.37-3 . do you have the link?
I got that info from various sources, one of them the archlinux thread, there have been 4 commits related to the r8169 driver in 2.6.37-4 ([http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.37.4](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.37.4)) and one of them seems to be causing the problem.

i haven't found a specific ubuntu bug report however i did at the kernel bugzilla, so i assume they are working on it.

[https://bugzilla.kernel.org/show_bug.cgi?id=29282](https://bugzilla.kernel.org/show_bug.cgi?id=29282)
[https://bugzilla.kernel.org/show_bug.cgi?id=32962](https://bugzilla.kernel.org/show_bug.cgi?id=32962)

also found a bug report at archlinux and some other distro's but i can't find the links anymore.
[https://bugs.archlinux.org/task/23429](https://bugs.archlinux.org/task/23429)

for now i am running the 2.6.37-3 mainstream kernel and i think i will be until this is fixed in a newer release. im not a big fan of the realtek proprietary drivers.

---

### Post by olesk on 2011-05-05
> **Nasair said:**
> I actually think it might be my Harddrive now, but I didn't have these issues before updating so I wounder if 11.04's newer kernel is just a little more touchy with hardware? IDK, but hopefully I'll get mine narrowed down as well.
 
I've actually contemplated the HDs as well. As I have 7 drives on two SATA adapters, six in two different raids (one RAID10 and one RAID1 bundled into one LVM2 VG) plus a Muskin SSD driver for my root, there are a lot of potential error sources.
 
I did finally manage to try with a new mobtherboard, RAM and CPU late yesterday night, and _this time it only killed my network connection, not my system_. To be clear: I'm doing the same test each time - mount an AFP share from an iMac, and from the share, mount a parseimage. Result: crash every time, but now seemingly only network, not system, after the HW replacement.
 
For those of you not too familiar with OSX, a parseimage is like an ISO image, except it's really just a folder of files presented as a file by OSX. I believe this kills the system as the stress it causes to the network/disks at mount is significant, as it needs to quickly scan a whole lot of files over the network in one go. My hypothesis is that this causes enough stress to expose an **underlying** problem, which is the real problem I need to solve. I do not think the AFPd/Netatalk is to blame, as similiar things have happened over NFS in the past.
 

I now have two theories (which fits nicely with the two latest posts - thanks guys! :) ):[LIST=1]
[*]My NIC, which is a R8111C, uses the R8168 module, which is still not fully working for R8111C chipsets and needs to be replaced with the Realtec drivers. I will try this one as soon as I get home from work today.
[*]Something is wrong with the drives. This is a bit more tricky. It could be the drives themselves, it could be my SATA backplanes, it could be the SATA controllers or cables. Or it could be software, i.e. the fs, the RAID, LVM2... As there is absolutely nothing in the logs to indicate this though, and SMART reports all clear, and most importantly: it seems to be working well when I'm not doing anything network related, I'm leaning towards point 1 for now.
[/LIST]

---

### Post by olesk on 2011-05-05
> **msekeris said:**
> I got that info from various sources, one of them the archlinux thread, there have been 4 commits related to the r8169 driver in 2.6.37-4 ([http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.37.4](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.37.4)) and one of them seems to be causing the problem.
 
i haven't found a specific ubuntu bug report however i did at the kernel bugzilla, so i assume they are working on it.
 
[https://bugzilla.kernel.org/show_bug.cgi?id=29282](https://bugzilla.kernel.org/show_bug.cgi?id=29282)
[https://bugzilla.kernel.org/show_bug.cgi?id=32962](https://bugzilla.kernel.org/show_bug.cgi?id=32962)
 
also found a bug report at archlinux and some other distro's but i can't find the links anymore.
[https://bugs.archlinux.org/task/23429](https://bugs.archlinux.org/task/23429)
 
for now i am running the 2.6.37-3 mainstream kernel and i think i will be until this is fixed in a newer release. im not a big fan of the realtek proprietary drivers.
 
 
Thanks for the links - that's very helpful! Though I am not a big fan of the realtek proprietary drivers either, my experience with trying different kernels has been that it didn't help my case and thus I'm left with trying the proprietary drivers (and if that doesn't work, start looking at drives/controllers). At this point though, I'm only trying to pinpoint my problem. IF the proprietary drivers solve my problem, I will at least know what has been causing all this, which is reason enough to bring out the booze in my book ;)
 
Update: This bug: [https://bugzilla.kernel.org/show_bug.cgi?id=32962](https://bugzilla.kernel.org/show_bug.cgi?id=32962), that you mentioned, seems to describe my situation perfectly. System hangs/freezes during heavy network load with Realtec 8111. There might be light at the end of the tunnel after all...

---

### Post by olesk on 2011-05-05
**It was the network card**.

After having installed the proprietary drivers from Realtek I had one heart stopping moment when the computer seemed to freeze followed by a huge relief realizing it was simply doing a massive read from the RAID and then happily plodding on.

The module for Realtek r8168/r8111, called r8169 is currently broken for r8168 and my r8111 cards. If you want to use these cards, you should really read [this entry]("http://www.jamesonwilliams.com/hardy-r8168") (the script is old and have some issues, but look at the source and you'll figure it out) and download the proprietary drivers direct from Realtek - they just released an updated version.

Symptoms include loss of connectivity, hang/freeze during both boot, random times and especially during high network load. Fixes are worked on upstream, but seem quite some way off from making it into the Ubuntu kernels just yet. 

My main takeaways from this process:

[LIST=1]
[*]Freezes with no log entries anywhere usually indicates serious hardware **or driver** problems (two sides of the same coin I guess)
[*]Inconsistent errors bite, and finding a way to reproduce them is the first step to solving them - no matter how weird or seemingly uncorrelated what you do is
[*]Completely dismantling your entire system should **not** be first option (I did this too early, and got some additional confusion due to a faulty RAM module in one alternative build) :D
[*]Searching for bug reports on your suspect pieces of HW can save a lot of time! (Especially true for network cards, GPUs and SATA-controllers)
[*]The Ubuntu community is amazing! Thank you so much for the help, and especially to **msekeris **who correctly identified the NIC as the source of all my woes! :)
[/LIST]

---


---
title: "Need Your Help Before Giving up on Linux"
date: 2009-11-25
forum: General Help
---

### Post by topcause on 2009-11-25
Hello Everyone, As as Windows power user for many years I'm new to the world  of Linux and decided to give Linux a try and see if this OS can be used as a day  to day desktop platform. To make the story short I have setup 4 partitions and  been trying out various distros (Fedora, OpenSuse, Debian, Ubuntu, Kubuntu, Mint  etc...) Most of the distors didnt last me but a day or so before getting removed  due to different difficulties which required much troubleshooting. After all in  the world of Desktop for end users we want things just to work without needing  to spend 60 hours just to figure out why something simple doesn't work. Anyhow  I'm pleased to say that I'm left with Ubuntu & Mint and for the past 5 days been  trying them out.  I have been able to resolve a few minor glitches but now  I'm stuck and need your help with 3 issues below:
 I don't want to give up Linux without a fight like most people do so any advise is appreciated.
  **1. I can not get my Canoscan 8600F scanner  working. I'm assuming I'm out of luck since there is no Linux drivers for it **.
**2. My DVD Burner is not burning.  I have  tried various medias and have no problems with it in Vista. I have also tried Brasero, GnomeBaker   I'm using  device below:**
# hdparm -i /dev/dvd
/dev/dvd:
Model=HL-DT-ST DVDRAM GH40L , FwRev=LM02 , SerialNo=684BEE7A70DA 
Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
BuffType=unknown, BuffSize=0kB, MaxMultSect=0
(maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio3 pio4 
DMA modes: mdma0 mdma1 mdma2 
UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
AdvancedPM=no
Drive conforms to: unknown: ATA/ATAPI-3,4,5,6,7
  Error Message:
  BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 41
BraseroGrowisofs stderr:   1.42% done, estimate finish Wed Nov 25 12:54:39 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   2.84% done, estimate finish Wed Nov 25 12:54:39 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   4.26% done, estimate finish Wed Nov 25 12:54:39 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: engaging DVD-RW DAO upon user request...
BraseroGrowisofs stderr: /dev/sr0: reserving 352147 blocks
BraseroGrowisofs stderr: , warning for short DAO recording
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 2.0x1352KBps.
BraseroGrowisofs stderr: :-[ TEST UNIT READY failed with SK=2h/LOGICAL UNIT NOT READY, LONG WRITE IN PROGRESS]: Resource temporarily unavailable
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=5h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type
BraseroGrowisofs stderr: :-( media is not formatted or unsupported.
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: :-( write failed: Wrong medium type
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 124
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811 

  
**3. I can not login to any of my servers using  logmein.com website. I have tried it with firefox, Opera and even IE6 from Wine.  I have java installed and when try to login it gets all the way to Negotiating  and then just dies with "Your Connection to the remote computer has been lost  Negotiating SSL..." See attached image. I have no problem from windows which is  using the same network on the 1st partition of the same box. I can also use  vertualbox from windows which has the 32bit version of Mint and it will also  work so I'm wondering if it's a 64bit issue.**

FYI: I'm running an Intel quad core with 8GB Ram so that's why I would like to  utilize the 64 bit version
   [IMG]http://forums.linuxmint.com/download/file.php?id=2645[/IMG]

---

### Post by topcause on 2009-11-27
Well I eneded up downgraded to the 32bit version. Logmein works fine in that environment. Still issues with DVD and Scanner...

---

### Post by bodhi.zazen on 2009-11-27
Those are odd errors, I wish I had a solution.

---

### Post by arcofire on 2009-11-27
I sympathise with you as I had initial problems starting with Linux. But I did sort them all out, with help from here and elsewhere. I know I was lucky. This was two years ago. Now that I only use Linux I never buy hardware that is unsupported.

But it's hard starting out.

I don't have any answers to your questions but maybe if you took each problem and made a separate post of it, with the problem summarised in the heading.

This might get more people here to respond, as they will know your problem while scanning the headlines. :)

---

### Post by topcause on 2009-11-30
Thanks arcofire but I'm not giving up just yet.  
I ended up fixing the Logmein issue by removing the 64 and installing the 32 bit SMP which still gives me my 8GB in Ram and I have not seen any performance degradation.
 
For the burner I ended up plugging in my external Lite-On which works with no problem. I guess Linux is not very compatible with SATA LG Burners.
 
I'm still battling the Scanner issue, from what I hear Canoscan 8600F is compatible but noone has put together a driver for it yet.

---

### Post by Locutus_of_Borg on 2009-11-30
try using this command to burn a dvd:
for an iso ```
 cdrecord dev=/dev/sr0 file.iso
```
for data```
growisofs -dvd-compat -Z /dev/sr0 -joliet-long -R /directory/
```
for video: convert to iso with mencoder and dvdauthor then burn as iso


what is the output of lsusb when you have your scanner plugged in?

---

### Post by topcause on 2009-11-30
[SIZE=2]Locutus_of_Borg below is what I get when try to burn the test.iso file:[/SIZE]
[COLOR=DarkRed]topcause@UBUNTU-1:~$ cdrecord dev=/dev/sr0 file.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
WARNING: /dev/sr0 seems to be mounted!
wodim: Device or resource busy. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.[/COLOR]

[SIZE=2]Below is the output of  lsusb.  So we know OS can see the Canon on Bus 001 Device 003 but no drivers to configure it.[/SIZE]
[COLOR=DarkRed]topcause@UBUNTU-1:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:2b17 Hewlett-Packard LaserJet 1020
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 004: ID 06f8:3005 Guillemot Corp. Hercules Dualpix Exchange
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04a9:2229 Canon, Inc. 
Bus 001 Device 002: ID 1c6b:a122 Philips & Lite-ON Digital Solutions Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]

---

### Post by Locutus_of_Borg on 2009-11-30
"Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second."

is the disk in use?
it should be unmounted and not in use by anything.



as for the canon, i dont know, all i can suggest is google, sorry

---

### Post by topcause on 2009-11-30
I've tried unmounting & mounting. Tried using a different blank DVD. Tried using the same blank DVD in the external burner and it works fine. Also the dev/sr0 has no problem playing the media, it just cant burn...
Also I know the actual drive is not defective because it works fine in XP or Vista. 
Strange....

---

### Post by Locutus_of_Borg on 2009-11-30
i dont know then

i assume ubuntu modularizes the scsi cdrom kernel parameter, but i dont use ubuntu so i cant say for sure, you could always rebuild the kernel with that built-in

but that seems like an unreasonable course of action

before giving up on linux you could try some other distributions and see how they work

personally, i am a fan of slackware (or slax if you want a live cd)

---

### Post by topcause on 2009-11-30
I've tried many distros and Ubuntu and Mint seem to have worked out best overall. I'll give slackware a try also but from a quick research it seems like they don't have a solid package management in place, I would hate to have to deal with Dependency nightmares... :)

---

### Post by Locutus_of_Borg on 2009-11-30
in my opinion, pkgtool is the most solid package manager i've ever used, and i've used most of the major distros over the years

it does not do dependency resolution, however, instead of a package system that breaks up every single application into *-core *-dev *-lib *-etc like ubuntu does, you get a full linux install, and there are tools like sbopkg that automate the download, compilation, and installation of source file packages, all you need to do is read the README files for dependency information or at worse, look at the output of ./configure 

personally, the stablity, fullness, and complete control slackware offers far outweighs the "easiness" of installing with apt

---

### Post by topcause on 2009-11-30
I will definitly give it try. I have couple of empty partitions and nothing to lose.
 
Thanks
TC

---

### Post by steveneddy on 2009-12-01
For scanning and printing, please try HP printers (all in one'ss work great) and use HP's linux software from the website, not the repos.

[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

For the DVD solution, either change the DVD burner or keep using the external burner.

You might also try looking at [System76]("http://www.system76.com/") for a system prebuilt with Ubuntu installed already. 

Wish I could help more.

---

### Post by chrisbay90 on 2009-12-01
I dont have the solution to your particular problem. I wish you all the best and hope you get it to work. I have a few words on the subject though.

Linux may seem like a struggle at first, but if you stick with it you will master it. Once you master it, you will love it, i guarantee. Unfortunately though, Linux is a little dry on the driver front. The veterans will tell you how far it has come, wich is an impressivly long way. But there are still some holes as most vendors just arnt inclined to write them.

Linux has come a long way and for the most part i would say is ready (in the case of distro's like ubuntu) 'out-of-the-box' as an OS anyone with basic computer knowledge can use without any hassles. However if you want to do more than web browse and write letters in openOffice you are going to need to get your hands atleast a little dirty. Linux does fall still fall short in some area's such as driver availabillity and 100% enterprise compatability (more to the fault of third parties than the linux comunity) Although having made it this far, im sure your aware of this.

That being said, i strongly encourage you to keep with it. Linux offers some many advantages, from freedom, cost, speed to customisability and being able to see what your system is doing and control every aspect of it quicky efficiently and easy. Stick in there it will pay off.

I wish you the best of luck with fixing your problems.

---

### Post by topcause on 2009-12-01
I agree with you. Linux has definitely has come a long way. We know Linux is King in certain server environments like web hosting but in order to get the attention of the day to day folks it needs to move more and more towards GUI.  I know many of the old Linux users and coders think certain things are easier done at the terminal but that's because that's how they have been doing it for years and probably also because a good GUI interface is not available for those certain things. I don't care how much of an expert someone is becomes when it comes to command lines, it's more typing and hideous attention to details so a dot or a slash doesn't get missed. I know this first hand.
MAC realized the only way they can survive is to provide what the new generation wants. GUI, Visual Implementations and Automation and that's when rolled out all the new cool apple systems and gadgets.
Again kudos to all the Linux developers for the great work and hopefully the hardware manufactures will soon realize that the new Linux is not the old dependency nightmare that was only sufficient for certain usage.

---


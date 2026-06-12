---
title: "Maverick &quot;Too many connections&quot; on boot"
date: 2010-12-01
forum: General Help
---

### Post by Starmartyr on 2010-12-01
I had experienced the error message "Too many connections" during a boot on a recent install of Maverick.  This occurred just as the boot up screen appeared after selecting 10.10 from the Grub menu.  I had disconnected any external system/plugs that were not needed, and it still happened.  Anyone know what this could have been?

I am currently saving all my data onto my backup drive, then will reformat the harddisk ext4 so that I can load a full clean install of Maverick.  I sure hope it works.

Gigabyte 870A-UD3
G.Skill 4gb DDR3 1600 RAM
AMD Phenom II X4 945 Deneb 3.0ghz
RAIDMAX 700W 80 PLUS Bronze Certified PS
SAMSUNG Spinpoint F3 HD103SJ 1TB 7200 RPM HD

---

### Post by pxc on 2010-12-02
Why reinstall?

I recently began seeing this message (after a migration to a new motherboard and a few other parts), but everything still works as expected. What about w/ you?

---

### Post by piquat on 2010-12-25
I know this is old but I'd thought I'd bump this as I get this also.  Not really a problem but I'm just curious.  

Also a new build here.

None of the same hardware.  It is a new AMD chip thought... 1090T X6.

Only thing that comes to mind is it's setting up a bunch of services at that time right?  Is it trying to do to many at once or issuing too many commands at once or too fast to X?

Everything seems to work but I wonder if this is maybe just a foreshadowing of a bug yet to be turned over.

---

### Post by piquat on 2010-12-25
```

[    9.913720] hda_codec: ALC892: BIOS auto-probing.
[    9.919258] Too many connections
[    9.921290] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.921338] HDA Intel 0000:01:05.1: setting latency timer to 64
[   13.595899] r8169 0000:04:00.0: eth0: link up
[   13.596036] r8169 0000:04:00.0: eth0: link up
[   16.374107] [fglrx] Could not enable MSI; System prevented initialization
[   16.374966] [fglrx] Firegl kernel thread PID: 1326
[   16.375187] [fglrx] IRQ 18 Enabled
[   17.187566] [fglrx] Gart USWC size:1279 M.
[   17.187568] [fglrx] Gart cacheable size:508 M.
[   17.187571] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   17.187572] [fglrx] Reserved FB block: Unshared offset:fbfa000, size:401000 
[   17.187574] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   19.927123] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   23.850915] eth0: no IPv6 routers present
[   25.133953] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   26.257598] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

```

Soooo, that's a problem with ALC892.  Audio.  Which seems to work.

Wonder if there's some ASUS software I haven't loaded up?

---

### Post by archonta on 2010-12-28
I get the "Too many connections" message too, in both Ubuntu and Kubuntu installation attempts. I'm not sure it's the sound chip. Mobo -> 890XA UD3 and CPU - 1090T.
I know I already have an issue with the ATI 6850 drivers already, as they're not officially available. I've seen the log you posted, but I remember the error code being different every time I tried to boot from the live CD. 

- Maybe the error message refers to something else. The term "connections" usually implies a network issue. I patched the LAN drivers, but the problem remains. 

- If you get to finally install the o/s (did you?) sometimes it crashes and gives you the same error message.

- I also see more people complaining about getting this message. I wonder what do they have in common, that causes the problem,  i.e. do you all have an AMD cpu or a Gigabyte mobo, or maybe the UD3 edition stinks (in comparison to the more expensive UD5/UD7), or is it just an incompatibility with the 68xx cards?

---

### Post by piquat on 2010-12-29
> **archonta said:**
> I get the "Too many connections" message too, in both Ubuntu and Kubuntu installation attempts. I'm not sure it's the sound chip. Mobo -> 890XA UD3 and CPU - 1090T.
I know I already have an issue with the ATI 6850 drivers already, as they're not officially available. I've seen the log you posted, but I remember the error code being different every time I tried to boot from the live CD. 
 
- Maybe the error message refers to something else. The term "connections" usually implies a network issue. I patched the LAN drivers, but the problem remains. 
 
- If you get to finally install the o/s (did you?) sometimes it crashes and gives you the same error message.
 
- I also see more people complaining about getting this message. I wonder what do they have in common, that causes the problem, i.e. do you all have an AMD cpu or a Gigabyte mobo, or maybe the UD3 edition stinks (in comparison to the more expensive UD5/UD7), or is it just an incompatibility with the 68xx cards?
 
I don't have a 6800 card. It's onboard at this point (until this weekend that is:guitar:)
 
The term "connections" threw me too. It could refer to network connections but I get this on boot, it shouldn't be creating a lot of connections at that point. What it could be is connections to the Xserver.
 
One thing to note here... you mentioned that you have a 1090t. Well, so do I. Asus MB though. I have a hard time believing all these people recently got 1090t's. LOL
 
Also, I don't remember if this happened when booting a live disc. It happens to me at boot, EVERY boot. I should really spend some time today looking through dmesg. I kind of forgot about this as it's currently causing no problems.

---

### Post by jorisctn on 2010-12-29
Same problem (?) here.
I have a fresh install of Maverick (64 bit desktop) on new hardware:

Asus Sabertooth X58
Intel Core i7 950
12 GB Kingston memory
OCZ Vertex2 SSD 240 GB
WD Caviar black 2 TB
Asus ENGTX 460

and get the "Too many connections" message on every boot.
Everything seems to work OK. I only use analog audio, so I don't know whether there is something wrong with HD audio.

The relevant (?) part of dmesg follows underneath.

I'm curious to learn what might be wrong.


[    7.524548] hda_codec: ALC892: BIOS auto-probing.
[    7.529980] Too many connections
[    7.531340]   alloc irq_desc for 34 on node -1
[    7.531342]   alloc kstat_irqs on node -1
[    7.531350] HDA Intel 0000:03:00.1: PCI INT B -> GSI 34 (level, low) -> IRQ 34
[    7.531353] hda_intel: Disable MSI for Nvidia chipset
[    7.531585] HDA Intel 0000:03:00.1: setting latency timer to 64

---

### Post by piquat on 2010-12-30
1090t i7-950
 
The only thing our systems have in common is they have fast CPU's and newer systems/motherboards.  I don't think it's the CPU though.  It happens right after the BIOS probe.  I assume that means it's looking for hardware and assigning addressing at that point.  Hmmmm, we all probably have fairly new BIOS's....

---

### Post by jorisctn on 2010-12-30
My MB has AMI BIOS version 0603, build date 10/29/10. 
I checked at the ASUS site that this is the latest version.

I also checked that the live CD throws the same "Too many connections" message during boot.

The default setting for PnP devices is such that the BIOS configures them all. In the advanced menu I changed this setting to "Yes" (meaning the OS instead of BIOS will configure all PnP devices, not required for boot). Also with this setting the "Too many connections" message remains.

---

### Post by piquat on 2010-12-30
> **jorisctn said:**
> My MB has AMI BIOS version 0603, build date 10/29/10. 
I checked at the ASUS site that this is the latest version.
 
I also checked that the live CD throws the same "Too many connections" message during boot.
 
The default setting for PnP devices is such that the BIOS configures them all.
 
Is that the setting that's something like "PnP OS       yes/no".  If that's what you're talking about, mine is set to yes.

---

### Post by jorisctn on 2010-12-30
> **piquat said:**
> Is that the setting that's something like "PnP OS       yes/no".  If that's what you're talking about, mine is set to yes.

Yes, it is.
In my manual it reads: "Plug And Play O/S [No]"
Since the default value is "No" and there seems to be no difference as far as the "Too many connections" message concerned, I set it back to "No"

---

### Post by jorisctn on 2010-12-31
> **piquat said:**
> 
Soooo, that's a problem with ALC892.  Audio.  Which seems to work.

Wonder if there's some ASUS software I haven't loaded up?

Just to make sure that indeed the communication with the ALC892 is the source of the "Too many connections" message I disabled HD audio in the BIOS and the message disappeared.

Driver problem?

---

### Post by piquat on 2010-12-31
> **jorisctn said:**
> Just to make sure that indeed the communication with the ALC892 is the source of the "Too many connections" message I disabled HD audio in the BIOS and the message disappeared.

Driver problem?

Hey!  Good idea!  Wish I had thought of that.

I have no idea where to go with this though.

I guess this means wait until the next kernel?  Newbie not sure....

---

### Post by jorisctn on 2010-12-31
> **piquat said:**
> Hey!  Good idea!  Wish I had thought of that.

I have no idea where to go with this though.

I guess this means wait until the next kernel?  Newbie not sure....

Glad to hear you like the idea :)
Agree with you that we probably have to wait for a new kernel.
Not a problem for me though because I'm happy with Analog Audio for now.

I don't expect any harm from the daily message "Too many connections", thanks to your contribution to the discussion on this forum.

---

### Post by jermza on 2011-01-02
I also get this message just before Ubuntu's login screen appears.  I have an i7 chip and a new-ish Asus motherboard.

Everything seems to work fine, though.  Ignoring it, however, seems pointless because it's probably something that is happening for a reason.  Plus, it looks unpolished.

Any ideas what it is?

---

### Post by myromance123 on 2011-01-25
Not to dig up a kind of old thread but, I have this as well. Only problem here though is that I don't have sound at all at the moment with Ubuntu 10.10 64-bit.

System Specs:
Proc: AMD Phenom II x4 965 BE
Mobo: Asus m4a88T-V EVO/USB3

Same onboard HDA device as you guys, Realtek ALC892. The "too many connections" problem might have something to do with how it connects to the PCI Bus, then again it could be anything. There is also a ATI/AMD HDMI Sound device, but I'm unsure what this is from the BIOS. I would have thought anything HDMI would be from a graphics card but this is seemingly integrated as well. 2 Audio devices? In Ubuntu however it only registers the Intel HDA Azalia device and ATI card hdmi sound I have. In Windows its another story.

Its the ALC892 for sure thats causing this. Sadly I have no sound at all. Wouldn't mind Analog sound at least :(

From dmesg I get:
```
[    9.383694] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.652185] hda_codec: ALC892: BIOS auto-probing.
[    9.658568] Too many connections
[    9.659916] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.659964]   alloc irq_desc for 44 on node 0
[    9.659965]   alloc kstat_irqs on node 0
[    9.659973] HDA Intel 0000:01:00.1: irq 44 for MSI/MSI-X
[    9.659991] HDA Intel 0000:01:00.1: setting latency timer to 64
[   11.082316] type=1400 audit(1295991305.355:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=856 comm="apparmor_parser"
[   11.082491] type=1400 audit(1295991305.355:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=856 comm="apparmor_parser"
[   11.082591] type=1400 audit(1295991305.355:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=856 comm="apparmor_parser"
[   11.153781] type=1400 audit(1295991305.425:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=860 comm="apparmor_parser"
[   11.726137] ppdev: user-space parallel port driver
[   14.384402] r8169 0000:02:00.0: eth0: link up
[   14.384407] r8169 0000:02:00.0: eth0: link up
[   18.258591]   alloc irq_desc for 45 on node 0
[   18.258594]   alloc kstat_irqs on node 0
[   18.258602] fglrx_pci 0000:01:00.0: irq 45 for MSI/MSI-X
[   18.259032] [fglrx] Firegl kernel thread PID: 1218
[   18.259203] [fglrx] IRQ 45 Enabled
[   18.558264] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   19.597930] [fglrx] Gart USWC size:1240 M.
[   19.597933] [fglrx] Gart cacheable size:491 M.
[   19.597936] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   19.597938] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000 
[   19.597939] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   24.412549] eth0: no IPv6 routers present
[   29.050209] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   29.575200] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

```

Just sharing in case anyone knows a fix, till then its a kernel wait eh...

---

### Post by piquat on 2011-01-26
No, it's great.  Do bump.  I'm enjoying the fact that it's not only me.

If you would, scroll up a few posts and you'll find this

> Just to make sure that indeed the communication with the ALC892 is the  source of the "Too many connections" message I disabled HD audio in the  BIOS and the message disappeared.Try disabling HD audio in the bios and see if you then have analog audio.

Also, since you've been around a while, where most of the rest of us in this thread seem to be newbs, is there even a bug report on this?  I haven't the slightest clue how to search for one on... I think it's launchpad, correct?  And if I didn't find one, I'm too new to have the correct details to properly describe the problem, I think anyway.  Any assistance you could offer would be great!

Thanks.

---

### Post by dsjstc on 2011-01-28
If your issue is this bug, I suggest you subscribe to the bug as "affects me too".
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448)

---

### Post by piquat on 2011-01-28
> **dsjstc said:**
> If your issue is this bug, I suggest you subscribe to the bug as "affects me too".
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448)
 
Thank you very much!  I probably wouldn't have found that on my own.


Edit:  Subscribed.

2nd edit:  Looking at that report doesn't instill any confidence in me.  It was reported over 6 months ago, only has 5 complainants at this point, hasn't been assigned to anybody and worst of all, it doesn't really stop anything from functioning most of the time so most people won't even notice it.  /sigh

---

### Post by Foxcow on 2011-02-03
I'm also getting this error after upgrading to a 1090T and MSI 870A-G54.

---

### Post by piquat on 2011-02-03
> **Foxcow said:**
> I'm also getting this error after upgrading to a 1090T and MSI 870A-G54.

If you haven't already, please check out dsjtc's link and subscribe to the bug if it sounds like your problem.

Thanks.

---

### Post by Foxcow on 2011-02-03
> **piquat said:**
> If you haven't already, please check out dsjtc's link and subscribe to the bug if it sounds like your problem.

Thanks.

Just finished doing that.  Thanks.


So I basically have a useless system now?

---

### Post by Foxcow on 2011-02-04
Well according to a very diligent person on launchpad, you have to rebuild the kernel to get this to work.

> 
One last tidbit. I finally figured out what the IDE controller was and why it was loading and being controlled by ata_piix. This board is an Intel vPro board and it supports IDE redirection over LAN. Basically at the firmware level it lets be remote mount an ISO image as if it was a locally connected CD-ROM drive.

This virtual IDE CD-ROM drive is what is connected to the controller that ata_piix is driving. So the system was behaving as expected outside of the very slow boot.

So in summary. all that is needed to fix this bug is to change CONFIG_SATA_AHCI= to 'y' from 'm'.

I verified it by making the change in debian.master/config/amd64/config/config.flavour.*

I then rebuilt the lucid kernel, installed it and I am a happy ubuntu user again.



Has anyone ever tried to do this before?

---

### Post by Foxcow on 2011-02-05
Just out of curiosity, does everyone with the problem have a dual screen?  

I re-installed and carefully installed updates until I got setting up my second monitor.  I made a backup of xorg.config in my etc/X11 directory.  Then, I configured my xorg.conf file by running 'sudo nvidia-settings' in the terminal.  Upon reboot, I got the "too many connections" error.  I was able to sign in, revert to the backed up xorg.conf, reboot and all is well.

---

### Post by piquat on 2011-02-07
> **Foxcow said:**
> Just out of curiosity, does everyone with the problem have a dual screen? 
 
I re-installed and carefully installed updates until I got setting up my second monitor. I made a backup of xorg.config in my etc/X11 directory. Then, I configured my xorg.conf file by running 'sudo nvidia-settings' in the terminal. Upon reboot, I got the "too many connections" error. I was able to sign in, revert to the backed up xorg.conf, reboot and all is well.
 
No, single monitor here.
 
And no, your system is not useless.  Actually, it's not causing much problems RIGHT NOW.  I wish it were as it's not getting much attention...

---

### Post by notlistening on 2011-02-13
I have found the on my system that if I disconnect the CD drive from the IDE interface that the system boots with no hang or delay. This seems strange to me.


There is still the battle between the different disk controller drivers but it does not hang. 

Strange bug this one. Will try some firmware update to see if they help.

---

### Post by Wolf-Ekkehard on 2011-02-14
At the expense of adding yet another voice that won't really help the issue along, but just to increment the occurrence counter.... I am getting the same error message during boot.  The system is a brand new build using an ASUS M4A88TD-V EVO/USB3 mobo (with a built-in ALC892 8 channel HD Audio) with an AMD Phenom II X6 1055T and a 10.10 amd64 brand-new Kubuntu install.

---

### Post by piquat on 2011-02-15
> **Wolf-Ekkehard said:**
> At the expense of adding yet another voice that won't really help the issue along, but just to increment the occurrence counter.... I am getting the same error message during boot.  The system is a brand new build using an ASUS M4A88TD-V EVO/USB3 mobo (with a built-in ALC892 8 channel HD Audio) with an AMD Phenom II X6 1055T and a 10.10 amd64 brand-new Kubuntu install.

Pretty close to the same hardware.

May not help, but it sure is interesting.

Thanks!):P

---

### Post by el_Paraguayo on 2011-02-18
Same issue here too.

New build: Gigabyte GA870A-UD3 motherboard. Mythbuntu 10.10.

Not causing me too much of an issue.

And I am getting digital audio out through my coax socket.

---

### Post by mn_voyageur on 2011-02-20
Yup.  Too many connections on my new box.  Running Ubuntu 10.10 (Linux 2.6.35-25-generic (x86_64))

I too have the MSI 870A-G54. AMD Athlon II X4 635 Processor

I have dual screens. (Radeon HD 5750) 

I no IDE equipment installed.

Since this is a second system for me, I am willing to be a guinea pig.

MarkN

FYI - My kids prefer Ubuntu over MS!

---

### Post by KalashNK on 2011-02-21
Same problem (audio works though)

AMD Phenom II 965BE
4G RAM G.Skill Rypjaws
Gygabite 890GPA-UD3H
ATI Radeon HD 5750

K.

---

### Post by montyleew on 2011-02-21
Thought I better chime in also.

Same problem. Analog audio works, haven't tried digital.

AMD Phenom II X4 955BE
8GB RAM, GSkill DDR3 1600
Gygabite 890GPA-UD3H 
ATI Radeon HD 4850
Dual Monitor

Are any Intel systems having this problem?

---

### Post by grim2 on 2011-02-21
Me too.
AMD Phenom II x6 1055
Gigabyte 890GPA-UD3H
8G RAM - Corsair
nVidia GeForce GT 240

Everything seems to work.

---

### Post by smiffsoft on 2011-02-25
Me too.
AMD Phenom II x4 965
ASUS M4A88TD-V EVO/USB3
8G RAM - G.Skill Ripjaw
nVidia GeForce 9800 GT
Audio - HDA-Intel - HDA ATI SB

My sound is completely dead.  It did work when I rebooted and disabled the Audio in the BIOS, then rebooted and turned it back on again, however even that has stopped fixing the issue for me now.

---

### Post by yeats on 2011-02-25
> **dsjstc said:**
> If your issue is this bug, I suggest you subscribe to the bug as "affects me too".
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448)

This bug does not seem to be relevant to this issue (or maybe I'm missing something - entirely possible :-) ).  I was led to this thread while troubleshooting a sudden lack of sound and the

```
[   11.476642] hda_codec: ALC892: BIOS auto-probing.
[   11.482561] Too many connections

```

messages.  My specs are very similar to the other posters:

AMD Phenom II x6 1055T
Gigabyte 870A-UD3
4G RAM - Kingston
nVidia GeForce 9800 GTX+

I've not yet gotten into the BIOS to play with disabling digital audio, but I suddenly am not able to hear sound.  This is also after removing pulseaudio, but I think that may be irrelevant since this seems to be a kernel bug.

---

### Post by yeats on 2011-02-25
Another fact:  I noticed that my speakers pop loudly at the same moment that the "Too many connections" message appears.  Do others hear that too?

---

### Post by WiuEmPe on 2011-02-26
[http://www.linuxforums.org/forum/gaming-multimedia-entertainment/168732-solved-no-sound-alsa-except-microphone.html](http://www.linuxforums.org/forum/gaming-multimedia-entertainment/168732-solved-no-sound-alsa-except-microphone.html)

And i have this same problem on my hardware:
Asrock 770 Extreme3
AMD Phenom(tm) II X4 955 Processor

---

### Post by dsjstc on 2011-02-26
Please start a different thread for discussion of audio.  It does not appear related to the "too many connections" issue.

---

### Post by luke_ar on 2011-02-28
Hi! I've got both problems mentioned here.

Motherboard - M4A88TD-V EVO/USB3
ALC892

uname -r
2.6.35-22-generic

Did anyone fixed it? I remember having the "Too many connections" problem and audio working fine, and some day the audio didn't work anymore.

---

### Post by Veld on 2011-02-28
I get that same "too many connections" message at boot and sometimes during shutdown (everything works fine, though).

Here are my specs:

AMD Phenom II X4 955 BE
Asus M4A88TD-M EVO/USB3
Kingston Kit 4GB DDR3 1333MHZ
Samsung 1TB SATA II 32MB F3

LC-POWER 560W GREEN POWER V2.3 (LC6560GP3)
Samsung DVD±R 22X SH-S223
Revoltec Multicard reader

---

### Post by gunsmoke on 2011-03-05
I get that same "too many connections" message at boot (everything works fine, though).

Found a similar submitted bug here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/720799]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/720799")



Here are my specs:

AMD Phenom II X6 T1090
Asus M4A88TD-M EVO/USB3
Corsair Kit 4GB DDR3 1333MHZ
Samsung 1,5TB SATA II 32MB F3

---

### Post by nasuh on 2011-03-18
I have same problem, everything works also.

My specs 
AMD Athlon II X3 445
Asus M4A88TD-M EVO/USB3
OCZ 40GB SSD

---

### Post by nasuh on 2011-03-18
oooops

---

### Post by CiaoCiao on 2011-03-20
I just wanted to reply since I am amazed I have the same hardware as so many others with the same problem..

It affects me as well.  
Analog audio works, haven't tried digital.

Asus M4A88TD-V/EVO USB3
AMD X4 965 BE
8 GB RAM
single monitor onboard DVI video.

---

### Post by Kirboosy on 2011-03-30
> **CiaoCiao said:**
> I just wanted to reply since I am amazed I have the same hardware as so many others with the same problem..

It affects me as well.  
Analog audio works, haven't tried digital.

Asus M4A88TD-V/EVO USB3
AMD X4 965 BE
8 GB RAM
single monitor onboard DVI video.

Same exact setup plus I have a MSI Twin Frozr 250 1 Gb OC. I also have the same issue. Maybe 11.04 will fix it.

---

### Post by Wolf-Ekkehard on 2011-03-30
Unlikely that it is gonna be fixed any time soon, since I don't think Upstream even knows about this.  Has anybody filed a bug report?  I wouldn't even know against what.... :-(

Could any kind moderator soul step in and help us out with this?

---

### Post by ipsi on 2011-03-31
I'm seeing this too, on:

```
Intel BOXDH67CLB3 Motherboard, Socket 1155
Intel Core i7-2600
16GiB Corsair CMV4GX3M1A1333C9 (4x4GiB)
NVidia GTX 570 (Proprietary Drivers)
```

To the best of my knowledge, I have no issues at present. Audio works, video works, etc.

EDIT: Booting is pretty quick, and this message typically appears around the 5-10 second mark. I haven't timed the boot, but it's quick enough that I'm pretty sure this isn't the issue mentioned earlier ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448)).

Log:
```
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    4.958467] udev[425]: starting version 163
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.258812] lp: driver loaded but no devices found
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.267393] type=1400 audit(1301570879.842:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=566 comm="apparmor_parser"
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.267400] type=1400 audit(1301570879.842:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=543 comm="apparmor_parser"
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.267844] type=1400 audit(1301570879.842:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=566 comm="apparmor_parser"
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.267853] type=1400 audit(1301570879.842:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=543 comm="apparmor_parser"
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.268082] type=1400 audit(1301570879.842:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=566 comm="apparmor_parser"
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.268094] type=1400 audit(1301570879.842:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=543 comm="apparmor_parser"
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.378104] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.568749] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.570861] rtusb init --->
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.570926] === pAd = ffffc90007b47000, size = 504952 ===
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.570927] <-- RTMPAllocAdapterBlock, Status=0
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.571454] usbcore: registered new interface driver rt2870
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.679555] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.697712] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.697766] xhci_hcd 0000:04:00.0: setting latency timer to 64
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.697777] xhci_hcd 0000:04:00.0: xHCI Host Controller
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.697820] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.697983] xhci_hcd 0000:04:00.0: irq 19, io mem 0xf7100000
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.701303] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.701343] xHCI xhci_add_endpoint called for root hub
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.701344] xHCI xhci_check_bandwidth called for root hub
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.701358] hub 3-0:1.0: USB hub found
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.701381] hub 3-0:1.0: 4 ports detected
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    6.969315] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: user_xattr
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    7.191393]   alloc irq_desc for 22 on node -1
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    7.191395]   alloc kstat_irqs on node -1
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    7.191400] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    7.191479]   alloc irq_desc for 45 on node -1
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    7.191480]   alloc kstat_irqs on node -1
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    7.191489] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    7.191511] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    8.150638] hda_codec: ALC892: BIOS auto-probing.
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    8.519545] Too many connections
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    8.521202] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    8.521204] hda_intel: Disable MSI for Nvidia chipset
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    8.521282] HDA Intel 0000:01:00.1: setting latency timer to 64
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    8.697806] nvidia: module license 'NVIDIA' taints kernel.
Apr  1 00:28:02 ipsi-desktop-lx kernel: [    8.697808] Disabling lock debugging due to kernel taint
```

---

### Post by coprolites on 2011-04-01
I get the "Too many connections" message on boot as well.

Gigabyte GA-P67A-UD3R (rev.1.0)
Intel i5-2500
Gigabyte GTX460OC 1GB
Corsair CMX4GX3M2A1600C9 (x2)
Samsung Spinpoint F3 1TB

No issues really, I just don't like error messages.

Hopefully this will be fixed on Natty..

---

### Post by JanvL on 2011-04-15
I had the problem that the system would not boot with an EDI CD-ROM or CD-RW.
With a SATA CD-ROM it works.

After putting in a GIGAbyte GF220 I get the "too many connections" and no sound.

ASUS M4A88TD-V EVO/USB3
Athlon 640 II x 4

I will try to disable HD sound in the bios.

Thanks for all the info, lets hope for a solution . . . . 

Jan

---

### Post by rklapp on 2011-04-16
> **Foxcow said:**
> Just out of curiosity, does everyone with the problem have a dual screen?  

I re-installed and carefully installed updates until I got setting up my second monitor.  I made a backup of xorg.config in my etc/X11 directory.  Then, I configured my xorg.conf file by running 'sudo nvidia-settings' in the terminal.  Upon reboot, I got the "too many connections" error.  I was able to sign in, revert to the backed up xorg.conf, reboot and all is well.
I'm a Linux newb and need specific help, please. When I install Xubuntu, I can't find a xorg.conf file in the X11 folder. It only exists after I try to activate the nvidia driver. When I try the sudo command, it says command not found. After I activate the nvidia driver, I can only get to the desktop through the failsafe graphics mode.

---

### Post by Foxcow on 2011-04-16
> **rklapp said:**
> I'm a Linux newb and need specific help, please. When I install Xubuntu, I can't find a xorg.conf file in the X11 folder. It only exists after I try to activate the nvidia driver. When I try the sudo command, it says command not found. After I activate the nvidia driver, I can only get to the desktop through the failsafe graphics mode.


I can try and help you with that problem but rather than do it in this thread, I think it would be most appropriate for you to make another thread and point me in its direction.  I know how frustrating it is to have a thread de-railed. :D

If you don't figure it out and make a new thread, please PM me a link so I can try to help you.

---

### Post by rklapp on 2011-04-17
Solved. When I went to the nvidia driver download page, I noticed that they had certified linux driver for my 470 gpu and beta driver for my 560ti. I swapped the gpus so the 470 is first, 560 second, and 9800gt third. I then loaded the updates and the graphics driver. When I boot, it still gives me the Too Many Connections message but when it shows the login tty question, the graphics skips over to the normal login screen. Seems to be fine now. Although you didn't specifically help me, it was enough to get the juices flowing and figure out the problem. Thanks.

I'm still trying to figure out how to read the cpu temp in linux that is reported in the BIOS. Any suggestions?

---


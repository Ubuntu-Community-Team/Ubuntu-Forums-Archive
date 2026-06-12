---
title: "Lucid Lynx + linux-image-pae + fglrx problem"
date: 2010-05-01
forum: General Help
---

### Post by rodrigorenie on 2010-05-01
Hello Forum

As soon as it was release, I've already installed Ubuntu 10.04 Lucid Lynx in my computer and, since I've 4GB RAM, Ubuntu automatically installed the PAE version of the kernel (linux-image-2.6.32-22-generic-pae).

Initially, no problems, until I tried to install the fglrx packages to use 3D acceleration of my onboard HD 3200 video. The installation was successful and the module load withou any problem, but the video after X restarted got corrupted, barely usable, as you can see in the screenshot I took of my screen with the problem. Itried rebooting the machine and the problem continued. Also tried removing the entire fglrx from ubuntu and installing the latest driver in the ATI website, but the same problem happend.

And it only happens with the PAE version of the kernel. I installed the normal version, without PAE, and the video is working perfectly.


Any ideas of what could be the problem? Any more information I can provide to help solving the problem?

thks


lspci:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by rodrigorenie on 2010-05-05
bump

---

### Post by Jean-Joey on 2010-06-05
I have problem too with the driver.. I cannot see the login window afte suspend/ screen saver and when maximizing/ minimizing and with other windows effects the graphics sucks
 any help? no one could help me!!

---

### Post by buanzo on 2010-06-16
Just happened to me.
I recently installed pae kernel on a previously non-pae system, I noticed really slow video output with my ATI 4830.... so I checked Xorg.log for EE|WW and noticed the issue.

On a side note, I googled "fglrx linux pae" and this thread is top-1 :P
:popcorn:

---

### Post by vanquishedangel on 2010-08-03
Bump

Sort of...... How i Fixed it, or rather broke it in mine. I have a HD 2400xt ati card on a dc7100 3.0 ghz intel with 4 gigs ram. I didn't originally have 4 gigs of ram, I had 3 1gig sticks and a 256mb stick That is important because I couldn't install lucid or karmic because of the pae, memory wasn't even for pae to "address" it. when I tried to install Lucid or karmic it brought me to a log in screen and once gave a "not enough space" error. I had dual channel memory so pae couldn't map it correctly with out the ram being equal in one of the channels.

So I had to upgrade from Hardy all the way to lucid, change to ext4 file-system and then I learned of pae, and in hardy, pae is not installed or enabled so when i updated, it was never installed so I tried to do it manually (big mistake). I disabled the proprietary drivers and then installed the pae files, then re-did grub, and rebooted, upon start up I got a message about "low graphics mode" then I re-enabled the drivers, rebooted and got an "error 24 something about memory block" also got a few "error 13" in there. When I tried to enable the open gl drivers I got the same thing, in all my kernels that were installed after enabling the drivers for the card (open gl or ati).

In the end I ended up re-installing Ubuntu since i couldn't boot but the memory error gave me a clue that I needed to replace the 256mb stick with a gig stick so i did. I then tried lucid live, and it worked. Not only that, but it installed pae right from the disk, I was so afraid to try ati drivers at all but i Downloaded the ones from the site and to my relief, they are working like a charm, at least until the kernel updates lol. BTW the only live cd i had was hardy at the time and it wont read ext4 from the disk.

I wrote all this so I may share that experience so others learn from it or a solution maybe found. I don't think the ati or pae function properly together unless  all channels of memory match in size and possibly speed.
As in a system with 4 slots with 2 channels, both slots in the same channel must be identical is my theory. Sorry if I got wordy, I cut a lot of the headaches i had out of the story lol, because they didn't work. Now i am going to bed, Good Luck.

---


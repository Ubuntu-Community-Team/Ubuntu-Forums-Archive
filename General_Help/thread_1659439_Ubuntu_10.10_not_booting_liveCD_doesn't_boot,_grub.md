---
title: "Ubuntu 10.10 not booting: liveCD doesn't boot, grub recovery mode doesn't boot"
date: 2011-01-04
forum: General Help
---

### Post by didibus on 2011-01-04
Hi,

I'm having a strange problem. Ubuntu 10.10 doesn't boot at all. The liveCD only boots once every like 30 attempts, installing from liveCD froze, but the Alternate CD worked and installed ubuntu. Now when I try to boot into it using GRUB, it freezes at the beginning of the boot process.

With normal boot it freezes at line: Starting AppArmor profiles Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

With recovery mode it freezes even before showing me anything

A little kinda like the liveCD, if I try like 30 times, it might manage to boot once in normal mode.

How do I fix it?

---------------
More details:

the liveCD freezes at: [xxx.xxx] Buffer I/o error on device fd0, logical block 0 [xxx.xxx]

That line keeps on repeating, the the xxx.xxx integer changes each time, and this goes on forever.

I tried removing my floppy drive, but it didn't help.
I tried to boot with fd0=noprobe

The one time it booted, when I restarted, it froze while trying to restart.

---

### Post by mikewhatever on 2011-01-04
How old/new is that computer? Can you also provide its hardware specs.

---

### Post by EdforUB on 2011-01-04
My PC is about 11 years old and I get the error message that cmov is not found on the CPU. Any help advice would be most greatfully appreciated. Thanks.

---

### Post by mikewhatever on 2011-01-04
Thanks for posting the age, that's useful, and let's assume that you haven't posted any specs because you don't know. I suspect the computer may be too old to run Ubuntu. The latest versions require about 256MB of RAM to run, not including the shared graphical memory. I'd suggest trying a more lightweight distro like Slitaz, PuppyLinux or AniX.

---

### Post by didibus on 2011-01-04
The computer is a Pentium 4 - 3.00ghz with hyper threading, 2048mb of DDR2 ram, and a Radeon 9600SE graphics card. It has a Sound Blaster Audigy sound card and Belkin wireless G wifi card.

I doubt it's because the computer is underpowered, especially since I manage to get ubuntu to boot once every 20-30 tries, and once it does, the OS runs incredibly smooth. I'm thinking it might be an incompatibility with one of the component, but since it sometimes manages to boot, I'm wondering if there is some kind of auto-detection of some of the drivers that for some reason, picks the wrong driver 29 out of 30 attempts.


@EdforUB: maybe you should start your own thread, because we don't seem to have the same problem at all. CMOV is a cpu OpCode that only exists in i686 and above processors, so if you have an older processor, it won't work. eg.: AMD k6 does not have the CMOV opcode. If you still want linux, you need to install a version of it that was compiled for older processors.

---

### Post by Krytarik on 2011-01-04
I had the same behaviour with one install-CD at my mum's machine, it also has a Radeon 9600 (XT version). It was the 10.04.1 Lucid version. I didn't need to fix it that time.

Try setting the "radeon.modeset"-option:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting) (section "KMS with a Radeon card")

---

### Post by didibus on 2011-01-05
I found the cause of the problem, but don't know the solution. It seems by removing the belkin wifi G card from the computer, then ubuntu boots just fine. Now how can I make ubuntu work nicelly with my card? I know it can, because sometimes it manages to boot with the card in and wifi works.

Thank You

---

### Post by Krytarik on 2011-01-05
It could be a conflict with "ndiswrapper", try disabling it if it's active:
[http://ubuntuforums.org/showthread.php?t=866252](http://ubuntuforums.org/showthread.php?t=866252)

You may also have to remove (purge) the respective packages:
ndiswrapper-common
ndiswrapper-utils-1.9 (if installed)

---

### Post by didibus on 2011-01-05
So it seems that the ndiswrapper isn't present on my system.

I managed to find out that my card is a Belkin F5D7000 v7032 and that it uses the RealTek chipset and the rtl818x drivers.

I tried to blacklist these:
blacklist rtl8180
blacklist rtl8181
blacklist rtl8182
blacklist rtl8183
blacklist rtl8184
blacklist rtl8185
blacklist rtl8186
blacklist rtl8187
blacklist rtl8188
blacklist rtl8189

When I do blacklist these in the /etc/modprobe.d/blacklist.conf, then I can boot into ubuntu, but obviously, my wifi card doesn't get detected. I'm starting to think it might just not be supported...

---

### Post by Krytarik on 2011-01-05
Try to find out exactly which module should support your card and only blacklist the others.

---

### Post by didibus on 2011-01-06
I found how to fix this problem and have the Belkin F5D7000 v7032 rev 20 work under ubuntu 10.10 Maverick.

Short Answer:

Install ubuntu with your card removed. Blacklist rtl8180. Put back your PCI card. Install the drivers for the card using ndiswrapper and the official belkin windows xp drivers. You now have working wifi.

Long Answer:

1) Remove the pci wifi card from your computer
2) Install ubuntu 10.10
3) Boot into ubuntu
4) open a terminal and type: ```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
5) This will prompt you for your password, enter it
6) Once inside gedit, simply add at the very bottom the line: ```
blacklist rtl8180
```
7) Then his Ctrl+S or click on Save and close gedit
8 ) Now if you have an alternate internet source that works (e.g: ethernet) follow from here, else jump to 11
9) Open Ubuntu Software Center and search for ```
ndiswrapper
```
10) Now select Windows Wireless Drivers and install it. Skip to 12
11) If you have no internet access. Then:
- from another computer, download: [http://packages.ubuntu.com/maverick/all/ndiswrapper-common]("http://packages.ubuntu.com/maverick/all/ndiswrapper-common") by clicking on All and selecting a mirror.
- from another computer, download: [http://packages.ubuntu.com/maverick/ndiswrapper-utils-1.9]("http://packages.ubuntu.com/maverick/ndiswrapper-utils-1.9") by clicking on your architecture and selecting a mirror.
- from another computer, download: [http://packages.ubuntu.com/maverick/ndisgtk]("http://packages.ubuntu.com/maverick/ndisgtk") by clicking on your architecture and selecting a mirror.
- Now install all 3 in the order you downloaded them, by clicking on them and choosing install.
12) Go to [http://en-us-support.belkin.com/app/answers/detail/a_id/303/~/f5d7000-wireless-g-desktop-card---driver]("http://en-us-support.belkin.com/app/answers/detail/a_id/303/~/f5d7000-wireless-g-desktop-card---driver") and download your cards drivers for Windows. Mine being F5D7000 - Driver - Version 7xxx
13) right click on the downloaded .exe file, and select extract here. There will now be a folder called f5d7000_something in the same directory
14) Go to System > Administration > Windows Wireless Drivers
15) Click on Install New Driver and browse to your extracted folder f5d7000_something > WINXP > *.inf (in my case it is BLKWGDv7.inf)
16) Click Install
17) That's it, you are done. You can click close. Your wifi card now works and ubuntu will not freeze anymore on boot, because of it.

---

### Post by Krytarik on 2011-01-06
Then it didn't work -in your case- to do just the steps from #3 onward, without re-installing Ubuntu with your card removed? If so, do you have a clue why?

---

### Post by didibus on 2011-01-07
Oh, sorry I made this unclear.
Actually you can simply follow step 3 onward, it worked for me. I just wanted to explain the process from the start, because even the liveCD freezes if you have the card in.

---

### Post by didibus on 2011-01-08
Blacklist module driver on boot:

It's also possible not to have to remove your card from the computer. When you are in GRUB, add **rtl8180.blacklist=yes** to the kernel boot arguments, and that will let you boot with the card in. This way you can easily boot the liveCD, install, then on the next restart, add that argument to the kernel again, now you will be logged in to your system, then make sure to edit the blacklist.conf file to permanently blacklist the faulty driver.

---


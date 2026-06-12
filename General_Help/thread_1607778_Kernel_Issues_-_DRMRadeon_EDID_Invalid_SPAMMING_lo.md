---
title: "Kernel Issues - DRM/Radeon EDID Invalid SPAMMING logs"
date: 2010-10-28
forum: General Help
---

### Post by DaninFuchs on 2010-10-28
Before anyone says this has been addressed, I'd like to mention that  I've looked in-depth and can't find an actual -fix- for this issue,  simply workarounds (which cause other things to break, for me.)
 
 Okay so this is a rather convoluted story. Last night I updated my  system, which turned out to be a mistake. At the time, I was running  Karmic/10.04, I forget which kernel. Reboot required. I put it off, but  for some reason I still haven't figured out, my machine locked up.
 
 Whatever. So I reboot, and......black screen. After messing around for  far too long, I manage to get the system to boot via SystemRescueCD -  seriously, look it up, you need it - and I instruct that to boot my  hard-drive-installed Linux since its tools said everything was OK.
 
 From within that, I was able to get my system powered up and in X, but  random things weren't working - kernel modules I didn't have proper  versions of, of course, since it was running the SysRescCD kernel with  my Ubuntu install. I figure I'll update to Maverick, since it's been  released and - in theory - should be stable. Update goes fine, reboot,  and everything works.....sort of. During boot, I saw a few pages of  messages fly by, somewhat akin to this;
 
 ```
[10497.020926] radeon 0000:01:05.0: HDMI Type A-1: EDID block 0 invalid.
 [10497.020936] [drm:radeon_dvi_detect] *ERROR* HDMI Type A-1: probed a monitor but no|invalid EDID
 [10507.192334] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 8
 [10507.192348] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
 [10507.192357] <3>01 00 00 00 00 00 00 00 00 00 03 00 00 00 00 00  ................
 [10507.192363] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.192370] <3>01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.192376] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.192382] <3>00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.192388] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.192394] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.192400] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.192405]
 [10507.243588] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
 [10507.243596] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.243603] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.243609] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.243616] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.243622] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.243628] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.243634] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.243640] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.243645]
 [10507.294774] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
 [10507.294781] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.294788] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.294794] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.294800] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.294806] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.294813] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.294819] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.294825] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.294830]
 [10507.347274] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
 [10507.347282] <3>00 00 00 00 00 00 00 00 00 00 7f 00 00 00 00 00  ................
 [10507.347289] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.347295] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.347301] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.347307] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.347313] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.347319] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 [10507.347326] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
 
```
 
(Sometimes one or two of those sets of 00's will have a different number  in a random location, I assume that's simply a bad read on the EDID  data bus.)

 I should note, this is a laptop, and I have NO external display connected. JUST the build-in LCD panel.
 
 Then X comes up, and I have.....nothing. Well, a Gmail Notifier login  prompt, then nothing. Background image loads, but nothing else..if I  alt-Tab, I see "mutter" (at the time I had NO idea what that was) and a  small two-inch square window border highlighted - no bars, no dock, no  icons or desktop. Alt-F2 won't work to run things, luckily I had Guake  installed so I could F12 myself a terminal.. Blah blah blah, switched  out of the Netbook launcher. Since then, ANY IO (network or drive)  results in 50% IOWAIT load, I've had to write a script to flush my  /var/log/{messages,kern.log,debug,syslog} files or it fills with  literally hundreds of megabytes of messages in **under a day!** and kills my free space at alarming rates.
 
 So, to summarize;
 A) Unity is unusable. The sidebars/top bar flash from time to time when  alt-tabbing, but that's all I get. If I use the 'radeon.modset=0' kernel  parameter, mutter complains about requiring a video device with this or  that on boot.
 B) Literally every five or ten seconds, my console window and several  log files receive between four and twelve lines of crap about EDID  problems (depending on which file)
 C) During normal use, I can EXPECT my touchpad to halt for three to ten  seconds any time I'm trying to do anything, and the keyboard will halt  for a few seconds randomly as well. My screen stops updating during this  period, I abruptly lose network throughput (transferring large files  SUCKS because of this) and in general I'm hating it.
 D) With radeon.modset=0 in linux kernel parameters, my screen will go  black for several seconds, every minute or less. Usually less. Also  causes random applications to complain, mostly those using 'extended'  features of video hardware.
 E) Extremely high IOWAIT times. Xorg is up near 2  hours of CPU time  after being up for only 8 hours, doing very little - Firefox, no  flash/animations. Console windows. Pidgin. Even now, simply typing this  and copying a file; ```
5.4%us,  5.6%sy,  0.0%ni, 10.1%id, 76.2%wa,   0.0%hi,  2.6%si,  0.0%st
```
 
 NONE of these problems existed before that update last night. I don't  remember what kernel I was on, or which kernel it went to, but here's  some random info I think might help; it's 5:15am and I know I'm leaving a  lot out. Let me know what I forgot, I'll add that.
 
 Kernel; Linux 2.6.36-020636-generic #201010210905 SMP Thu Oct 21 09:08:58 UTC 2010 x86_64 GNU/Linux
 OS; Ubuntu 10.10 x64
 Video; 01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
 
 Computer; TOSHIBA; Satellite P305D
 
 `lsmod | grep radeon`
 ```
lsmod | grep rad
 radeon                915834  2 
 ttm                    66976  1 radeon
 drm_kms_helper         34518  1 radeon
 drm                   219952  4 radeon,ttm,drm_kms_helper
 i2c_algo_bit            5870  1 radeon
 
```
 
 `lshw` (Clips of it anyways)
 ```
        *-pci:0
              description: PCI bridge
              product: RS690 PCI to PCI Bridge (Internal gfx)
              vendor: ATI Technologies Inc
              physical id: 1
              bus info: pci@0000:00:01.0
              version: 00
              width: 32 bits
              clock: 66MHz
              capabilities: pci ht normal_decode bus_master cap_list
              resources: ioport:9000(size=4096) memory:f8000000-f81fffff ioport:f0000000(size=134217728)
            *-display
                 description: VGA compatible controller
                 product: RS690M [Radeon X1200 Series]
                 vendor: ATI Technologies Inc
                 physical id: 5
                 bus info: pci@0000:01:05.0
                 version: 00
                 width: 64 bits
                 clock: 33MHz
                 capabilities: pm msi vga_controller bus_master cap_list rom
                 configuration: driver=radeon latency=64
                 resources: irq:18 memory:f0000000-f7ffffff  memory:f8100000-f810ffff ioport:9000(size=256) memory:f8000000-f80fffff
            *-multimedia
                 description: Audio device
                 product: Radeon X1200 Series Audio Controller
                 vendor: ATI Technologies Inc
                 physical id: 5.2
                 bus info: pci@0000:01:05.2
                 version: 00
                 width: 64 bits
                 clock: 33MHz
                 capabilities: pm msi bus_master cap_list
                 configuration: driver=HDA Intel latency=64
                 resources: irq:19 memory:f8110000-f8113fff
 
```
 
 According to Additional Drivers, no proprietary drivers are installed on  this system. I'd attach more files, but it seems they're larger than allowed. I'm not sure where to go from here. Any ideas will be  investigated, and any help will be appreciated. Thank you. (Side note,  I'm on my way to sleep right now. I work in four hours. I'll reply ASAP,  thanks!)

---

### Post by davcr on 2010-10-28
Same problem here, running Ubuntu 10.10 on1 a hp compaq 6820s laptop with no external screen, no DVI connector. Kernel version is 2.6.36 64-bit.

I started having problems when upgraded from 9.10 to 10.04. The boot process started to take ages (about 2 minutes), and after checking the logs, I found the aforementioned tons of spam related to "drm/edid" errors. At that point, it only caused problems during start-up. I upgraded the system to 10.10 hoping a new kernel version would solve the problem, but instead, things got worse. Now the system freezes every 10 seconds for about 5 seconds, making it almost impossible to use it. The display, the mouse cursor and the keyboard are frozen during that interval. Not even the BIOS keyboard buffer works: if you keep on typing when the system gets stuck, most characters are never read by the system.

These periods of inactivity occur simultaneously to the dumping of several blocks of "drm/edid" error followed by a bunch of double zeros to the kernel log file, so my impression is that both things are related. 

Oct 28 07:44:58 mulobomba kernel: [57898.503883] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
Oct 28 07:44:58 mulobomba kernel: [57898.503890] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:58 mulobomba kernel: [57898.503893] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:58 mulobomba kernel: [57898.503896] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:58 mulobomba kernel: [57898.503898] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:58 mulobomba kernel: [57898.503901] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:58 mulobomba kernel: [57898.503903] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:58 mulobomba kernel: [57898.503906] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:58 mulobomba kernel: [57898.503909] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:58 mulobomba kernel: [57898.503911] 
Oct 28 07:44:59 mulobomba kernel: [57899.888241] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
Oct 28 07:44:59 mulobomba kernel: [57899.888247] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:59 mulobomba kernel: [57899.888250] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:59 mulobomba kernel: [57899.888253] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:59 mulobomba kernel: [57899.888256] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:59 mulobomba kernel: [57899.888258] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:59 mulobomba kernel: [57899.888261] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:59 mulobomba kernel: [57899.888264] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Oct 28 07:44:59 mulobomba kernel: [57899.888266] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................

(etc.)

---

### Post by DaninFuchs on 2010-10-31
...yup, still having the same problem... Anyone even come close to touching this?

---

### Post by markus111 on 2010-11-07
Hello,

same problem in my Compaq 6820s :(. About every 10 seconds Ubuntu freezes for about 5 seconds, which makes it inpossible to use it. Hope anyone has got a solution for this.
In a virtual machine (VirtualBox) it runs perfect.

markus111

---

### Post by DaninFuchs on 2010-11-07
And for every person who posts here, there's gotta be at least fifty people who have the issue and haven't found this thread. Unfortunately, I haven't been able to find a fix, and it seems nobody else is willing/able to help.

The problem is kernel-side, their new (annoyingly bad) EDID handling seems to think - at least in my case - that I have something plugged in via HDMI when it's not.

Instead of disabling the HDMI after X failures, or ignoring the input that returns garbage every time it polls, it's decided it's going to hammer it until it answers back "properly" and eventually it segfaults some kernel code rather than  intelligently managing its errors. It spams your logs with FAR too much junk, there's no way to disable it.

YES, I know, radeon.modeset=0 in the kernel parameters line in Grub. Guess what though? When I do that, something randomly segfaults Xorg on init. Worth it? No. Because then I have NO Xorg functionality, instead of annoying, stuttery, halting, occasionally screen-mode-resetting functionality. It's a trade-off. And it's rapidly becoming a trade-off I'm not willing to deal with.

One of the Ubuntu bug reports that I found - which I can't find again, and don't feel like digging out - had a kernel patch that changed the "errors" from EDID invalid checksumming, to "warnings"....that's a half-assed fix. It's meant to make people (who can't get it to run at all) get some functionality back there. I'm betting it still hesitates every time it tries to scan EDID on everything. I'm betting it still causes tons of error log flooding. And I'm definitely going to bet that it still randomly resets my screen.

---

### Post by LiquidMeson on 2010-11-13
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/547147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/547147)

the grub edit someone proposed in the comments is nice temporary fix

---

### Post by DaninFuchs on 2010-11-15
> **LiquidMeson said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/547147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/547147)

the grub edit someone proposed in the comments is nice temporary fix
Oh sure it is. Except that, as mentioned, when I have modeset turned off, Xorg segfaults. Granted I turned it off directly in the radeon driver instead of simply specifying 'nomodeset' - but it still segfaults. And yes, I did try that method, since I haven't seen it specifically before.

---

### Post by rdratlos on 2010-11-16
@DaninFuchs

From the information you have posted I can see that your laptop uses ATI's RS690M [Radeon X1200 Series] integrated graphics chipset. My PC is based on the Asus M2A-VM HDMI board, which uses the same chipset. After day's of investigation, I found a solution for the invalid EDID spamming problem you mentioned. At least for my PC it works fine now using Ubuntu kernel 2.6.35-22-generic. The problem relates to KSM using the drm.ko and radeon.ko kernel driver modules, which are not failure tolerant against hardware problems of this chipset and periodically spam the logs with their error notifications. 

To solve it, first check the i2c interface of the display data channel (DDC). For this you need the package i2c-tools:
```
sudo aptitude install i2c-tools
``````
rdratlos@Mark-Aurel:~$ sudo i2cdetect -l
i2c-0    smbus         SMBus PIIX4 adapter at 0b00         SMBus adapter
i2c-1    i2c           Radeon i2c bit bus VGA              I2C adapter
i2c-2    i2c           Radeon i2c bit bus HDMI             I2C adapter
i2c-3    i2c           Radeon i2c bit bus DVI              I2C adapter
rdratlos@Mark-Aurel:~$ sudo i2cdetect 1
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-1.
I will probe address range 0x03-0x77.
Continue? [Y/n] y
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --                         
rdratlos@Mark-Aurel:~$ sudo i2cdetect 2
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-2.
I will probe address range 0x03-0x77.
Continue? [Y/n] y   
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          03 04 05 06 07 08 09 0a 0b 0c 0d 0e 0f 
10: 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 
20: 20 21 22 23 24 25 26 27 28 29 2a 2b 2c 2d 2e 2f 
30: 30 31 32 33 34 35 36 37 38 39 3a 3b 3c 3d 3e 3f 
40: 40 41 42 43 44 45 46 47 48 49 4a 4b 4c 4d 4e 4f 
50: 50 51 52 53 54 55 56 57 58 59 5a 5b 5c 5d 5e 5f 
60: 60 61 62 63 64 65 66 67 68 69 6a 6b 6c 6d 6e 6f 
70: 70 71 72 73 74 75 76 77                         
rdratlos@Mark-Aurel:~$ sudo i2cdetect 3
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-3.
I will probe address range 0x03-0x77.
Continue? [Y/n] y
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: 50 -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --                         

```In my case, a Samsung monitor is connected to the DVI-I interface. HDMI has been disabled in BIOS settings. The extended display identification data (EDID) from the monitor is accessed on port 0x50. From the i2cdump you see, that the graphics chipset correctly reports the required DDC to be available for the DVI interface but also for the disabled HDMI interface. The drm kernel module now tries to get the EDID data, which cannot be loaded, as there's no monitor connected. 

Before you start fixing your problem double-check the availability of a valid EDID by using the tool read-edid-i2c. You will find the source code and further instructions [here]("http://www.polypux.org/projects/read-edid/"). In order to use it, you also need to install the package read-edit:
```
sudo aptitude install read-edid
```If the following command succeeds, you can start to fix the kernel problem:
```
sudo /usr/src/kernel/read-edid-i2c/read-edid-i2c | parse-edid
```In order ro fix the problem you need to correct and rebuild the kernel driver module radeon.ko. Compiling kernel modules requires further Ubuntu packages (fakeroot, build-essentials). More information is available on the [Ubuntu wiki]("http://wiki.ubuntuusers.de/Kernel/Kompilierung").

Follow the steps below (for kernel version 2.6.35-22):
1. Download kernel source (same kernel version as currently used)
    ```
sudo apt-get source linux-image-2.6.35-22-generic
```2. Patch the kernel using the attached patch (save to drm_radeon.diff to the location where apt-get downloaded the kernel source tarball)
    ```
sudo patch -p0 < drm_radeon.diff
```3. Enter source directory
```
    cd linux-2.6.35

```4. Get kernel build configuration that has been used to build the now running kernel
```
    sudo cp /boot/config-2.6.35-22-generic .config
    sudo cp /usr/src/linux-headers-2.6.35-22-generic/Module.symvers .

```5. Configure kernel build
```
    sudo make oldconfig
    sudo make prepare
    sudo make modules SUBDIRS=scripts

```6. Compile the module sources
```
    sudo make modules SUBDIRS=drivers/gpu/drm/radeon

```7. Copy the updated module into the kernel library
```
    sudo cp drivers/gpu/drm/radeon/radeon.ko /lib/modules/2.6.35-22-generic/kernel/drivers/gpu/drm/radeon/

```8. Restart your system and test the updated module

The spamming of invalid EDID notifications should have stopped.

```
dmesg
```should show EDID availability for each of your connectors and an EDID dump for the buggy connector. /var/log/syslog should not have any EDID spamming.

I saw that there will be a huge amount of changes and updates to the two kernel drivers in the 2.6.36 kernel. From a brief check of the source code, I doubt that they will fix our problem. The attached patch does only work for kernel version 2.6.35-22. For any kernel updates the patch has also to be updated and the radeon.ko module must be built again.

---

### Post by DaninFuchs on 2010-11-16
> **rdratlos said:**
> @DaninFuchs

From the information you have posted I can see that your laptop uses ATI's RS690M [Radeon X1200 Series] integrated graphics chipset. My PC is based on the Asus M2A-VM HDMI board, which uses the same chipset. After day's of investigation, I found a solution for the invalid EDID spamming problem you mentioned. At least for my PC it works fine now using Ubuntu kernel 2.6.35-22-generic. The problem relates to KSM using the drm.ko and radeon.ko kernel driver modules, which are not failure tolerant against hardware problems of this chipset and periodically spam the logs with their error notifications. 

To solve it, first check the i2c interface of the display data channel (DDC). For this you need the package i2c-tools:
```
sudo aptitude install i2c-tools
``````
rdratlos@Mark-Aurel:~$ sudo i2cdetect -l
i2c-0    smbus         SMBus PIIX4 adapter at 0b00         SMBus adapter
i2c-1    i2c           Radeon i2c bit bus VGA              I2C adapter
i2c-2    i2c           Radeon i2c bit bus HDMI             I2C adapter
i2c-3    i2c           Radeon i2c bit bus DVI              I2C adapter
rdratlos@Mark-Aurel:~$ sudo i2cdetect 1
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-1.
I will probe address range 0x03-0x77.
Continue? [Y/n] y
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --                         
rdratlos@Mark-Aurel:~$ sudo i2cdetect 2
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-2.
I will probe address range 0x03-0x77.
Continue? [Y/n] y   
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          03 04 05 06 07 08 09 0a 0b 0c 0d 0e 0f 
10: 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 
20: 20 21 22 23 24 25 26 27 28 29 2a 2b 2c 2d 2e 2f 
30: 30 31 32 33 34 35 36 37 38 39 3a 3b 3c 3d 3e 3f 
40: 40 41 42 43 44 45 46 47 48 49 4a 4b 4c 4d 4e 4f 
50: 50 51 52 53 54 55 56 57 58 59 5a 5b 5c 5d 5e 5f 
60: 60 61 62 63 64 65 66 67 68 69 6a 6b 6c 6d 6e 6f 
70: 70 71 72 73 74 75 76 77                         
rdratlos@Mark-Aurel:~$ sudo i2cdetect 3
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-3.
I will probe address range 0x03-0x77.
Continue? [Y/n] y
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: 50 -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --                         

```In my case, a Samsung monitor is connected to the DVI-I interface. HDMI has been disabled in BIOS settings. The extended display identification data (EDID) from the monitor is accessed on port 0x50. From the i2cdump you see, that the graphics chipset correctly reports the required DDC to be available for the DVI interface but also for the disabled HDMI interface. The drm kernel module now tries to get the EDID data, which cannot be loaded, as there's no monitor connected. 

Before you start fixing your problem double-check the availability of a valid EDID by using the tool read-edid-i2c. You will find the source code and further instructions [here]("http://www.polypux.org/projects/read-edid/"). In order to use it, you also need to install the package read-edit:
```
sudo aptitude install read-edid
```If the following command succeeds, you can start to fix the kernel problem:
```
sudo /usr/src/kernel/read-edid-i2c/read-edid-i2c | parse-edid
```In order ro fix the problem you need to correct and rebuild the kernel driver module radeon.ko. Compiling kernel modules requires further Ubuntu packages (fakeroot, build-essentials). More information is available on the [Ubuntu wiki]("http://wiki.ubuntuusers.de/Kernel/Kompilierung").

Follow the steps below (for kernel version 2.6.35-22):
1. Download kernel source (same kernel version as currently used)
    ```
sudo apt-get source linux-image-2.6.35-22-generic
```2. Patch the kernel using the attached patch (save to drm_radeon.diff to the location where apt-get downloaded the kernel source tarball)
    ```
sudo patch -p0 < drm_radeon.diff
```3. Enter source directory
```
    cd linux-2.6.35

```4. Get kernel build configuration that has been used to build the now running kernel
```
    sudo cp /boot/config-2.6.35-22-generic .config
    sudo cp /usr/src/linux-headers-2.6.35-22-generic/Module.symvers .

```5. Configure kernel build
```
    sudo make oldconfig
    sudo make prepare
    sudo make modules SUBDIRS=scripts

```6. Compile the module sources
```
    sudo make modules SUBDIRS=drivers/gpu/drm/radeon

```7. Copy the updated module into the kernel library
```
    sudo cp drivers/gpu/drm/radeon/radeon.ko /lib/modules/2.6.35-22-generic/kernel/drivers/gpu/drm/radeon/

```8. Restart your system and test the updated module

The spamming of invalid EDID notifications should have stopped.

```
dmesg
```should show EDID availability for each of your connectors and an EDID dump for the buggy connector. /var/log/syslog should not have any EDID spamming.

I saw that there will be a huge amount of changes and updates to the two kernel drivers in the 2.6.36 kernel. From a brief check of the source code, I doubt that they will fix our problem. The attached patch does only work for kernel version 2.6.35-22. For any kernel updates the patch has also to be updated and the radeon.ko module must be built again.
Fantastic! Finally a reply from someone who has some clue what I'm going through. Thank you so much for your time, however - I ran into a block real early. Doing the I2C checking resulted in discovering that it's not working. I installed a non-Ubuntu kernel a while ago; Linux Gemini 2.6.36-020636rc8-generic #201010150908 SMP

At this point, i2c reported nothing when checked. (i2cdetect -l)  I manually inserted the I2C modules I could find from the /lib/modules tree, to no avail. When run, it now finds my SMBus PIIX4 adapter, and nothing further.

I tried to move ahead to see if the read-edid-i2c may help, but that failed as I don't have the full kernel source installed - at least, I assume this is why. I was hoping to not have to recompile a kernel to get this working, as it's something that should just work....but clearly that's not an option, haha. My concern there is, I suppose, as simple as, it's been years since I've scratch-built a kernel, so I'm feeling stunningly lazy about hand-configuring it. I assume it'd be easy enough to scrape the config out of /proc (if the Ubuntu devs were so gracious as to include it, which I'll assume they were) but from there, I'd need to ensure the whole shebang is configured to "typical" Ubuntu spec, so I don't have to beat Grub into submission yet again...

However, I assume I'm getting ahead of myself - what's your recommendation at this point? Go back to a stocker Ubuntu kernel? Load some I2C module I didn't consider/find? Thanks again for your time.

---

### Post by rdratlos on 2010-11-17
> **DaninFuchs said:**
> Fantastic! Finally a reply from someone who has some clue what I'm going through. Thank you so much for your time, however - I ran into a block real early. Doing the I2C checking resulted in discovering that it's not working. I installed a non-Ubuntu kernel a while ago; Linux Gemini 2.6.36-020636rc8-generic #201010150908 SMP

At this point, i2c reported nothing when checked. (i2cdetect -l)  I manually inserted the I2C modules I could find from the /lib/modules tree, to no avail. When run, it now finds my SMBus PIIX4 adapter, and nothing further.


You're right. Just installing i2c-tools is not sufficient. I should have been more precise. We need a chain to get user-based access to the i2c bus. In case of my Asus board it worked this way:
1. Install the lm-sensors package and let it probe your HW
```
sudo sensors-detect
```One of the steps of sensors-detect is to probe the I2C/SMBus adapters. You should see your graphics adapters in the output. For this purpose sensors-detect loads the i2c-dev kernel module and unloads it after probing. At least on my system, this module was not part of the default kernel module suit. If this is true also for your system, load the i2c-dev module again:
```
sudo modprobe i2c-dev
```With lsmod you should see now following kernel modules loaded:
```
rdratlos@Mark-Aurel:~$ lsmod |grep i2c
i2c_dev                 6310  0 
i2c_piix4              10047  0 
i2c_algo_bit            6208  1 radeon

```If this is true, just edit /etc/modules and add following two lines to get i2c-dev also loaded at boot time:
```
# Get access to monitor EDID EEPROM via i2c
i2c_dev

```Now you should have permant user access to the i2c adapters.

---

### Post by DaninFuchs on 2010-11-17
*Sorry, just got home from work. Okay, here goes.

Well, it did detect the SMBus adapter for the PIIX4 device. I had everything set up properly, and had already done sensors_detect. However, your reply lead me to a discovery - the i2c_algo_bit module was not being used by the radeon module.

...so I tried to modprobe the radeon module, and it barked at me. Turns out, there's an invalid kernel parameter being passed - one of the ones I added to grub.cfg in a desperate attempt to "just try anything that anyone says might help" after not receiving any answers here for so long. I removed that, rebooted, and got back the 'pretty' that I forgot I was even missing (some of the accelerated effects and such) - and now i2cdetect returns the device itself. Trying the rest now, will update when I have a result one way or the other. May be a little bit because I'll be multitasking somewhat. Thanks for your attention.

Also, as a side note, when I'm doing tasks like this, rather than spam 'sudo xxxxx' I tend to just drop to superuser and do it, entering my 19-character password because I strayed from the laptop for ten minutes just drives me up the wall. I'm a fairly experienced Linux user, been through a trillion problems and fixes and kernel builds and what-have-you, so if you feel the urge to be less newbie-friendly I won't hold it against you, haha. On the same note, I also feel the need to say thank you, on behalf of the others out there who may be reading this in the future - your detailed, clearly-explained, well-backed, step-by-step information will no doubt prove to be helpful to many. I can't tell you how often I've read posts that say "just do this 2 fix ur prob" and just barebones the heck out of their steps. Hand someone a list of commands and you fix their problem; explain to someone why they're running the commands, and you teach them how.

---

### Post by Stephen_m64 on 2010-12-28
i Just built a small server:

Athlon X2 4850B
ECS A740GM-M Motherboard (integrated radeon graphics)

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100
02:00.0 Ethernet controller: Atheros Communications L2 Fast Ethernet (rev a0)

```

Installed 10.10 amd64 server and immediately started getting this issue.

for now i have just sidestepped the problem by blacklisting the radeon module but a real fix for it would be appreciated.

---

### Post by ridethestream on 2011-01-09
Ubuntu 10.10 

I applied the patch and rebuilt the module but nothing has changed.
Learning about how to build kernel at the moment.

I have the same EDID non-stop kernel debug messages. 
EDID checksum,
Raw EDID
DVI-D-1

root@Ubuntu-box:~# i2cdetect 3
 WARNING! This program can confuse your I2C bus, cause data loss and worse!
 I will probe file /dev/i2c-3.
 I will probe address range 0x03-0x77.
 Continue? [Y/n] 
      0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
 00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
 10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
 20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
 30: -- -- -- -- -- -- -- 37 -- -- 3a -- -- -- -- -- 
 40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
 50: 50 -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
 60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
 70: -- -- -- -- -- -- -- --

---

### Post by DaninFuchs on 2011-01-09
> **ridethestream said:**
> Ubuntu 10.10 

I applied the patch and rebuilt the module but nothing has changed.
Learning about how to build kernel at the moment.

I have the same EDID non-stop kernel debug messages. 
EDID checksum,
Raw EDID
DVI-D-1

root@Ubuntu-box:~# i2cdetect 3
 WARNING! This program can confuse your I2C bus, cause data loss and worse!
 I will probe file /dev/i2c-3.
 I will probe address range 0x03-0x77.
 Continue? [Y/n] 
      0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
 00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
 10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
 20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
 30: -- -- -- -- -- -- -- 37 -- -- 3a -- -- -- -- -- 
 40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
 50: 50 -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
 60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
 70: -- -- -- -- -- -- -- --

Alright - you rebuilt the module, did you install it into the kernel modules directory? /lib/<kernel-version> path - if not, wouldn't have any effect whatsoever.

I didn't have any luck with it either, never got around to return-posting - my main issue is that it wants to believe there's a monitor there, but keeps getting "incorrect information" from "it", which occasionally causes problems in the kernel. The log spamming is annoying, but I wrote a cron job to periodically empty the logs. Sucks for troubleshooting, especially if I need to see what a USB device is doing wrong. Dmesg is useless, because of this, and I didn't feel like loading a few megabytes of logs to see what happened.

I haven't bothered with it since my last post, but I'm growing more tempted every day to move back to Windows, especially with all the things that keep getting broken in 'updates'. My touchscreen used to work fine, but the Ubuntu devs changed their handling of xorg.conf and input modules, now I can't figure out how to fix that. Don't update your Alsa, you'll lose audio - they ditched OSS completely, which breaks Alsa unless it's compiled without OSS support. I'm growing weary of it all.

---

### Post by ridethestream on 2011-01-10
I just figured out how to install new kernel on Ubuntu. 

I tested 2.6.37 kernel from kernel.org. It hasn't solved the issue yet. There are less than five codes that generate flooding kernel debug messages in Radeaon drive sources. It starts DRM_ macro functions and one or two prinktk(). Running 'grep -r -n DRM .../gpu/drm and ...gpu/drm/radeon will show you location.  I'm going to do this.

I noticed Ubuntu kernel has its unique kernel options and patches. When I boot on 2.6.37 kernel, I get a lot of system wide error message. So, I'm running 2.6.35 on Ubuntu kernel. Ubuntu 2.6.35-24 kernel source is so buggy, Radeon driver source  contains many 'error, incompatible types' compile error. How ever built  the binary kernel and modules, it makes me wonder. 

Except nice GUI, Ubuntu system is loosing my faith.  I don't bother much. I had been out of Linux for few years. And, I gotta catch up basic stuff. Once I pick up again, I'll probably build my own Linux box. My first Linux box was Slackware 0.xx on 386 IBM machine on 1991. 

Thanks for response.

---

### Post by DaninFuchs on 2011-01-10
> **ridethestream said:**
> I just figured out how to install new kernel on Ubuntu. 

I tested 2.6.37 kernel from kernel.org. It hasn't solved the issue yet. There are less than five codes that generate flooding kernel debug messages in Radeaon drive sources. It starts DRM_ macro functions and one or two prinktk(). Running 'grep -r -n DRM .../gpu/drm and ...gpu/drm/radeon will show you location.  I'm going to do this.

I'm using a 2.6.37 kernel presently, due to some required fixes. I think it was an Ubuntu source, but I forget now. Problem is, it has non-backward-compatible changes to some things I use so I'm a bit stuck. I may look into rebuilding it from source, and stripping the debug and EDID junk out myself..if I get the time. I'm also considering AriOS, an Ubuntu derivative. Heard good things, but always skeptical - usually all derivs do is prepackage a few things and patch bootscreens, heh.

> I noticed Ubuntu kernel has its unique kernel options and patches. When I boot on 2.6.37 kernel, I get a lot of system wide error message. So, I'm running 2.6.35 on Ubuntu kernel. Ubuntu 2.6.35-24 kernel source is so buggy, Radeon driver source  contains many 'error, incompatible types' compile error. How ever built  the binary kernel and modules, it makes me wonder. 

Yeah, they actually do a fair amount of tweaking and fixing, which is awesome, but I hat how they tend to enforce changes to 'update' from 'deprecated' methods.. Tried and true? Yeah, but it's old, this way is better...nevermind that it isn't done yet, and doesn't work for some people, and fixes are either ugly or unknown...admittedly, this EDID crap is the core kernel team's fault not Ubuntu devs, but still.

> Except nice GUI, Ubuntu system is loosing my faith.  I don't bother much. I had been out of Linux for few years. And, I gotta catch up basic stuff. Once I pick up again, I'll probably build my own Linux box. My first Linux box was Slackware 0.xx on 386 IBM machine on 1991. 

I agree. I use Linux because it's faster and better with resources than Windows, and tends to let me satisfy my tweak and tune impulses, but damn...lately every new release brings as much stress and pain as it does new features..and the greatest part is I never have the 'mainstream' issues, it's always weird crap nobody else deals with. If you want to DIY, may look into Gentoo. Good setup, easier than source but a whole different experience. They do some good kernel work too. Wonder if they've fixed the EDID issues... Let me know if you do find anything though.

---

### Post by ridethestream on 2011-01-13
There are three options to solve this issue.

[LIST]
[*]Replace the graphic card
[*][Apply ATI driver ]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English")
[*]Get kernel source and patch the raedeon module source.
[/LIST]
I'm almost finished to block the EDID error message on source level.

I found a script file yesterday while I was patching ATI driver for X Window. It's called install-fglrx-debian.sh. [http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)

It downloads the right ATI driver for your graphic card , apply patches on the driver source, and install it.  It did work smoothly. Unluckily, ATI driver doesn't support my graphic card which is so retard. I'm running ATI Catalyst suit on Windows XP. :(  It seems the ATI driver replace radeon.ko file.

It did not work out for me but I'm almost at the end of troubleshooting.
I only get one EDID message once in a while, the radeon, drm modules I patched runs fine.  

What I experienced though was patched radeon module conflictes against X Window Radeonhd driver.  I needed to remove and install Radeon driver that supports my graphic card.

IMHO, anyone who has good knowledge of Linux kernel would solve this issue effectively. I'm far from that level.  It's funny to see how the EDID related source codes work. The developers don't have enough information about data bits about EDID and hardware spec so they just log any EDID related data out of their head to kernel.

---

### Post by DaninFuchs on 2011-01-17
> **ridethestream said:**
> There are three options to solve this issue.

[LIST]
[*]Replace the graphic card
[*][Apply ATI driver ]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English")
[*]Get kernel source and patch the raedeon module source.
[/LIST]
All well and good, but..
A) Graphics card is built into the laptop.
B) ATI driver doesn't work with my card anymore, because ATI - in their attempts to reap profits, be lazy, and screw people who're stuck with their hardware - removed support for "old" cards in the new driver.
C) Could do, but it's more of a core KMS/Radeon misbehavior issue.

Also, you'd have to get the Ubuntu source, being that they've added all manner of extras to the kernel, and it's just too much effort for me to learn how the stupid thing is supposed to work. I just wish the kernel team responsible for breaking the thing by enabling EDID secondary-packet retreiving and too stupid to make it NOTICE the errors, would either be forced to fix it - at gun point if required - or just publicly humiliated. (Yeah, I'm in a mood. I'm tired of this crap.)  

I mean seriously. Probing every five seconds, that's pretty stupid. Four times in a row? Come on. Dumping 11 lines of code to the CONSOLE, when the only people who -should- see those messages are other kernel devs, instead of..I dunno..putting in an "Enable debug output" location? Retarded. Coding it in such a way that it causes a few dozen milliseconds of hesitation each time? Fired. Coding it in such a way that it causes a stack dump periodically? Not making a flag that says "Crap, this didn't work the last three thousand times, maybe I shouldn't check it again every five seconds until the user screams in rage"? Not allowing users a way to disable probing of specific outputs, since the smart ones will think of that first? I think sometimes these guys aren't as smart as they seem.

> I'm almost finished to block the EDID error message on source level.

I found a script file yesterday while I was patching ATI driver for X Window. It's called install-fglrx-debian.sh. [http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)

It downloads the right ATI driver for your graphic card , apply patches on the driver source, and install it.  It did work smoothly. Unluckily, ATI driver doesn't support my graphic card which is so retard. I'm running ATI Catalyst suit on Windows XP. :(  It seems the ATI driver replace radeon.ko file.


The old ATI driver doesn't support the new Xorg. The new ATI driver doesn't support "new" cards. Go ATI.

> It did not work out for me but I'm almost at the end of troubleshooting.
I only get one EDID message once in a while, the radeon, drm modules I patched runs fine.  

What I experienced though was patched radeon module conflictes against X Window Radeonhd driver.  I needed to remove and install Radeon driver that supports my graphic card.

RadeonHD doesn't work as well with my (most) "card"/chip/whatever. It also refuses to run at all for me, blows up on init. Huzzah. However, "RadeonHD" is an Xorg server, not a kernel module, so it wouldn't fix the DRM issues.

> IMHO, anyone who has good knowledge of Linux kernel would solve this issue effectively. I'm far from that level.  It's funny to see how the EDID related source codes work. The developers don't have enough information about data bits about EDID and hardware spec so they just log any EDID related data out of their head to kernel.

Actually, the developers have enough information about all of it. The logged messages from the kernel are caused by incorrect data - AKA a chip reporting it has four outputs, and only having two or three, thus causing it to try to read EDID data from a bus that's not connected, getting static, latent, or just outright corrupted return values, typically due to having an unconnected enpoint and capturing EMI from other hardware as "data". The problem is that they didn't code something that noticed if there was an error, and stopped checking unless asked to check again...or something to disable repeat probing..or something to disable extra outputs..or something to disable the scanning of the secondary capabilities packet..etc etc etc.. Removing the logging messages won't fix the problem. It'll still do everything, may or may not still cause hesitations and stuttering, may or may not cause stack dumps, etc. What needs to be done is fixing the scanning subroutines. I don't know enough about persistant kernel pointers/variables/stacks (etc) to add that sort of thing in, and anything I kludge in would likely be invalidated and require patching in a week when a new revision that still doesn't fix the problem is out, so I'm just going to not touch it.

---

### Post by ridethestream on 2011-01-22
Debian Lenny kernel-2.6.32 solved the issue which I checked out.
It only checks EDID once during the boot. It does not spam kernel messages all the time any more. ;)

Some graphic chips require firmware installation too. I just found out few days ago.
I'm not sure Ubuntu provides it as a package. 

Since I installed Lenny Kernel-2.6.32, and installed firmware, the kernel driver of graphic card run great.

---

### Post by turbo9 on 2011-01-22
I just had this problem (again) and blamed my ATI card. This was with Ubuntu 10.10 running on bare hardware.

It turns out that Ubuntu could not get the right video resolution from my monitor. I see a number of these messages in dmesg


[ 12.905074] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 63
[ 12.905125] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[ 12.905166] <3>40 ff ff ff ff ff ff ff 22 64 b3 06 01 08 00 00 @......."d......
[ 12.905170] <3>2e 0f 01 03 0a 22 1b 78 ea fd 59 a5 53 4a 9d 24 .....".x..Y.SJ.$
[ 12.905173] <3>14 4f 56 bf ef 80 81 80 31 0a 31 ca 01 01 01 01 .OV.....1.1.....
[ 12.905176] <3>01 01 01 01 01 01 30 2a 00 98 51 00 2a 40 30 70 ......0*..Q.*@0p
[ 12.905179] <3>13 00 52 0e 11 00 00 1e 00 00 00 fd 00 38 4b 1e ..R..........8K.
[ 12.905182] <3>50 0e 00 0a 20 20 20 20 20 20 00 00 00 ff 00 35 P... .....5
[ 12.905185] <3>34 36 44 44 31 4b 43 41 32 30 34 39 00 00 00 fc 46DD1KCA2049....
[ 12.905188] <3>00 48 61 6e 6e 53 74 61 72 20 55 31 37 31 00 80 .HannStar U171..

Now, this worked in Ubuntu 10.04, but didn't in 10.10. Then, it magically started working in 10.10 for a few weeks and then the problem came back.

Here is how I fixed it:

You don't need to be root to do this.

Check to see if the video mode exists. 

xrandr

If the one we want is missing, we need to add it. 
Get the mode line from the desired resolution:

cvt 1280 1024	

which barfs out something like:

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

Grab the modeline from the second line of output and add it to the known modes:

xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

Things might shimmy a bit, which you might interpret as a good sign.

Associate this mode with the appropriate video output

xrandr --addmode VGA-0 1280x1024_60.00

Then use your normal video resolution gui to set it and then make it the default.

This setting does not survive a reboot. You get a bunch of "could not set monitor resolution" messages.
The default setting survives the restart, but the system does not know the mode exists (same problem as before).
So, write a script with the steps above and execute it once you login (put a call to it on the panel). 

xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA-0 1280x1024_60.00

Things should shimmy and then go to the resolution you set as default before.

This is not a permanent fix - it is a hack, but I can live with it (rather than buying a new monitor).

---

### Post by Escoba on 2011-01-26
Having this same problem after installing 11.04 Natty (worst error in my life) on my old Pressario 2100, can't find a solution yet, but I think i'll try to go back to 10.04, will bump with results.

---

### Post by JoeFriday49 on 2011-02-11
I'm having the same sort of problems here with 10.10

Will going to 10.4 cure it?

My Post: [http://ubuntuforums.org/showthread.php?t=1685378](http://ubuntuforums.org/showthread.php?t=1685378)

---

### Post by herton on 2011-02-25
> **rdratlos said:**
> @DaninFuchs

From the information you have posted I can see that your laptop uses ATI's RS690M [Radeon X1200 Series] integrated graphics chipset. My PC is based on the Asus M2A-VM HDMI board, which uses the same chipset. After day's of investigation, I found a solution for the invalid EDID spamming problem you mentioned. At least for my PC it works fine now using Ubuntu kernel 2.6.35-22-generic. The problem relates to KSM using the drm.ko and radeon.ko kernel driver modules, which are not failure tolerant against hardware problems of this chipset and periodically spam the logs with their error notifications. 

...


@rdratlos -- can you raise and submit the issue upstream? Please report the problem sending an email with the description to [email]dri-devel@lists.freedesktop.org[/email] mailing list and perhaps with CC to [email]linux-kernel@vger.kernel.org[/email], adding your patch also for comments.

---

### Post by DaninFuchs on 2011-02-25
> **herton said:**
> @rdratlos -- can you raise and submit the issue upstream? Please report the problem sending an email with the description to [email]dri-devel@lists.freedesktop.org[/email] mailing list and perhaps with CC to [email]linux-kernel@vger.kernel.org[/email], adding your patch also for comments.

His fix was for one kernel version only, and did not fix all of the problem, just most of the evidence. That patch is honestly fairly elementary, anf any kernel dev (ANY one of them, wether they do Filesystem, spinlock debugging, protocol or ANYTHING ELSE) could fix this problem, it's SUCH a simple fix. Just disable 'extended' EDID packet parsing for a port when it comes back invalid several times. Make it re-enable the input after a replug. I've been too lazy to do it myself as of yet, but I'm getting closer to being that sick of it. I've simply shelved that laptop and moved to one with half the power and a smaller screen, just so I don't have to deal with it.

 Also, notes:

Yes, rolling back to 10.04 will fix the issue, so long as you don't step into 10.10's kernels, or anything newer than what ir ships with.

To the commenter with the 'xrandr/video mode' "fix" - if that solved your problem, you're having a different one. My (our as in most of these posts) problem is that the video card is incorrectly reporting enabled outputs that are not electrically/phisically connected, not anything to do with what mode it choses. My specific system is a laptop - it uses LVDS comms to the screen, IE the video mode is returned by the T-Con (LCD Control board), hardcoded into its firmware as its native resolution. KMS sets the mode based upon what it gets from EDID, thus CREATING the mode. Therefore, the mode exists. Your 'temporary fix' is entirely likely due to the fact that it seems tempermental. I recently upgraded my kernel to the newest 2.6.37 and .38 kernels released for Ubuntu, and thought it was fixed each time, only to find that it malfunctioned still - simply took longer the first time.

Also, a note regarding kernels. Neither the 2.6.37 or .38 versions (.37.1, or .38....something, will check later if I remember) fix the issue. In fact, now sometimes my screen goes 'scrambled' periodically, and sometimes still does the CPU core Xorg takeover bit. It does it less often, but has two problems instead, one far more jarring than the other. UGH!

I know they are aware of the issue, it's been brought to their attention. Sadly they're ignoring the 'small percentage of users affected' for their other projects. Thanks, you're awesome..

---

### Post by herton on 2011-02-25
> **DaninFuchs said:**
> His fix was for one kernel version only, and did not fix all of the problem, just most of the evidence. That patch is honestly fairly elementary, anf any kernel dev (ANY one of them, wether they do Filesystem, spinlock debugging, protocol or ANYTHING ELSE) could fix this problem, it's SUCH a simple fix. Just disable 'extended' EDID packet parsing for a port when it comes back invalid several times. Make it re-enable the input after a replug. I've been too lazy to do it myself as of yet, but I'm getting closer to being that sick of it. I've simply shelved that laptop and moved to one with half the power and a smaller screen, just so I don't have to deal with it.

Sure, the problem is that the kernel developers which takes care of this code should be aware of the problem so that they can see and discuss it, not always they track down forums. The proper way to make them aware is reporting the problem on the mailing lists I cited, giving all details and the patch, so everyone can discuss and reach a solution, and in the end a fix could finally be commited in main kernel, avoiding you guys to having to keep a hack or workaround.

 > **DaninFuchs said:**
> 
I know they are aware of the issue, it's been brought to their attention. Sadly they're ignoring the 'small percentage of users affected' for their other projects. Thanks, you're awesome..

Ah, was this already reported then (bugzilla.kernel.org or bugzilla.freedesktop.org, or the mailing lists)?

---

### Post by zidarsk8 on 2011-04-04
Hello,

I'm too much of a "noob" to understand most of these posts, I've read them all, and I haven't gotten anywhere with the problem. So this post is just bumping the thread and telling everyone that it would be nice if someone could fix this problem.

It's really annoying having the whole system freeze every 5 seconds for a few seconds, and I was hoping that with the new releases the bug would get fixed. Sadly with every ubuntu release since 9.04 I have more and more problems with my hardware, and from 10.10 on, nothing works.

PS: does anyone know what is the status of the bug, has it been reported, is anyone working on it, or should we all just buy different laptops (sarcasm).

---

### Post by rdratlos on 2011-06-21
> **herton said:**
> @rdratlos -- can you raise and submit the issue upstream? Please report the problem sending an email with the description to [EMAIL="dri-devel@lists.freedesktop.org"]dri-devel@lists.freedesktop.org[/EMAIL] mailing list and perhaps with CC to [EMAIL="linux-kernel@vger.kernel.org"]linux-kernel@vger.kernel.org[/EMAIL], adding your patch also for comments.

Dear herton,

sorry for the late reply. Today I sent the kernel driver patch for commenting to the linux-kernel list ([https://lkml.org/lkml/2011/6/21/245](https://lkml.org/lkml/2011/6/21/245)). Some days ago, they received also another patch, so chances are good, that this issue will finally be fixed. 

Br Thomas

---

### Post by rdratlos on 2011-06-23
> **rdratlos said:**
> Dear herton,

sorry for the late reply. Today I sent the kernel driver patch for commenting to the linux-kernel list ([https://lkml.org/lkml/2011/6/21/245](https://lkml.org/lkml/2011/6/21/245)). Some days ago, they received also another patch, so chances are good, that this issue will finally be fixed. 

Br Thomas

During discussion of the kernel driver patch above, Jean Delvare and Alex Deucher from the linux kernel team gave some valuable hints that lead me to a trivial workaround for our problem, until a kernel patch will finally solve it:

As *root* create a new file **options.config** in **/etc/modprobe.d** directory with following line:

```
options i2c-algo-bit bit_test=1
```Then restart Ubuntu check your kernel logs. The EDID spam should have gone. Instead, you should find the follwoing in the kernel logs:

```

[   14.275670] [drm] Initialized drm 1.1.0 20060810
[   15.017146] [drm] radeon defaulting to kernel modesetting.
[   15.017152] [drm] radeon kernel modesetting enabled.
[   15.020091] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.024389] [drm] initializing kernel modesetting (RS690 0x1002:0x791E).
.
.
.
[   15.111239] Radeon i2c bit bus 0xc0: Test OK
[   15.111346] Radeon i2c bit bus 0x90: Test OK
[   15.111428] Radeon i2c bit bus 0x91: Test OK
[   15.111474] **Radeon i2c bit bus 0x92: SDA stuck low!**
[   15.111512] **[drm:radeon_i2c_create] *ERROR* Failed to register bit i2c 0x92**
[   15.111695] **[drm:radeon_add_atom_connector] *ERROR* HDMI: Failed to assign ddc bus! Check dmesg for i2c errors.**
[   15.111789] [drm] Radeon Display Connectors
[   15.111791] [drm] Connector 0:
[   15.111793] [drm]   VGA
[   15.111796] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[   15.111799] [drm]   Encoders:
[   15.111800] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.111803] [drm] Connector 1:
[   15.111804] [drm]   S-video
[   15.111806] [drm]   Encoders:
[   15.111807] [drm]     TV1: INTERNAL_KLDSCP_DAC1
[   15.111809] [drm] Connector 2:
[   15.111811] [drm]   **HDMI-A**
[   15.111812] [drm]   HPD2
[   15.111814] [drm]   **DDC: no ddc bus **- possible BIOS bug - please report to xorg-driver-ati@lists.x.org
[   15.111816] [drm]   Encoders:
[   15.111818] [drm]     DFP2: INTERNAL_DDI
[   15.111820] [drm] Connector 3:
[   15.111822] [drm]   DVI-D
[   15.111824] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[   15.111826] [drm]   Encoders:
[   15.111828] [drm]     DFP3: INTERNAL_LVTM1
.
.
.
[   16.110040] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0

```On my Asus M2A-VM HDMI board I had disabled HDMI, I'm not even sure if I did install the packaged HDMI/AV/S/SPDIF card at all. This leads to not properly terminated i2c bus lines, which later-on cause the EDID spamming. Of course this is not a solution, but an easy work-around, which gives us both: kernel mode setting (KMS) and spam-free logs. 

Hope this helps you.

---

### Post by JoeFriday49 on 2011-06-29
> **rdratlos said:**
> During discussion of the kernel driver patch above, Jean Delvare and Alex Deucher from the linux kernel team gave some valuable hints that lead me to a trivial workaround for our problem, until a kernel patch will finally solve it:


When the kernel patch is developed will it be applied to the older supported versions as well as the current versions?  I'm using 10.04 LTS and was just curious if this will come down the Update Manager or will it have to be added manually...

---

### Post by Stephen_m64 on 2011-07-04
> **rdratlos said:**
> .................
As *root* create a new file **options.config** in **/etc/modprobe.d** directory with following line:

```
options i2c-algo-bit bit_test=1
```Then restart Ubuntu check your kernel logs. The EDID spam should have gone. 
......................

Followed the directions except named mine options.conf not options.config and it worked perfectly to fix the EDID spam on my  ECS A740GM-M MB


```
[   15.511202] Radeon i2c bit bus 0x92: SDA stuck low!
[   15.511235] [drm:radeon_i2c_create] *ERROR* Failed to register bit i2c 0x92
[   15.511313] [drm] Radeon Display Connectors
[   15.511315] [drm] Connector 0:
[   15.511316] [drm]   VGA
[   15.511318] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[   15.511320] [drm]   Encoders:
[   15.511322] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.511323] [drm] Connector 1:
[   15.511324] [drm]   DVI-D
[   15.511326] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[   15.511328] [drm]   Encoders:
[   15.511329] [drm]     DFP3: INTERNAL_LVTM1

```

Thanks.

---

### Post by rdratlos on 2011-07-13
> **Stephen_m64 said:**
> Followed the directions except named mine options.conf not options.config and it worked perfectly to fix the EDID spam on my  ECS A740GM-M MB


```
[   15.511202] Radeon i2c bit bus 0x92: SDA stuck low!
[   15.511235] [drm:radeon_i2c_create] *ERROR* Failed to register bit i2c 0x92
[   15.511313] [drm] Radeon Display Connectors
[   15.511315] [drm] Connector 0:
[   15.511316] [drm]   VGA
[   15.511318] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[   15.511320] [drm]   Encoders:
[   15.511322] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.511323] [drm] Connector 1:
[   15.511324] [drm]   DVI-D
[   15.511326] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[   15.511328] [drm]   Encoders:
[   15.511329] [drm]     DFP3: INTERNAL_LVTM1

```Thanks.

Could you please post the full dmesg log as it was before you applied i2c algo test? There is an upstream kernel patch underway which may also solve your problem without need for i2c algo testing. 
In addition, please post the output of 
> lspci -v 

---

### Post by Stephen_m64 on 2011-07-13
> **rdratlos said:**
> Could you please post the full dmesg log as it was before you applied i2c algo test? There is an upstream kernel patch underway which may also solve your problem without need for i2c algo testing. 
In addition, please post the output of lspci -v

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-server (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 (Ubuntu 2.6.38-8.42-server 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-server root=UUID=d4c723c1-a93d-42f4-b989-0074de188bae ro quiet
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b400 (usable)
[    0.000000]  BIOS-e820: 000000000009b400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfeb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfeb0000 - 00000000bfebe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfebe000 - 00000000bfee0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfeee000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: ECS A740GM-M/A740GM-M, BIOS 080014  05/07/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbfeb0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfeb0000
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bfeb0000 page 4k
[    0.000000] kernel direct mapping tables up to bfeb0000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ bfeaa000-bfeb0000
[    0.000000] RAMDISK: 366fc000 - 37376000
[    0.000000] ACPI: RSDP 00000000000faf20 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bfeb0000 0003C (v01 050710 RSDT1106 20100507 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bfeb0200 00084 (v02 050710 FACP1106 20100507 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bfeb0440 04A49 (v01  1AAAA 1AAAA000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bfebe000 00040
[    0.000000] ACPI: APIC 00000000bfeb0390 0006C (v01 050710 APIC1106 20100507 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bfeb0400 0003C (v01 050710 OEMMCFG  20100507 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bfebe040 00071 (v01 050710 OEMB1106 20100507 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bfeb4e90 00038 (v01 050710 OEMHPET  20100507 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bfeb4ed0 0028A (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012c200000-ffff88012f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000bfeb0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 982587
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3917 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767720 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bfeb0000 - 00000000bfebe000
[    0.000000] PM: Registered nosave memory: 00000000bfebe000 - 00000000bfee0000
[    0.000000] PM: Registered nosave memory: 00000000bfee0000 - 00000000bfeee000
[    0.000000] PM: Registered nosave memory: 00000000bfeee000 - 00000000bfef0000
[    0.000000] PM: Registered nosave memory: 00000000bfef0000 - 00000000bff00000
[    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at bff00000 (gap: bff00000:3f800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800bfc00000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 965557
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-server root=UUID=d4c723c1-a93d-42f4-b989-0074de188bae ro quiet
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ b4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ b4000000
[    0.000000] PM: Registered nosave memory: 00000000b4000000 - 00000000b8000000
[    0.000000] Memory: 3716600k/4980736k available (6023k kernel code, 1050388k absent, 213748k reserved, 5025k data, 880k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2500.207 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5000.41 BogoMIPS (lpj=25002070)
[    0.010010] pid_max: default: 32768 minimum: 301
[    0.010032] Security Framework initialized
[    0.010049] AppArmor: AppArmor initialized
[    0.010050] Yama: becoming mindful.
[    0.010506] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012709] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.013879] Mount-cache hash table entries: 256
[    0.014020] Initializing cgroup subsys ns
[    0.014023] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.014026] Initializing cgroup subsys cpuacct
[    0.014031] Initializing cgroup subsys memory
[    0.014040] Initializing cgroup subsys devices
[    0.014042] Initializing cgroup subsys freezer
[    0.014044] Initializing cgroup subsys net_cls
[    0.014046] Initializing cgroup subsys blkio
[    0.014078] tseg: 0000000000
[    0.014092] CPU: Physical Processor ID: 0
[    0.014093] CPU: Processor Core ID: 0
[    0.014096] mce: CPU supports 5 MCE banks
[    0.014107] using C1E aware idle routine
[    0.015549] ACPI: Core revision 20110112
[    0.018391] ftrace: allocating 24611 entries in 97 pages
[    0.020091] Setting APIC routing to flat
[    0.020393] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.126277] CPU0: AMD Athlon(tm) Dual Core Processor 4850B stepping 02
[    0.130000] Performance Events: AMD PMU driver.
[    0.130000] ... version:                0
[    0.130000] ... bit width:              48
[    0.130000] ... generic registers:      4
[    0.130000] ... value mask:             0000ffffffffffff
[    0.130000] ... max period:             00007fffffffffff
[    0.130000] ... fixed-purpose events:   0
[    0.130000] ... event mask:             000000000000000f
[    0.130000] Booting Node   0, Processors  #1
[    0.280135] Brought up 2 CPUs
[    0.280137] Total of 2 processors activated (10000.59 BogoMIPS).
[    0.280334] devtmpfs: initialized
[    0.281368] print_constraints: dummy: 
[    0.281368] Time: 23:34:51  Date: 07/13/11
[    0.281368] NET: Registered protocol family 16
[    0.281368] node 0 link 0: io port [1000, ffffff]
[    0.281368] TOM: 00000000d0000000 aka 3328M
[    0.281368] node 0 link 0: mmio [d0000000, dffeffff]
[    0.281368] node 0 link 0: mmio [d0000000, cfffffff]
[    0.281368] node 0 link 0: mmio [e0000000, efffffff]
[    0.281368] node 0 link 0: mmio [dfff0000, dfffffff]
[    0.281368] node 0 link 0: mmio [a0000, bffff]
[    0.281368] node 0 link 0: mmio [f0000000, ffffffff]
[    0.281368] TOM2: 0000000130000000 aka 4864M
[    0.281368] bus: [00, 07] on node 0 link 0
[    0.281368] bus: 00 index 0 [io  0x0000-0xffff]
[    0.281368] bus: 00 index 1 [mem 0xd0000000-0xdfffffff]
[    0.281368] bus: 00 index 2 [mem 0xe0000000-0xffffffff]
[    0.281368] bus: 00 index 3 [mem 0x000a0000-0x000bffff]
[    0.281368] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
[    0.281368] ACPI: bus type pci registered
[    0.281368] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.281368] PCI: not using MMCONFIG
[    0.281368] PCI: Using configuration type 1 for base access
[    0.281981] Trying to unpack rootfs image as initramfs...
[    0.282077] bio: create slab <bio-0> at 0
[    0.282797] ACPI: EC: Look up EC in DSDT
[    0.284531] ACPI: Executed 4 blocks of module-level executable AML code
[    0.311033] ACPI: Interpreter enabled
[    0.311037] ACPI: (supports S0 S3 S4 S5)
[    0.311054] ACPI: Using IOAPIC for interrupt routing
[    0.311076] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.312905] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.410084] ACPI: No dock devices found.
[    0.410088] HEST: Table not found.
[    0.410091] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.410174] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.410350] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.410352] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.410355] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.410357] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.410359] pci_root PNP0A03:00: host bridge window [mem 0xbff00000-0xdfffffff]
[    0.410362] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.410374] pci 0000:00:00.0: [1002:7911] type 0 class 0x000600
[    0.410399] pci 0000:00:01.0: [1002:7912] type 1 class 0x000604
[    0.410429] pci 0000:00:05.0: [1002:7915] type 1 class 0x000604
[    0.410451] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.410454] pci 0000:00:05.0: PME# disabled
[    0.410489] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.410510] pci 0000:00:11.0: reg 10: [io  0xd000-0xd007]
[    0.410520] pci 0000:00:11.0: reg 14: [io  0xc000-0xc003]
[    0.410530] pci 0000:00:11.0: reg 18: [io  0xb000-0xb007]
[    0.410540] pci 0000:00:11.0: reg 1c: [io  0xa000-0xa003]
[    0.410550] pci 0000:00:11.0: reg 20: [io  0x9000-0x900f]
[    0.410560] pci 0000:00:11.0: reg 24: [mem 0xfe8ff800-0xfe8ffbff]
[    0.410612] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.410625] pci 0000:00:12.0: reg 10: [mem 0xfe8fe000-0xfe8fefff]
[    0.410689] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.410703] pci 0000:00:12.1: reg 10: [mem 0xfe8fd000-0xfe8fdfff]
[    0.410773] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.410792] pci 0000:00:12.2: reg 10: [mem 0xfe8ff000-0xfe8ff0ff]
[    0.410862] pci 0000:00:12.2: supports D1 D2
[    0.410864] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.410868] pci 0000:00:12.2: PME# disabled
[    0.410890] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.410903] pci 0000:00:13.0: reg 10: [mem 0xfe8fc000-0xfe8fcfff]
[    0.410970] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.410984] pci 0000:00:13.1: reg 10: [mem 0xfe8f7000-0xfe8f7fff]
[    0.411054] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.411073] pci 0000:00:13.2: reg 10: [mem 0xfe8f6800-0xfe8f68ff]
[    0.411143] pci 0000:00:13.2: supports D1 D2
[    0.411145] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.411149] pci 0000:00:13.2: PME# disabled
[    0.411174] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.411267] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.411284] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.411294] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.411303] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.411313] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.411323] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.411373] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.411395] pci 0000:00:14.2: reg 10: [mem 0xfe8f0000-0xfe8f3fff 64bit]
[    0.411453] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.411457] pci 0000:00:14.2: PME# disabled
[    0.411471] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.411547] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.411588] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.411602] pci 0000:00:14.5: reg 10: [mem 0xfe8f5000-0xfe8f5fff]
[    0.411672] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.411688] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.411703] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.411717] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.411758] pci 0000:01:05.0: [1002:796e] type 0 class 0x000300
[    0.411768] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.411774] pci 0000:01:05.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.411779] pci 0000:01:05.0: reg 20: [io  0xe000-0xe0ff]
[    0.411783] pci 0000:01:05.0: reg 24: [mem 0xfe900000-0xfe9fffff]
[    0.411794] pci 0000:01:05.0: supports D1 D2
[    0.411807] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.411811] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.411814] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.411817] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.411853] pci 0000:02:00.0: [1969:2048] type 0 class 0x000200
[    0.411872] pci 0000:02:00.0: reg 10: [mem 0xfebc0000-0xfebfffff 64bit]
[    0.411917] pci 0000:02:00.0: reg 30: [mem 0xfeba0000-0xfebbffff pref]
[    0.411948] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.411952] pci 0000:02:00.0: PME# disabled
[    0.411970] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.411978] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.411982] pci 0000:00:05.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.411985] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.411988] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.412049] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.412053] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.412058] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.412062] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.412065] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.412067] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.412070] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.412072] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.412075] pci 0000:00:14.4:   bridge window [mem 0xbff00000-0xdfffffff] (subtractive decode)
[    0.412077] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.412089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.412223] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.412257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.412303] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.412377]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.416344] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.416385] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.416424] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.416463] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.416501] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.416541] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.416580] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[    0.416619] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.416742] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.416744] vgaarb: loaded
[    0.416930] SCSI subsystem initialized
[    0.417001] libata version 3.00 loaded.
[    0.417047] usbcore: registered new interface driver usbfs
[    0.417057] usbcore: registered new interface driver hub
[    0.417089] usbcore: registered new device driver usb
[    0.417194] wmi: Mapper loaded
[    0.417196] PCI: Using ACPI for IRQ routing
[    0.417199] PCI: pci_cache_line_size set to 64 bytes
[    0.417277] reserve RAM buffer: 000000000009b400 - 000000000009ffff 
[    0.417279] reserve RAM buffer: 00000000bfeb0000 - 00000000bfffffff 
[    0.417377] NetLabel: Initializing
[    0.417378] NetLabel:  domain hash size = 128
[    0.417380] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.417391] NetLabel:  unlabeled traffic allowed by default
[    0.417432] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.417437] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.419472] Switching to clocksource hpet
[    0.419580] Switched to NOHz mode on CPU #0
[    0.419580] Switched to NOHz mode on CPU #1
[    0.419580] AppArmor: AppArmor Filesystem Enabled
[    0.419580] pnp: PnP ACPI init
[    0.419580] ACPI: bus type pnp registered
[    0.419580] pnp 00:00: [bus 00-ff]
[    0.419580] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.419580] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.419580] pnp 00:00: [io  0x0d00-0xffff window]
[    0.419580] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.419580] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.419580] pnp 00:00: [mem 0xbff00000-0xdfffffff window]
[    0.419580] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.419580] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.419580] pnp 00:01: [dma 4]
[    0.419580] pnp 00:01: [io  0x0000-0x000f]
[    0.419580] pnp 00:01: [io  0x0081-0x0083]
[    0.419580] pnp 00:01: [io  0x0087]
[    0.419580] pnp 00:01: [io  0x0089-0x008b]
[    0.419580] pnp 00:01: [io  0x008f]
[    0.419580] pnp 00:01: [io  0x00c0-0x00df]
[    0.419580] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.419580] pnp 00:02: [io  0x0070-0x0071]
[    0.419580] pnp 00:02: [irq 8]
[    0.419580] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.419580] pnp 00:03: [io  0x0061]
[    0.419580] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.419580] pnp 00:04: [io  0x00f0-0x00ff]
[    0.419580] pnp 00:04: [irq 13]
[    0.419580] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.419580] pnp 00:05: [io  0x03f8-0x03ff]
[    0.419580] pnp 00:05: [irq 4]
[    0.419580] pnp 00:05: [dma 0 disabled]
[    0.419580] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.419580] pnp 00:06: [mem 0xfed00000-0xfed003ff]
[    0.419580] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.419580] pnp 00:07: [mem 0xfec00000-0xfec00fff]
[    0.419580] pnp 00:07: [mem 0xfee00000-0xfee00fff]
[    0.419580] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.419580] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.419580] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.419580] pnp 00:08: [io  0x0010-0x001f]
[    0.419580] pnp 00:08: [io  0x0022-0x003f]
[    0.419580] pnp 00:08: [io  0x0062-0x0063]
[    0.419580] pnp 00:08: [io  0x0065-0x006f]
[    0.419580] pnp 00:08: [io  0x0072-0x007f]
[    0.419580] pnp 00:08: [io  0x0080]
[    0.419580] pnp 00:08: [io  0x0084-0x0086]
[    0.419580] pnp 00:08: [io  0x0088]
[    0.419580] pnp 00:08: [io  0x008c-0x008e]
[    0.419580] pnp 00:08: [io  0x0090-0x009f]
[    0.419580] pnp 00:08: [io  0x00a2-0x00bf]
[    0.419580] pnp 00:08: [io  0x00b1]
[    0.419580] pnp 00:08: [io  0x00e0-0x00ef]
[    0.419580] pnp 00:08: [io  0x04d0-0x04d1]
[    0.419580] pnp 00:08: [io  0x040b]
[    0.419580] pnp 00:08: [io  0x04d6]
[    0.419580] pnp 00:08: [io  0x0c00-0x0c01]
[    0.419580] pnp 00:08: [io  0x0c14]
[    0.419580] pnp 00:08: [io  0x0c50-0x0c51]
[    0.419580] pnp 00:08: [io  0x0c52]
[    0.419580] pnp 00:08: [io  0x0c6c]
[    0.419580] pnp 00:08: [io  0x0c6f]
[    0.419580] pnp 00:08: [io  0x0cd0-0x0cd1]
[    0.419580] pnp 00:08: [io  0x0cd2-0x0cd3]
[    0.419580] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.419580] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.419580] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.419580] pnp 00:08: [io  0x0a7a-0x0b1f]
[    0.419580] pnp 00:08: [io  0x0b30-0x0bff]
[    0.419580] pnp 00:08: [io  0x0800-0x089f]
[    0.419580] pnp 00:08: [io  0x0b20-0x0b2f]
[    0.419580] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.419580] pnp 00:08: [io  0x0900-0x090f]
[    0.419580] pnp 00:08: [io  0x0910-0x091f]
[    0.419580] pnp 00:08: [io  0xfe00-0xfefe]
[    0.419580] pnp 00:08: [mem 0xffb80000-0xffbfffff]
[    0.419580] pnp 00:08: [mem 0xfec10000-0xfec1001f]
[    0.419580] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.419580] system 00:08: [io  0x040b] has been reserved
[    0.419580] system 00:08: [io  0x04d6] has been reserved
[    0.419580] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.419580] system 00:08: [io  0x0c14] has been reserved
[    0.419580] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.419580] system 00:08: [io  0x0c52] has been reserved
[    0.419580] system 00:08: [io  0x0c6c] has been reserved
[    0.419580] system 00:08: [io  0x0c6f] has been reserved
[    0.419580] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.419580] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.419580] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.419580] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.419580] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.419580] system 00:08: [io  0x0a7a-0x0b1f] has been reserved
[    0.419580] system 00:08: [io  0x0b30-0x0bff] has been reserved
[    0.419580] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.419580] system 00:08: [io  0x0b20-0x0b2f] has been reserved
[    0.419580] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.419580] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.419580] system 00:08: [io  0xfe00-0xfefe] has been reserved
[    0.419580] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.419580] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.419580] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.419580] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.419580] pnp 00:09: [io  0x0e00-0x0e0f]
[    0.419580] pnp 00:09: [io  0x0e80-0x0e8f]
[    0.419580] pnp 00:09: [io  0x0f40-0x0f4f]
[    0.419580] pnp 00:09: [io  0x0a30-0x0a3f]
[    0.419580] system 00:09: [io  0x0e00-0x0e0f] has been reserved
[    0.419580] system 00:09: [io  0x0e80-0x0e8f] has been reserved
[    0.419580] system 00:09: [io  0x0f40-0x0f4f] has been reserved
[    0.419580] system 00:09: [io  0x0a30-0x0a3f] has been reserved
[    0.419580] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.419773] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.419819] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.419822] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.419933] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.419935] pnp 00:0b: [mem 0x000c0000-0x000cffff]
[    0.419937] pnp 00:0b: [mem 0x000e0000-0x000fffff]
[    0.419943] pnp 00:0b: [mem 0x00100000-0xbfefffff]
[    0.419945] pnp 00:0b: [mem 0xfec00000-0xffffffff]
[    0.420031] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.420034] system 00:0b: [mem 0x000c0000-0x000cffff] has been reserved
[    0.420037] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.420039] system 00:0b: [mem 0x00100000-0xbfefffff] could not be reserved
[    0.420042] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.420045] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.420151] pnp: PnP ACPI: found 12 devices
[    0.420153] ACPI: ACPI bus type pnp unregistered
[    0.426374] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.426377] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.426380] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.426383] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.426387] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.426389] pci 0000:00:05.0:   bridge window [io  disabled]
[    0.426392] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.426395] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.426398] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.426400] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.426405] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.426409] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.426422] pci 0000:00:05.0: setting latency timer to 64
[    0.426430] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.426432] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.426435] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.426437] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.426439] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.426442] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.426444] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.426446] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]
[    0.426449] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.426451] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.426454] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.426456] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.426458] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.426461] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.426463] pci_bus 0000:03: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.426465] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.426503] NET: Registered protocol family 2
[    0.426678] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.428380] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.432337] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.432784] TCP: Hash tables configured (established 524288 bind 65536)
[    0.432787] TCP reno registered
[    0.432801] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.432849] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.432984] NET: Registered protocol family 1
[    0.575341] Freeing initrd memory: 12776k freed
[    0.580033] pci 0000:01:05.0: Boot video device
[    0.580039] PCI: CLS 64 bytes, default 64
[    0.580813] PCI-DMA: Disabling AGP.
[    0.580934] PCI-DMA: aperture base @ b4000000 size 65536 KB
[    0.580936] PCI-DMA: using GART IOMMU.
[    0.580941] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.584192] audit: initializing netlink socket (disabled)
[    0.584205] type=2000 audit(1310600091.580:1): initialized
[    0.597780] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.599672] VFS: Disk quotas dquot_6.5.2
[    0.599735] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.600429] fuse init (API version 7.16)
[    0.600532] msgmni has been set to 7412
[    0.600832] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.600872] io scheduler noop registered
[    0.600874] io scheduler deadline registered (default)
[    0.600921] io scheduler cfq registered
[    0.601107] pcieport 0000:00:05.0: setting latency timer to 64
[    0.601138] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    0.601211] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.601233] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.601372] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.660024] ACPI: Power Button [PWRB]
[    0.660071] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.660074] ACPI: Power Button [PWRF]
[    0.660226] ACPI: acpi_idle registered with cpuidle
[    0.662978] thermal LNXTHERM:00: registered as thermal_zone0
[    0.662981] ACPI: Thermal Zone [THRM] (30 C)
[    0.663021] ERST: Table is not found!
[    0.663119] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.683758] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.020713] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.021022] Linux agpgart interface v0.103
[    1.022190] brd: module loaded
[    1.022723] loop: module loaded
[    1.022842] i2c-core: driver [adp5520] using legacy suspend method
[    1.022844] i2c-core: driver [adp5520] using legacy resume method
[    1.023086] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.023124] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.023534] Fixed MDIO Bus: probed
[    1.023564] PPP generic driver version 2.4.2
[    1.023627] tun: Universal TUN/TAP device driver, 1.6
[    1.023629] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.023728] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.023778] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.023809] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.023863] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.060033] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.060053] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.060066] ehci_hcd 0000:00:12.2: debug port 1
[    1.060093] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff000
[    1.080017] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.080139] hub 1-0:1.0: USB hub found
[    1.080143] hub 1-0:1.0: 6 ports detected
[    1.080272] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.080285] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.080328] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.080359] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.080374] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.080387] ehci_hcd 0000:00:13.2: debug port 1
[    1.080406] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8f6800
[    1.100020] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.100123] hub 2-0:1.0: USB hub found
[    1.100127] hub 2-0:1.0: 6 ports detected
[    1.100220] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.100269] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.100281] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.100324] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.140047] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
[    1.204139] hub 3-0:1.0: USB hub found
[    1.204145] hub 3-0:1.0: 3 ports detected
[    1.204264] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.204275] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.204318] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.204356] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
[    1.264120] hub 4-0:1.0: USB hub found
[    1.264125] hub 4-0:1.0: 3 ports detected
[    1.264249] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.264261] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.264310] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.264357] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
[    1.324124] hub 5-0:1.0: USB hub found
[    1.324130] hub 5-0:1.0: 3 ports detected
[    1.324245] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.324257] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.324300] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.324338] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8f7000
[    1.384116] hub 6-0:1.0: USB hub found
[    1.384122] hub 6-0:1.0: 3 ports detected
[    1.384237] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.384248] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.384293] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.384331] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe8f5000
[    1.444115] hub 7-0:1.0: USB hub found
[    1.444121] hub 7-0:1.0: 2 ports detected
[    1.444203] uhci_hcd: USB Universal Host Controller Interface driver
[    1.444315] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.444668] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.444673] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.444744] mousedev: PS/2 mouse device common for all mice
[    1.444844] rtc_cmos 00:02: RTC can wake from S4
[    1.480061] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.480086] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.480190] device-mapper: uevent: version 1.0.3
[    1.480265] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.480351] device-mapper: multipath: version 1.2.0 loaded
[    1.480354] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.480491] cpuidle: using governor ladder
[    1.480493] cpuidle: using governor menu
[    1.480732] TCP cubic registered
[    1.480857] NET: Registered protocol family 10
[    1.481326] NET: Registered protocol family 17
[    1.481344] Registering the dns_resolver key type
[    1.481377] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4850B (2 cpu cores) (version 2.20.00)
[    1.481424] powernow-k8:    0 : fid 0x11 (2500 MHz), vid 0xe
[    1.481426] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xf
[    1.481428] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x11
[    1.481430] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x13
[    1.481432] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x15
[    1.481433] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x16
[    1.481584] PM: Hibernation image not present or could not be loaded.
[    1.481605] registered taskstats version 1
[    1.481810]   Magic number: 3:453:605
[    1.481904] rtc_cmos 00:02: setting system clock to 2011-07-13 23:34:53 UTC (1310600093)
[    1.481907] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.481909] EDD information not available.
[    1.483485] Freeing unused kernel memory: 880k freed
[    1.483868] Write protecting the kernel read-only data: 10240k
[    1.484338] Freeing unused kernel memory: 104k freed
[    1.488990] Freeing unused kernel memory: 1416k freed
[    1.512099] <30>udev[96]: starting version 167
[    1.597252] scsi0 : pata_atiixp
[    1.598618] scsi1 : pata_atiixp
[    1.599313] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.599316] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.604919] Atheros(R) L2 Ethernet Driver - version 2.2.3
[    1.604922] Copyright (c) 2007 Atheros Corporation.
[    1.606484] ahci 0000:00:11.0: version 3.0
[    1.606512] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.606574] ahci 0000:00:11.0: irq 41 for MSI/MSI-X
[    1.606692] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.606696] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.607746] atl2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.607764] atl2 0000:02:00.0: setting latency timer to 64
[    1.609040] scsi2 : ahci
[    1.611076] scsi3 : ahci
[    1.612973] scsi4 : ahci
[    1.614629] scsi5 : ahci
[    1.615961] scsi6 : ahci
[    1.617275] scsi7 : ahci
[    1.617361] ata3: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff900 irq 41
[    1.617365] ata4: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff980 irq 41
[    1.617368] ata5: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa00 irq 41
[    1.617372] ata6: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa80 irq 41
[    1.617375] ata7: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffb00 irq 41
[    1.617379] ata8: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffb80 irq 41
[    1.970046] ata7: SATA link down (SStatus 0 SControl 300)
[    1.970079] ata4: SATA link down (SStatus 0 SControl 300)
[    1.970131] ata6: SATA link down (SStatus 0 SControl 300)
[    1.980034] ata8: SATA link down (SStatus 0 SControl 300)
[    2.170018] ata3: softreset failed (device not ready)
[    2.170021] ata3: applying SB600 PMP SRST workaround and retrying
[    2.230017] ata5: softreset failed (device not ready)
[    2.230020] ata5: applying SB600 PMP SRST workaround and retrying
[    2.370026] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.430027] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.433370] ata5.00: ATA-8: WDC WD20EARS-00MVWB0, 50.0AB50, max UDMA/133
[    2.433373] ata5.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.437370] ata5.00: configured for UDMA/133
[    2.546287] ata3.00: ATA-7: ST3250820AS, 3.AAD, max UDMA/133
[    2.546290] ata3.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.604597] ata3.00: configured for UDMA/133
[    2.604730] scsi 2:0:0:0: Direct-Access     ATA      ST3250820AS      3.AA PQ: 0 ANSI: 5
[    2.604866] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.604908] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.604912] sd 2:0:0:0: [sda] Write Protect is off
[    2.604915] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.604934] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.605019] scsi 4:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 50.0 PQ: 0 ANSI: 5
[    2.605150] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    2.605240] sd 4:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.605285] sd 4:0:0:0: [sdb] Write Protect is off
[    2.605287] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.605307] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.623838]  sdb: sdb1
[    2.624118] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.740939]  sda: sda1 sda2 < sda5 >
[    2.741214] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.216692] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.483407] <30>udev[337]: starting version 167
[   13.523894] lp: driver loaded but no devices found
[   13.564868] Adding 9936892k swap on /dev/sda5.  Priority:-1 extents:1 across:9936892k 
[   13.652135] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.679975] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   13.681040] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   13.681123] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   13.689606] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   13.736662] Bridge firewalling registered
[   13.740747] device eth0 entered promiscuous mode
[   13.742149] atl2 0000:02:00.0: irq 42 for MSI/MSI-X
[   13.742804] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.824772] MCE: In-kernel MCE decoding enabled.
[   13.845385] [drm] Initialized drm 1.1.0 20060810
[   13.852867] EDAC MC: Ver: 2.1.0 Apr 11 2011
[   13.865655] EDAC amd64_edac: v3.3.0
[   13.873928] EDAC amd64: DRAM ECC disabled.
[   13.873936] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   13.873938]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   13.873939]  (Note that use of the override may cause unknown side effects.)
[   13.907374] type=1400 audit(1310600105.910:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=458 comm="apparmor_parser"
[   13.907710] type=1400 audit(1310600105.910:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=458 comm="apparmor_parser"
[   13.907921] type=1400 audit(1310600105.910:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=458 comm="apparmor_parser"
[   13.909367] type=1400 audit(1310600105.910:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=507 comm="apparmor_parser"
[   13.909704] type=1400 audit(1310600105.910:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=507 comm="apparmor_parser"
[   13.909920] type=1400 audit(1310600105.910:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=507 comm="apparmor_parser"
[   13.910108] [drm] radeon defaulting to kernel modesetting.
[   13.910111] [drm] radeon kernel modesetting enabled.
[   13.911655] type=1400 audit(1310600105.920:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=570 comm="apparmor_parser"
[   13.911999] type=1400 audit(1310600105.920:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=570 comm="apparmor_parser"
[   13.912217] type=1400 audit(1310600105.920:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=570 comm="apparmor_parser"
[   13.920243] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.933479] [drm] initializing kernel modesetting (RS740 0x1002:0x796E).
[   13.933523] [drm] register mmio base: 0xFEAF0000
[   13.933525] [drm] register mmio size: 65536
[   13.934085] ATOM BIOS: ATI
[   13.934101] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[   13.934104] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[   13.934126] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.934128] [drm] Driver supports precise vblank timestamp query.
[   13.934140] [drm] radeon: irq initialized.
[   13.934312] [drm] Detected VRAM RAM=256M, BAR=256M
[   13.934317] [drm] RAM width 128bits DDR
[   13.941075] [TTM] Zone  kernel: Available graphics memory: 1898864 kiB.
[   13.941079] [TTM] Initializing pool allocator.
[   13.941103] [drm] radeon: 256M of VRAM memory ready
[   13.941106] [drm] radeon: 512M of GTT memory ready.
[   13.941140] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.944564] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   13.946950] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   13.947526] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   13.947580] br0: port 1(eth0) entering forwarding state
[   13.947582] br0: port 1(eth0) entering forwarding state
[   13.952939] radeon 0000:01:05.0: WB enabled
[   13.953020] [drm] Loading RS690/RS740 Microcode
[   13.964675] [drm] radeon: ring at 0x00000000A0001000
[   13.964694] [drm] ring test succeeded in 1 usecs
[   13.964817] [drm] radeon: ib pool ready.
[   13.964887] [drm] ib test succeeded in 0 usecs
[   13.964889] [drm] Enabling audio support
[   13.964896] failed to evaluate ATIF got AE_BAD_PARAMETER
[   13.965102] [drm] Radeon Display Connectors
[   13.965104] [drm] Connector 0:
[   13.965105] [drm]   VGA
[   13.965107] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[   13.965109] [drm]   Encoders:
[   13.965110] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   13.965112] [drm] Connector 1:
[   13.965113] [drm]   DVI-D
[   13.965114] [drm]   HPD2
[   13.965116] [drm]   DDC: 0x7e40 0x7e60 0x7e44 0x7e64 0x7e48 0x7e68 0x7e4c 0x7e6c
[   13.965117] [drm]   Encoders:
[   13.965119] [drm]     DFP2: INTERNAL_DDI
[   13.965120] [drm] Connector 2:
[   13.965121] [drm]   DVI-D
[   13.965123] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[   13.965125] [drm]   Encoders:
[   13.965126] [drm]     DFP3: INTERNAL_LVTM1
[   13.999448] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.030920] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 95
[   14.030926] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.030931] <3>03 01 01 01 01 01 01 01 01 01 01 01 01 01 00 01  ................
[   14.030933] <3>7f 01 01 01 01 01 01 01 00 00 00 7f 01 01 01 01  ................
[   14.030935] <3>01 01 01 00 00 00 00 00 00 01 01 01 01 01 07 01  ................
[   14.030937] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 00  ................
[   14.030939] <3>01 01 01 01 01 00 01 01 01 01 00 00 00 00 00 00  ................
[   14.030941] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.030943] <3>00 00 00 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.030945] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.030946] 
[   14.083544] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 117
[   14.083548] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.083551] <3>07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.083553] <3>00 00 00 00 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.083555] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.083557] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.083559] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.083561] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.083563] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.083565] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 03 01 01  ................
[   14.083567] 
[   14.140755] input: HDA ATI SB Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input2
[   14.140861] input: HDA ATI SB Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input3
[   14.140923] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[   14.140981] input: HDA ATI SB Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[   14.141045] input: HDA ATI SB HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   14.144659] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 153
[   14.144665] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.144670] <3>07 00 00 00 00 00 00 00 00 00 00 00 00 01 01 01  ................
[   14.144672] <3>01 01 01 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.144674] <3>00 00 00 00 00 00 00 00 00 01 01 01 01 01 01 01  ................
[   14.144676] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.144678] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.144680] <3>01 01 01 01 01 01 01 01 01 01 01 01 00 01 01 01  ................
[   14.144682] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.144684] <3>01 01 01 01 01 01 01 3f 00 00 00 00 00 00 00 00  .......?........
[   14.144686] 
[   14.194748] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 115
[   14.194752] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.194756] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 01  ................
[   14.194758] <3>01 00 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.194760] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.194762] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.194764] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.194766] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.194768] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.194770] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.194772] 
[   14.194775] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
[   14.353403] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   14.353407] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.353410] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.353412] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.353415] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.353417] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.353419] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.353421] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.353423] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.353425] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.353426] 
[   14.403461] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   14.403465] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.403468] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.403470] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.403473] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.403475] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.403477] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.403479] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.403481] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.403483] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.403484] 
[   14.453530] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   14.453534] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.453537] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.453539] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.453541] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.453543] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.453545] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.453547] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.453549] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.453551] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.453553] 
[   14.503586] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   14.503590] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.503595] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.503597] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.503599] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.503601] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.503603] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.503605] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.503607] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.503609] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.503611] 
[   14.503612] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
[   14.503615] [drm:radeon_dvi_detect] *ERROR* DVI-D-1: probed a monitor but no|invalid EDID
[   14.505546] No connectors reported connected with modes
[   14.505550] [drm] Cannot find any crtc or sizes - going 1024x768
[   14.511139] [drm] fb mappable at 0xD0040000
[   14.511141] [drm] vram apper at 0xD0000000
[   14.511142] [drm] size 3145728
[   14.511143] [drm] fb depth is 24
[   14.511145] [drm]    pitch is 4096
[   14.511313] Console: switching to colour frame buffer device 128x48
[   14.516666] fb0: radeondrmfb frame buffer device
[   14.516668] drm: registered panic notifier
[   14.516675] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
[   14.701956] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.764477] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 2
[   14.764573] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.764633] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.764635] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.764637] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.764639] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.764641] <3>00 00 00 ff 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.764643] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.764645] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.764647] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.764649] 
[   14.814691] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   14.814777] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.814835] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.814838] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.814840] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.814842] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.814844] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.814846] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.814848] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.814850] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.814851] 
[   14.868788] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 176
[   14.868885] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.868945] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.868947] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.868949] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0f  ................
[   14.868951] <3>00 00 00 00 1f 00 7f 00 00 00 00 00 00 00 00 00  ................
[   14.868953] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.868955] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.868957] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.868959] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.868961] 
[   14.919041] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   14.919127] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.919186] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.919188] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.919190] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.919192] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.919194] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.919197] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.919199] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.919201] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.919202] 
[   14.919206] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
[   14.919209] [drm:radeon_dvi_detect] *ERROR* DVI-D-1: probed a monitor but no|invalid EDID
[   14.972728] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   14.972814] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.972873] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.972875] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.972877] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.972879] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.972881] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.972883] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.972885] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.972887] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.972889] 
[   15.022932] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   15.023018] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   15.023076] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.023078] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.023080] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.023082] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.023084] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.023086] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.023088] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.023090] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.023092] 
[   15.075342] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 12
[   15.075439] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   15.075499] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.075501] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.075503] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.075505] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.075507] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.075509] <3>00 00 00 00 00 00 00 00 00 00 00 00 ff 01 01 01  ................
[   15.075511] <3>01 01 01 01 01 01 00 00 00 00 00 00 00 00 00 00  ................
[   15.075514] <3>00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.075517] 
[   15.082015] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   15.126826] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 27
[   15.126918] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   15.126977] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 03  ................
[   15.126979] <3>07 ff 00 00 00 00 00 01 01 00 03 07 00 00 01 00  ................
[   15.126981] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.126983] <3>00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 00  ................
[   15.126985] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.126987] <3>00 00 00 00 01 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.126989] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.126991] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   15.126993] 
[   15.126996] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
[   15.126999] [drm:radeon_dvi_detect] *ERROR* DVI-D-1: probed a monitor but no|invalid EDID
[   15.273049] type=1400 audit(1310600107.280:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=777 comm="apparmor_parser"
[   15.516524] kvm: Nested Virtualization enabled
[   15.570320] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.618191] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.535623] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   23.940013] br0: no IPv6 routers present
[   24.550015] eth0: no IPv6 routers present
[   24.575301] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   24.575393] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   24.575453] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.575456] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.575458] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.575460] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.575462] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.575464] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.575466] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.575468] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.575469] 
[   24.625504] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   24.628077] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   24.630645] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.630647] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.630651] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.630653] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.630656] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.630659] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.630662] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.630664] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.630667] 
[   24.680695] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   24.683239] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   24.685744] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.685746] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.685748] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.685750] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.685752] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.685754] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.685756] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.685758] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.685760] 
[   24.735787] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   24.738327] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   24.740831] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.740834] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.740837] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.740840] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.740842] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.740845] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.740848] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.740851] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   24.740853] 
[   24.740857] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
[   24.740861] [drm:radeon_dvi_detect] *ERROR* DVI-D-1: probed a monitor but no|invalid EDID
[   34.815299] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   34.817869] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   34.820397] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.820399] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.820402] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.820405] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.820408] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.820410] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.820413] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.820416] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.820418] 
[   34.870444] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   34.872965] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   34.875466] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.875468] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.875470] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.875472] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.875474] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.875476] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.875478] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.875480] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.875482] 
[   34.925504] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   34.928005] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   34.930489] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.930491] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.930495] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.930498] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.930501] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.930503] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.930506] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.930509] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.930512] 
[   34.980543] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 3
[   34.983035] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   34.985470] <3>03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.985472] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.985474] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.985476] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.985478] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.985480] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.985482] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.985484] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   34.985486] 
[   34.985488] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
[   34.985491] [drm:radeon_dvi_detect] *ERROR* DVI-D-1: probed a monitor but no|invalid EDID
```

sudo lspci -v:
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, 66MHz, medium devsel, latency 0

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: Elitegroup Computer Systems Device 2615
	Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: feb00000-febfffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [b0] Subsystem: Elitegroup Computer Systems Device 2615
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Virtual Channel
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Elitegroup Computer Systems Device 4390
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 41
	I/O ports at d000 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at b000 [size=8]
	I/O ports at a000 [size=4]
	I/O ports at 9000 [size=16]
	Memory at fe8ff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [50] MSI: Enable+ Count=1/4 Maskable- 64bit+
	Capabilities: [70] SATA HBA v1.0
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe8fe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe8fd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe8ff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe8fc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe8f7000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fe8f6800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: [70] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fe8f0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe8f5000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100 (prog-if 00 [VGA controller])
	Subsystem: Elitegroup Computer Systems Device 2615
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at e000 [size=256]
	Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 2
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: radeon
	Kernel modules: radeon

02:00.0 Ethernet controller: Atheros Communications L2 Fast Ethernet (rev a0)
	Subsystem: Elitegroup Computer Systems Device 2048
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at feba0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: atl2
	Kernel modules: atl2
```

As requested.

---

### Post by rdratlos on 2011-07-14
> **Stephen_m64 said:**
> dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-server (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 (Ubuntu 2.6.38-8.42-server 2.6.38.2)

```sudo lspci -v:
```

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100 (prog-if 00 [VGA controller])
    Subsystem: Elitegroup Computer Systems Device 2615
    Flags: bus master, fast devsel, latency 64, IRQ 18
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at e000 [size=256]
    Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 2
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: radeon
    Kernel modules: radeon

```

From checking the information that you've provided I believe that the new extended DDC probing mechanism of the kernel radeon driver will solve your problem. In Launchpad PPA you will find a 2.6.38.8 test kernel, where I've included your ECS motherboard. Could you please test it and provide me feedback? In case the fix solves your problem I will send the patch upstream to get it included into the linux kernel radeon driver.

Test kernel installation procedure:
Add following two lines to file** /etc/apt/sources.list**:
```
deb http://ppa.launchpad.net/rdratlos/ppa-asus-m2a-fix/ubuntu natty main
deb-src http://ppa.launchpad.net/rdratlos/ppa-asus-m2a-fix/ubuntu natty main

```Add PPA key to your apt keyring:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 61B873BC
```Add new test kernel version (2.6.38-8.43~lp722806thor3) to your 2.6.38-8.42-server kernel:
```

sudo apt-get update
sudo apt-get upgrade

```Disable again i2c testing by removing file **options.conf** in **/etc/modprobe.d** directory.

After reboot please check dmesg for the correct kernel version and the drm log entries. There should be four EDID dumps in the log after the Radeon connectors list and then ... SILENCE. Good luck!
As soon as you have the new dmesg log, please post it. 

P.S: After you've finished testing if you don't like the solution, remove the two lines from file **/etc/apt/sources.list **and run 
```
sudo apt-get update
```once more.

---

### Post by Stephen_m64 on 2011-07-14
I put the ppa repo into its own file in /etc/apt/sources.list.d as i don't use sources.list, added the repo key, updated and installed.

had to edit /etc/default/grub and force the kernel to load as 2.6.38-10-server was released and that was booting instead.

uname -a
```

Linux miniserve 2.6.38-8-server #43~lp722806thor3-Ubuntu SMP Thu Jul 14 18:58:48 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-server (buildd@louvi) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #43~lp722806thor3-Ubuntu SMP Thu Jul 14 18:58:48 UTC 2011 (Ubuntu 2.6.38-8.43~lp722806thor3-server 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-server root=UUID=d4c723c1-a93d-42f4-b989-0074de188bae ro quiet
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b400 (usable)
[    0.000000]  BIOS-e820: 000000000009b400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfeb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfeb0000 - 00000000bfebe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfebe000 - 00000000bfee0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfeee000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: ECS A740GM-M/A740GM-M, BIOS 080014  05/07/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbfeb0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfeb0000
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bfeb0000 page 4k
[    0.000000] kernel direct mapping tables up to bfeb0000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ bfeaa000-bfeb0000
[    0.000000] RAMDISK: 366fc000 - 37376000
[    0.000000] ACPI: RSDP 00000000000faf20 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bfeb0000 0003C (v01 050710 RSDT1106 20100507 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bfeb0200 00084 (v02 050710 FACP1106 20100507 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bfeb0440 04A49 (v01  1AAAA 1AAAA000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bfebe000 00040
[    0.000000] ACPI: APIC 00000000bfeb0390 0006C (v01 050710 APIC1106 20100507 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bfeb0400 0003C (v01 050710 OEMMCFG  20100507 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bfebe040 00071 (v01 050710 OEMB1106 20100507 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bfeb4e90 00038 (v01 050710 OEMHPET  20100507 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bfeb4ed0 0028A (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012c200000-ffff88012f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000bfeb0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 982587
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3917 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767720 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bfeb0000 - 00000000bfebe000
[    0.000000] PM: Registered nosave memory: 00000000bfebe000 - 00000000bfee0000
[    0.000000] PM: Registered nosave memory: 00000000bfee0000 - 00000000bfeee000
[    0.000000] PM: Registered nosave memory: 00000000bfeee000 - 00000000bfef0000
[    0.000000] PM: Registered nosave memory: 00000000bfef0000 - 00000000bff00000
[    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at bff00000 (gap: bff00000:3f800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800bfc00000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 965557
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-server root=UUID=d4c723c1-a93d-42f4-b989-0074de188bae ro quiet
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ b4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ b4000000
[    0.000000] PM: Registered nosave memory: 00000000b4000000 - 00000000b8000000
[    0.000000] Memory: 3716600k/4980736k available (6023k kernel code, 1050388k absent, 213748k reserved, 5025k data, 880k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2499.968 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.020006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4999.93 BogoMIPS (lpj=24999680)
[    0.020010] pid_max: default: 32768 minimum: 301
[    0.020032] Security Framework initialized
[    0.020049] AppArmor: AppArmor initialized
[    0.020051] Yama: becoming mindful.
[    0.020480] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.022663] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.023837] Mount-cache hash table entries: 256
[    0.023978] Initializing cgroup subsys ns
[    0.023982] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.023985] Initializing cgroup subsys cpuacct
[    0.023989] Initializing cgroup subsys memory
[    0.023998] Initializing cgroup subsys devices
[    0.024001] Initializing cgroup subsys freezer
[    0.024002] Initializing cgroup subsys net_cls
[    0.024004] Initializing cgroup subsys blkio
[    0.024036] tseg: 0000000000
[    0.024051] CPU: Physical Processor ID: 0
[    0.024052] CPU: Processor Core ID: 0
[    0.024054] mce: CPU supports 5 MCE banks
[    0.024065] using C1E aware idle routine
[    0.025507] ACPI: Core revision 20110112
[    0.028346] ftrace: allocating 24611 entries in 97 pages
[    0.030092] Setting APIC routing to flat
[    0.030392] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.136229] CPU0: AMD Athlon(tm) Dual Core Processor 4850B stepping 02
[    0.140000] Performance Events: AMD PMU driver.
[    0.140000] ... version:                0
[    0.140000] ... bit width:              48
[    0.140000] ... generic registers:      4
[    0.140000] ... value mask:             0000ffffffffffff
[    0.140000] ... max period:             00007fffffffffff
[    0.140000] ... fixed-purpose events:   0
[    0.140000] ... event mask:             000000000000000f
[    0.140000] Booting Node   0, Processors  #1
[    0.290134] Brought up 2 CPUs
[    0.290136] Total of 2 processors activated (10000.11 BogoMIPS).
[    0.290330] devtmpfs: initialized
[    0.291368] print_constraints: dummy: 
[    0.291368] Time:  0:39:17  Date: 07/15/11
[    0.291368] NET: Registered protocol family 16
[    0.291368] node 0 link 0: io port [1000, ffffff]
[    0.291368] TOM: 00000000d0000000 aka 3328M
[    0.291368] node 0 link 0: mmio [d0000000, dffeffff]
[    0.291368] node 0 link 0: mmio [d0000000, cfffffff]
[    0.291368] node 0 link 0: mmio [e0000000, efffffff]
[    0.291368] node 0 link 0: mmio [dfff0000, dfffffff]
[    0.291368] node 0 link 0: mmio [a0000, bffff]
[    0.291368] node 0 link 0: mmio [f0000000, ffffffff]
[    0.291368] TOM2: 0000000130000000 aka 4864M
[    0.291368] bus: [00, 07] on node 0 link 0
[    0.291368] bus: 00 index 0 [io  0x0000-0xffff]
[    0.291368] bus: 00 index 1 [mem 0xd0000000-0xdfffffff]
[    0.291368] bus: 00 index 2 [mem 0xe0000000-0xffffffff]
[    0.291368] bus: 00 index 3 [mem 0x000a0000-0x000bffff]
[    0.291368] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
[    0.291368] ACPI: bus type pci registered
[    0.291368] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.291368] PCI: not using MMCONFIG
[    0.291368] PCI: Using configuration type 1 for base access
[    0.291983] Trying to unpack rootfs image as initramfs...
[    0.292080] bio: create slab <bio-0> at 0
[    0.292801] ACPI: EC: Look up EC in DSDT
[    0.294533] ACPI: Executed 4 blocks of module-level executable AML code
[    0.321038] ACPI: Interpreter enabled
[    0.321041] ACPI: (supports S0 S3 S4 S5)
[    0.321058] ACPI: Using IOAPIC for interrupt routing
[    0.321081] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.322911] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.420084] ACPI: No dock devices found.
[    0.420088] HEST: Table not found.
[    0.420091] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.420174] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.420348] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.420351] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.420353] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.420355] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.420358] pci_root PNP0A03:00: host bridge window [mem 0xbff00000-0xdfffffff]
[    0.420360] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.420372] pci 0000:00:00.0: [1002:7911] type 0 class 0x000600
[    0.420397] pci 0000:00:01.0: [1002:7912] type 1 class 0x000604
[    0.420427] pci 0000:00:05.0: [1002:7915] type 1 class 0x000604
[    0.420449] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.420452] pci 0000:00:05.0: PME# disabled
[    0.420486] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.420508] pci 0000:00:11.0: reg 10: [io  0xd000-0xd007]
[    0.420518] pci 0000:00:11.0: reg 14: [io  0xc000-0xc003]
[    0.420528] pci 0000:00:11.0: reg 18: [io  0xb000-0xb007]
[    0.420538] pci 0000:00:11.0: reg 1c: [io  0xa000-0xa003]
[    0.420548] pci 0000:00:11.0: reg 20: [io  0x9000-0x900f]
[    0.420558] pci 0000:00:11.0: reg 24: [mem 0xfe8ff800-0xfe8ffbff]
[    0.420610] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.420623] pci 0000:00:12.0: reg 10: [mem 0xfe8fe000-0xfe8fefff]
[    0.420689] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.420702] pci 0000:00:12.1: reg 10: [mem 0xfe8fd000-0xfe8fdfff]
[    0.420772] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.420791] pci 0000:00:12.2: reg 10: [mem 0xfe8ff000-0xfe8ff0ff]
[    0.420861] pci 0000:00:12.2: supports D1 D2
[    0.420863] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.420867] pci 0000:00:12.2: PME# disabled
[    0.420889] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.420903] pci 0000:00:13.0: reg 10: [mem 0xfe8fc000-0xfe8fcfff]
[    0.420971] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.420984] pci 0000:00:13.1: reg 10: [mem 0xfe8f7000-0xfe8f7fff]
[    0.421054] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.421073] pci 0000:00:13.2: reg 10: [mem 0xfe8f6800-0xfe8f68ff]
[    0.421144] pci 0000:00:13.2: supports D1 D2
[    0.421146] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.421150] pci 0000:00:13.2: PME# disabled
[    0.421175] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.421268] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.421285] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.421294] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.421304] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.421314] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.421323] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.421373] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.421395] pci 0000:00:14.2: reg 10: [mem 0xfe8f0000-0xfe8f3fff 64bit]
[    0.421453] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.421457] pci 0000:00:14.2: PME# disabled
[    0.421471] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.421547] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.421588] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.421602] pci 0000:00:14.5: reg 10: [mem 0xfe8f5000-0xfe8f5fff]
[    0.421672] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.421688] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.421703] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.421718] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.421759] pci 0000:01:05.0: [1002:796e] type 0 class 0x000300
[    0.421768] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.421774] pci 0000:01:05.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.421778] pci 0000:01:05.0: reg 20: [io  0xe000-0xe0ff]
[    0.421783] pci 0000:01:05.0: reg 24: [mem 0xfe900000-0xfe9fffff]
[    0.421794] pci 0000:01:05.0: supports D1 D2
[    0.421807] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.421810] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.421813] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.421817] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.421853] pci 0000:02:00.0: [1969:2048] type 0 class 0x000200
[    0.421872] pci 0000:02:00.0: reg 10: [mem 0xfebc0000-0xfebfffff 64bit]
[    0.421917] pci 0000:02:00.0: reg 30: [mem 0xfeba0000-0xfebbffff pref]
[    0.421948] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.421952] pci 0000:02:00.0: PME# disabled
[    0.421969] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.421977] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.421981] pci 0000:00:05.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.421984] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.421987] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.422048] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.422052] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.422057] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.422061] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.422064] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.422066] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.422069] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.422071] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.422074] pci 0000:00:14.4:   bridge window [mem 0xbff00000-0xdfffffff] (subtractive decode)
[    0.422077] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.422089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.422222] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.422257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.422302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.422376]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.426340] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.426381] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.426420] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.426459] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.426497] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.426537] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.426576] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[    0.426615] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.426738] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.426741] vgaarb: loaded
[    0.426925] SCSI subsystem initialized
[    0.426998] libata version 3.00 loaded.
[    0.427043] usbcore: registered new interface driver usbfs
[    0.427052] usbcore: registered new interface driver hub
[    0.427083] usbcore: registered new device driver usb
[    0.427083] wmi: Mapper loaded
[    0.427083] PCI: Using ACPI for IRQ routing
[    0.427083] PCI: pci_cache_line_size set to 64 bytes
[    0.427083] reserve RAM buffer: 000000000009b400 - 000000000009ffff 
[    0.427083] reserve RAM buffer: 00000000bfeb0000 - 00000000bfffffff 
[    0.427083] NetLabel: Initializing
[    0.427083] NetLabel:  domain hash size = 128
[    0.427083] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.427083] NetLabel:  unlabeled traffic allowed by default
[    0.427083] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.427083] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.427083] Switching to clocksource hpet
[    0.429613] Switched to NOHz mode on CPU #0
[    0.429615] Switched to NOHz mode on CPU #1
[    0.429613] AppArmor: AppArmor Filesystem Enabled
[    0.429613] pnp: PnP ACPI init
[    0.429613] ACPI: bus type pnp registered
[    0.429613] pnp 00:00: [bus 00-ff]
[    0.429613] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.429613] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.429613] pnp 00:00: [io  0x0d00-0xffff window]
[    0.429613] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.429613] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.429613] pnp 00:00: [mem 0xbff00000-0xdfffffff window]
[    0.429613] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.429613] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.429613] pnp 00:01: [dma 4]
[    0.429613] pnp 00:01: [io  0x0000-0x000f]
[    0.429613] pnp 00:01: [io  0x0081-0x0083]
[    0.429613] pnp 00:01: [io  0x0087]
[    0.429613] pnp 00:01: [io  0x0089-0x008b]
[    0.429613] pnp 00:01: [io  0x008f]
[    0.429613] pnp 00:01: [io  0x00c0-0x00df]
[    0.429613] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.429613] pnp 00:02: [io  0x0070-0x0071]
[    0.429613] pnp 00:02: [irq 8]
[    0.429613] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.429613] pnp 00:03: [io  0x0061]
[    0.429613] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.429613] pnp 00:04: [io  0x00f0-0x00ff]
[    0.429613] pnp 00:04: [irq 13]
[    0.429613] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.429613] pnp 00:05: [io  0x03f8-0x03ff]
[    0.429613] pnp 00:05: [irq 4]
[    0.429613] pnp 00:05: [dma 0 disabled]
[    0.429613] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.429613] pnp 00:06: [mem 0xfed00000-0xfed003ff]
[    0.429613] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.429613] pnp 00:07: [mem 0xfec00000-0xfec00fff]
[    0.429613] pnp 00:07: [mem 0xfee00000-0xfee00fff]
[    0.429613] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.429613] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.429613] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.429613] pnp 00:08: [io  0x0010-0x001f]
[    0.429613] pnp 00:08: [io  0x0022-0x003f]
[    0.429613] pnp 00:08: [io  0x0062-0x0063]
[    0.429613] pnp 00:08: [io  0x0065-0x006f]
[    0.429613] pnp 00:08: [io  0x0072-0x007f]
[    0.429613] pnp 00:08: [io  0x0080]
[    0.429613] pnp 00:08: [io  0x0084-0x0086]
[    0.429613] pnp 00:08: [io  0x0088]
[    0.429613] pnp 00:08: [io  0x008c-0x008e]
[    0.429613] pnp 00:08: [io  0x0090-0x009f]
[    0.429613] pnp 00:08: [io  0x00a2-0x00bf]
[    0.429613] pnp 00:08: [io  0x00b1]
[    0.429613] pnp 00:08: [io  0x00e0-0x00ef]
[    0.429613] pnp 00:08: [io  0x04d0-0x04d1]
[    0.429613] pnp 00:08: [io  0x040b]
[    0.429613] pnp 00:08: [io  0x04d6]
[    0.429613] pnp 00:08: [io  0x0c00-0x0c01]
[    0.429613] pnp 00:08: [io  0x0c14]
[    0.429613] pnp 00:08: [io  0x0c50-0x0c51]
[    0.429613] pnp 00:08: [io  0x0c52]
[    0.429613] pnp 00:08: [io  0x0c6c]
[    0.429613] pnp 00:08: [io  0x0c6f]
[    0.429613] pnp 00:08: [io  0x0cd0-0x0cd1]
[    0.429613] pnp 00:08: [io  0x0cd2-0x0cd3]
[    0.429613] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.429613] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.429613] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.429613] pnp 00:08: [io  0x0a7a-0x0b1f]
[    0.429613] pnp 00:08: [io  0x0b30-0x0bff]
[    0.429613] pnp 00:08: [io  0x0800-0x089f]
[    0.429613] pnp 00:08: [io  0x0b20-0x0b2f]
[    0.429613] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.429613] pnp 00:08: [io  0x0900-0x090f]
[    0.429613] pnp 00:08: [io  0x0910-0x091f]
[    0.429613] pnp 00:08: [io  0xfe00-0xfefe]
[    0.429613] pnp 00:08: [mem 0xffb80000-0xffbfffff]
[    0.429613] pnp 00:08: [mem 0xfec10000-0xfec1001f]
[    0.429613] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.429613] system 00:08: [io  0x040b] has been reserved
[    0.429613] system 00:08: [io  0x04d6] has been reserved
[    0.429613] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.429613] system 00:08: [io  0x0c14] has been reserved
[    0.429613] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.429613] system 00:08: [io  0x0c52] has been reserved
[    0.429613] system 00:08: [io  0x0c6c] has been reserved
[    0.429613] system 00:08: [io  0x0c6f] has been reserved
[    0.429613] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.429613] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.429613] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.429613] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.429613] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.429613] system 00:08: [io  0x0a7a-0x0b1f] has been reserved
[    0.429613] system 00:08: [io  0x0b30-0x0bff] has been reserved
[    0.429613] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.429613] system 00:08: [io  0x0b20-0x0b2f] has been reserved
[    0.429613] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.429613] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.429613] system 00:08: [io  0xfe00-0xfefe] has been reserved
[    0.429613] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.429613] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.429613] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.429613] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.429613] pnp 00:09: [io  0x0e00-0x0e0f]
[    0.429613] pnp 00:09: [io  0x0e80-0x0e8f]
[    0.429613] pnp 00:09: [io  0x0f40-0x0f4f]
[    0.429613] pnp 00:09: [io  0x0a30-0x0a3f]
[    0.429613] system 00:09: [io  0x0e00-0x0e0f] has been reserved
[    0.429613] system 00:09: [io  0x0e80-0x0e8f] has been reserved
[    0.429613] system 00:09: [io  0x0f40-0x0f4f] has been reserved
[    0.429613] system 00:09: [io  0x0a30-0x0a3f] has been reserved
[    0.429613] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.429645] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.429692] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.429695] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.429805] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.429808] pnp 00:0b: [mem 0x000c0000-0x000cffff]
[    0.429810] pnp 00:0b: [mem 0x000e0000-0x000fffff]
[    0.429815] pnp 00:0b: [mem 0x00100000-0xbfefffff]
[    0.429817] pnp 00:0b: [mem 0xfec00000-0xffffffff]
[    0.429868] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.429870] system 00:0b: [mem 0x000c0000-0x000cffff] has been reserved
[    0.429873] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.429876] system 00:0b: [mem 0x00100000-0xbfefffff] could not be reserved
[    0.429879] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.429881] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.430022] pnp: PnP ACPI: found 12 devices
[    0.430023] ACPI: ACPI bus type pnp unregistered
[    0.436242] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.436246] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.436249] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.436252] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.436256] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.436258] pci 0000:00:05.0:   bridge window [io  disabled]
[    0.436261] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.436263] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.436267] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.436269] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.436274] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.436277] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.436292] pci 0000:00:05.0: setting latency timer to 64
[    0.436300] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.436302] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.436305] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.436307] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.436309] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.436312] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.436314] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.436316] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]
[    0.436319] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.436321] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.436324] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.436326] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.436328] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.436331] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.436333] pci_bus 0000:03: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.436335] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.436373] NET: Registered protocol family 2
[    0.436565] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.438235] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.442228] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.442681] TCP: Hash tables configured (established 524288 bind 65536)
[    0.442684] TCP reno registered
[    0.442699] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.442750] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.442882] NET: Registered protocol family 1
[    0.585488] Freeing initrd memory: 12776k freed
[    0.590035] pci 0000:01:05.0: Boot video device
[    0.590043] PCI: CLS 64 bytes, default 64
[    0.590812] PCI-DMA: Disabling AGP.
[    0.590932] PCI-DMA: aperture base @ b4000000 size 65536 KB
[    0.590934] PCI-DMA: using GART IOMMU.
[    0.590938] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.594259] audit: initializing netlink socket (disabled)
[    0.594273] type=2000 audit(1310690356.590:1): initialized
[    0.607848] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.609711] VFS: Disk quotas dquot_6.5.2
[    0.609773] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.610461] fuse init (API version 7.16)
[    0.610564] msgmni has been set to 7412
[    0.610864] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.610904] io scheduler noop registered
[    0.610906] io scheduler deadline registered (default)
[    0.610953] io scheduler cfq registered
[    0.611138] pcieport 0000:00:05.0: setting latency timer to 64
[    0.611169] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    0.611243] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.611265] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.611402] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.680022] ACPI: Power Button [PWRB]
[    0.680070] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.680073] ACPI: Power Button [PWRF]
[    0.680225] ACPI: acpi_idle registered with cpuidle
[    0.682944] thermal LNXTHERM:00: registered as thermal_zone0
[    0.682946] ACPI: Thermal Zone [THRM] (30 C)
[    0.682987] ERST: Table is not found!
[    0.683085] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.703728] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.040712] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.041018] Linux agpgart interface v0.103
[    1.042186] brd: module loaded
[    1.042723] loop: module loaded
[    1.042836] i2c-core: driver [adp5520] using legacy suspend method
[    1.042838] i2c-core: driver [adp5520] using legacy resume method
[    1.043079] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.043117] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.043545] Fixed MDIO Bus: probed
[    1.043575] PPP generic driver version 2.4.2
[    1.043637] tun: Universal TUN/TAP device driver, 1.6
[    1.043639] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.043738] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.043790] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.043819] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.043873] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.080028] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.080047] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.080061] ehci_hcd 0000:00:12.2: debug port 1
[    1.080085] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff000
[    1.100027] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.100145] hub 1-0:1.0: USB hub found
[    1.100149] hub 1-0:1.0: 6 ports detected
[    1.100277] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.100289] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.100334] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.100365] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.100380] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.100392] ehci_hcd 0000:00:13.2: debug port 1
[    1.100412] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8f6800
[    1.120014] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.120113] hub 2-0:1.0: USB hub found
[    1.120116] hub 2-0:1.0: 6 ports detected
[    1.120210] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.120259] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.120271] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.120312] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.120360] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
[    1.184118] hub 3-0:1.0: USB hub found
[    1.184124] hub 3-0:1.0: 3 ports detected
[    1.184237] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.184250] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.184293] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.184331] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
[    1.244119] hub 4-0:1.0: USB hub found
[    1.244125] hub 4-0:1.0: 3 ports detected
[    1.244250] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.244261] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.244310] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.250056] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
[    1.314119] hub 5-0:1.0: USB hub found
[    1.314125] hub 5-0:1.0: 3 ports detected
[    1.314237] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.314249] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.314294] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.314331] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8f7000
[    1.374114] hub 6-0:1.0: USB hub found
[    1.374120] hub 6-0:1.0: 3 ports detected
[    1.374233] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.374244] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.374286] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.374324] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe8f5000
[    1.434108] hub 7-0:1.0: USB hub found
[    1.434114] hub 7-0:1.0: 2 ports detected
[    1.434194] uhci_hcd: USB Universal Host Controller Interface driver
[    1.434305] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.434659] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.434663] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.434734] mousedev: PS/2 mouse device common for all mice
[    1.434833] rtc_cmos 00:02: RTC can wake from S4
[    1.470062] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.470086] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.470186] device-mapper: uevent: version 1.0.3
[    1.470263] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.470346] device-mapper: multipath: version 1.2.0 loaded
[    1.470348] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.470487] cpuidle: using governor ladder
[    1.470489] cpuidle: using governor menu
[    1.470728] TCP cubic registered
[    1.470855] NET: Registered protocol family 10
[    1.471321] NET: Registered protocol family 17
[    1.471338] Registering the dns_resolver key type
[    1.471371] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4850B (2 cpu cores) (version 2.20.00)
[    1.471418] powernow-k8:    0 : fid 0x11 (2500 MHz), vid 0xe
[    1.471420] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xf
[    1.471422] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x11
[    1.471424] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x13
[    1.471425] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x15
[    1.471427] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x16
[    1.471582] PM: Hibernation image not present or could not be loaded.
[    1.471602] registered taskstats version 1
[    1.471808]   Magic number: 3:262:658
[    1.471823] block ram11: hash matches
[    1.471903] rtc_cmos 00:02: setting system clock to 2011-07-15 00:39:18 UTC (1310690358)
[    1.471906] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.471907] EDD information not available.
[    1.473484] Freeing unused kernel memory: 880k freed
[    1.473873] Write protecting the kernel read-only data: 10240k
[    1.474344] Freeing unused kernel memory: 104k freed
[    1.478995] Freeing unused kernel memory: 1416k freed
[    1.501955] <30>udev[96]: starting version 167
[    1.553953] Atheros(R) L2 Ethernet Driver - version 2.2.3
[    1.553956] Copyright (c) 2007 Atheros Corporation.
[    1.554044] ahci 0000:00:11.0: version 3.0
[    1.554073] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.554140] ahci 0000:00:11.0: irq 41 for MSI/MSI-X
[    1.554260] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.554264] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.558482] scsi0 : ahci
[    1.562301] scsi1 : ahci
[    1.567701] scsi2 : ahci
[    1.567837] scsi3 : ahci
[    1.571407] scsi4 : ahci
[    1.572755] scsi5 : ahci
[    1.572848] ata1: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff900 irq 41
[    1.572851] ata2: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff980 irq 41
[    1.572855] ata3: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa00 irq 41
[    1.572858] ata4: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa80 irq 41
[    1.572862] ata5: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffb00 irq 41
[    1.572865] ata6: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffb80 irq 41
[    1.577157] atl2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.577170] atl2 0000:02:00.0: setting latency timer to 64
[    1.578455] scsi6 : pata_atiixp
[    1.578555] scsi7 : pata_atiixp
[    1.579201] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.579204] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.920064] ata4: SATA link down (SStatus 0 SControl 300)
[    1.920098] ata6: SATA link down (SStatus 0 SControl 300)
[    1.920129] ata2: SATA link down (SStatus 0 SControl 300)
[    1.920158] ata5: SATA link down (SStatus 0 SControl 300)
[    2.120026] ata1: softreset failed (device not ready)
[    2.120029] ata1: applying SB600 PMP SRST workaround and retrying
[    2.180018] ata3: softreset failed (device not ready)
[    2.180021] ata3: applying SB600 PMP SRST workaround and retrying
[    2.320027] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.368423] ata1.00: ATA-7: ST3250820AS, 3.AAD, max UDMA/133
[    2.368426] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.380027] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.383399] ata3.00: ATA-8: WDC WD20EARS-00MVWB0, 50.0AB50, max UDMA/133
[    2.383401] ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.386424] ata3.00: configured for UDMA/133
[    2.426729] ata1.00: configured for UDMA/133
[    2.426861] scsi 0:0:0:0: Direct-Access     ATA      ST3250820AS      3.AA PQ: 0 ANSI: 5
[    2.427045] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.427074] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.427137] sd 0:0:0:0: [sda] Write Protect is off
[    2.427140] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.427161] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.427175] scsi 2:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 50.0 PQ: 0 ANSI: 5
[    2.427325] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.427399] sd 2:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.427470] sd 2:0:0:0: [sdb] Write Protect is off
[    2.427473] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.427492] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.455071]  sdb: sdb1
[    2.455342] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.563073]  sda: sda1 sda2 < sda5 >
[    2.563333] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.963826] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.576554] <30>udev[333]: starting version 167
[   13.604809] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.634091] lp: driver loaded but no devices found
[   13.662132] Adding 9936892k swap on /dev/sda5.  Priority:-1 extents:1 across:9936892k 
[   13.667362] MCE: In-kernel MCE decoding enabled.
[   13.703684] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   13.704674] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   13.704749] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   13.720348] EDAC MC: Ver: 2.1.0 Jul 14 2011
[   13.722957] EDAC amd64_edac: v3.3.0
[   13.728113] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   13.732571] EDAC amd64: DRAM ECC disabled.
[   13.732581] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   13.732582]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   13.732584]  (Note that use of the override may cause unknown side effects.)
[   13.751199] [drm] Initialized drm 1.1.0 20060810
[   13.858845] Bridge firewalling registered
[   13.868789] device eth0 entered promiscuous mode
[   13.870250] atl2 0000:02:00.0: irq 42 for MSI/MSI-X
[   13.870911] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.011159] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.033645] type=1400 audit(1310690371.053:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=488 comm="apparmor_parser"
[   14.033993] type=1400 audit(1310690371.053:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=488 comm="apparmor_parser"
[   14.034209] type=1400 audit(1310690371.053:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=488 comm="apparmor_parser"
[   14.035749] type=1400 audit(1310690371.053:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=563 comm="apparmor_parser"
[   14.036082] type=1400 audit(1310690371.053:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=563 comm="apparmor_parser"
[   14.036298] type=1400 audit(1310690371.053:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=563 comm="apparmor_parser"
[   14.037753] type=1400 audit(1310690371.053:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=633 comm="apparmor_parser"
[   14.038089] type=1400 audit(1310690371.053:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=633 comm="apparmor_parser"
[   14.038303] type=1400 audit(1310690371.053:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=633 comm="apparmor_parser"
[   14.056894] [drm] radeon defaulting to kernel modesetting.
[   14.056897] [drm] radeon kernel modesetting enabled.
[   14.058164] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.060787] [drm] initializing kernel modesetting (RS740 0x1002:0x796E 0x1019:0x2615).
[   14.060825] [drm] register mmio base: 0xFEAF0000
[   14.060827] [drm] register mmio size: 65536
[   14.061471] ATOM BIOS: ATI
[   14.061491] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[   14.061494] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[   14.061512] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.061514] [drm] Driver supports precise vblank timestamp query.
[   14.061525] [drm] radeon: irq initialized.
[   14.061703] [drm] Detected VRAM RAM=256M, BAR=256M
[   14.061708] [drm] RAM width 128bits DDR
[   14.063540] [TTM] Zone  kernel: Available graphics memory: 1898864 kiB.
[   14.063544] [TTM] Initializing pool allocator.
[   14.063568] [drm] radeon: 256M of VRAM memory ready
[   14.063571] [drm] radeon: 512M of GTT memory ready.
[   14.063598] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   14.067295] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   14.075018] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   14.075586] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.075641] br0: port 1(eth0) entering forwarding state
[   14.075643] br0: port 1(eth0) entering forwarding state
[   14.075767] radeon 0000:01:05.0: WB enabled
[   14.075845] [drm] Loading RS690/RS740 Microcode
[   14.081690] [drm] radeon: ring at 0x00000000A0001000
[   14.081710] [drm] ring test succeeded in 1 usecs
[   14.081827] [drm] radeon: ib pool ready.
[   14.081897] [drm] ib test succeeded in 0 usecs
[   14.081899] [drm] Enabling audio support
[   14.081907] failed to evaluate ATIF got AE_BAD_PARAMETER
[   14.082119] [drm] Radeon Display Connectors
[   14.082121] [drm] Connector 0:
[   14.082122] [drm]   VGA
[   14.082124] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[   14.082126] [drm]   Encoders:
[   14.082127] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   14.082129] [drm] Connector 1:
[   14.082130] [drm]   DVI-D
[   14.082131] [drm]   HPD2
[   14.082133] [drm]   DDC: 0x7e40 0x7e60 0x7e44 0x7e64 0x7e48 0x7e68 0x7e4c 0x7e6c
[   14.082134] [drm]   Encoders:
[   14.082136] [drm]     DFP2: INTERNAL_DDI
[   14.082137] [drm] Connector 2:
[   14.082138] [drm]   DVI-D
[   14.082140] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[   14.082141] [drm]   Encoders:
[   14.082142] [drm]     DFP3: INTERNAL_LVTM1
[   14.085703] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[   14.150726] input: HDA ATI SB Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input2
[   14.150833] input: HDA ATI SB Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input3
[   14.150895] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[   14.150952] input: HDA ATI SB Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[   14.151016] input: HDA ATI SB HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   14.159500] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 228
[   14.159509] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.159514] <3>03 01 01 03 00 01 0f 00 00 00 00 00 00 00 00 00  ................
[   14.159516] <3>00 03 01 01 7f 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.159518] <3>01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.159520] <3>00 00 00 00 03 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.159522] <3>01 01 01 01 01 01 7f 00 00 00 00 00 00 00 00 00  ................
[   14.159524] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.159526] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 1f  ................
[   14.159528] <3>00 01 01 7f 01 01 01 01 01 01 01 01 01 00 00 00  ................
[   14.159529] 
[   14.209623] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 117
[   14.209627] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.209630] <3>03 00 00 01 01 00 01 01 01 00 01 01 01 01 01 01  ................
[   14.209632] <3>01 01 01 01 01 01 01 01 01 00 00 00 00 00 00 01  ................
[   14.209634] <3>01 00 01 01 01 01 01 01 01 01 01 01 00 01 01 01  ................
[   14.209636] <3>01 01 00 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.209638] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.209640] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.209642] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.209644] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.209646] 
[   14.259699] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 10
[   14.259703] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.259706] <3>07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.259708] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.259710] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.259712] <3>00 00 01 01 01 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.259714] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.259716] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.259718] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.259720] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.259721] 
[   14.309754] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 112
[   14.309758] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   14.309761] <3>07 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.309763] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.309765] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.309767] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.309769] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.309771] <3>01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01  ................
[   14.309773] <3>01 01 01 01 01 01 01 01 01 01 00 00 00 00 00 00  ................
[   14.309775] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   14.309777] 
[   14.309780] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
[   14.309783] [drm] Radeon display connector DVI-D-1: No monitor connected or invalid EDID
[   14.311728] [drm] Radeon display connector DVI-D-2: No monitor connected or invalid EDID
[   14.406280] No connectors reported connected with modes
[   14.406284] [drm] Cannot find any crtc or sizes - going 1024x768
[   14.411878] [drm] fb mappable at 0xD0040000
[   14.411880] [drm] vram apper at 0xD0000000
[   14.411881] [drm] size 3145728
[   14.411882] [drm] fb depth is 24
[   14.411883] [drm]    pitch is 4096
[   14.412082] Console: switching to colour frame buffer device 128x48
[   14.417429] fb0: radeondrmfb frame buffer device
[   14.417431] drm: registered panic notifier
[   14.417438] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
[   14.640714] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.096056] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   15.228514] type=1400 audit(1310690372.243:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=803 comm="apparmor_parser"
[   15.497051] kvm: Nested Virtualization enabled
[   15.535852] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.596302] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.428448] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   24.070019] br0: no IPv6 routers present
[   24.950013] eth0: no IPv6 routers present
```


Looks like it works perfectly. Thanks, and great work!

Though i will probably re-enable the i2c setting and switch to the newest kernel.

---

### Post by rdratlos on 2011-07-15
> **Stephen_m64 said:**
> 
Looks like it works perfectly. Thanks, and great work!

Though i will probably re-enable the i2c setting and switch to the newest kernel.

You're welcome. Glad to have helped you. 

Sorry, but I missed the kernel update by Ubuntu. In the PPA you will find fixed kernel also for Ubuntu [2.6.38-10.46.]("https://launchpad.net/%7Erdratlos/+archive/ppa-asus-m2a-fix/+sourcepub/1818960/+listing-archive-extra")

I'll try to keep the PPA up to date with Ubuntu kernel releases, as long as the patch is not in upstream kernel.

---

### Post by rdratlos on 2011-07-29
> **JoeFriday49 said:**
> When the kernel patch is developed will it be applied to the older supported versions as well as the current versions?  I'm using 10.04 LTS and was just curious if this will come down the Update Manager or will it have to be added manually...

In Launchpad PPA you will find a 2.6.32 and 2.6.35 test kernel for Ubuntu lucid, where I've  included the Asus M2A-VM patch. Could you please test it and provide me  feedback? 

Test kernel installation procedure:
Add following two lines to file** /etc/apt/sources.list**:

```
deb [http://ppa.launchpad.net/rdratlos/ppa-asusfix/ubuntu](http://ppa.launchpad.net/rdratlos/ppa-asusfix/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/rdratlos/ppa-asusfix/ubuntu](http://ppa.launchpad.net/rdratlos/ppa-asusfix/ubuntu) lucid main 
```Add PPA key to your apt keyring:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 61B873BC
```     Add new test kernel version (2.6.32-33.71+lp722806v1 or 2.6.35-25.44~lucid1+lp722806v1):
```
sudo apt-get update
sudo apt-get upgrade
```After reboot please check dmesg for the correct kernel version and the  drm log entries. There should be four EDID dumps in the log after the  Radeon connectors list and then ... SILENCE. Good luck!
As soon as you have the new dmesg log, please post it.

---

### Post by Routhinator on 2011-08-05
Following this thread I have attempted the fixes included here, right up to updating to kernel 2.6.38-10, however there has been no success. I am still getting the following output every 5 seconds to the terminal and the logs, and my DRI performance is severely impacted. It's bad enough that ATI dumped my card, now this laptop is nearly useless except for facebook, and what good is that really?

dmesg:

```
[  529.976130] 
[  530.027643] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  530.027651] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.027659] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.027666] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.027673] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.027680] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.027686] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.027694] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.027700] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.027706] 
[  530.078488] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  530.078496] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.078503] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.078511] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.078517] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.078524] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.078531] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.078538] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.078545] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.078551] 
[  530.129056] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  530.129064] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.129072] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.129079] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.129086] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.129093] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.129100] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.129107] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.129114] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  530.129119] 
[  530.129131] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[  530.129140] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[  540.216543] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  540.216560] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  540.216568] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  540.216576] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  540.216582] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  540.216589] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  540.216596] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  540.216602] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  540.216609] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  .............
```

lspci -v:

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, 66MHz, medium devsel, latency 0
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: 8e200000-8e3fffff
	Prefetchable memory behind bridge: 0000000080000000-0000000087ffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc Device 7914 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=0a, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 8d200000-8e1fffff
	Prefetchable memory behind bridge: 0000000088000000-0000000088ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: 8c200000-8d1fffff
	Prefetchable memory behind bridge: 0000000089000000-000000008a0fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 8b100000-8c1fffff
	Prefetchable memory behind bridge: 000000008a100000-000000008b0fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	I/O ports at 7038 [size=8]
	I/O ports at 704c [size=4]
	I/O ports at 7030 [size=8]
	I/O ports at 7048 [size=4]
	I/O ports at 7010 [size=16]
	Memory at 8e409000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at 8e408000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
	Memory at 8e407000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at 8e406000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
	Memory at 8e405000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at 8e404000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at 8e409400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 7000 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, slow devsel, latency 64, IRQ 11
	Memory at 8e400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, fast devsel, latency 64, IRQ 11
	Memory at 80000000 (64-bit, prefetchable) [size=128M]
	Memory at 8e300000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 6000 [size=256]
	Memory at 8e200000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff68
	Flags: bus master, fast devsel, latency 0, IRQ 19
	I/O ports at 3000 [size=256]
	Memory at 89010000 (64-bit, prefetchable) [size=4K]
	Memory at 89000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 89020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7128
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 8b100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

```

So.. what next? Obviously since I have a laptop upgrading my video is a non-option. Well actually, upgrading anything is a non-option with the current state of the economy. I'd have to be nuts to spend money on hardware right now.

Really need to fix this.

---

### Post by rdratlos on 2011-08-06
> **Routhy said:**
> Following this thread I have attempted the fixes included here, right up to updating to kernel 2.6.38-10, however there has been no success. I am still getting the following output every 5 seconds to the terminal and the logs, and my DRI performance is severely impacted. It's bad enough that ATI dumped my card, now this laptop is nearly useless except for facebook, and what good is that really?

dmesg: ...

So.. what next? Obviously since I have a laptop upgrading my video is a non-option. Well actually, upgrading anything is a non-option with the current state of the economy. I'd have to be nuts to spend money on hardware right now.

Really need to fix this.

Funny that your dmesg has only zeros in the EDID dump. Usually, we see also some non-zero bytes. 
Please post the complete dmesg after reboot of your laptop. Then I will try to add your laptop to the kernel patch.

Did you try this: [http://ubuntuforums.org/showthread.php?t=1607778](http://ubuntuforums.org/showthread.php?t=1607778)?

---

### Post by Routhinator on 2011-08-06
I thought that was very odd as well, especially since that's not the results from i2C. i2C detects the monitor attached to adapter 3 with a proper edid.


dmesg after reboot: (as much of it as the backlog would let me grab)

```
...
[   58.011753] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.011756] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.011759] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.011762] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.011764] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.011767] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.011769] 
[   58.061738] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   58.061741] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.061744] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.061747] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.061750] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.061753] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.061794] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.061797] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.061800] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.061802] 
[   58.111690] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   58.111693] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.111696] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.111700] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.111703] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.111706] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.111708] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.111712] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.111715] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.111717] 
[   58.111720] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   58.111723] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   58.165407] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   58.165415] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.165418] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.165421] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.165424] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.165427] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.165430] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.165433] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.165436] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.165438] 
[   58.215512] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   58.215516] <3>00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.215519] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.215522] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.215525] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.215528] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.215530] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.215533] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.215536] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.215538] 
[   58.265297] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   58.265300] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.265303] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.265306] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.265309] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.265312] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.265316] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.265319] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.265322] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.265324] 
[   58.315052] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   58.315055] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.315058] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.315062] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.315064] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.315067] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.315070] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.315073] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.315076] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   58.315078] 
[   58.315083] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   58.315087] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   64.144030] wlan0: no IPv6 routers present
[   67.991102] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   67.991110] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   67.991113] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   67.991116] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   67.991119] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   67.991122] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   67.991125] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   67.991128] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   67.991131] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   67.991133] 
[   68.041129] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   68.041132] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.041135] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.041139] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.041141] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.041144] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.041147] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.041150] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.041153] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.041155] 
[   68.090996] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   68.090999] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.091002] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.091005] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.091008] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.091011] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.091014] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.091016] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.091019] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.091021] 
[   68.140925] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   68.140928] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.140931] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.140934] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.140937] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.140940] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.140943] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.140946] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.140948] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   68.140951] 
[   68.140955] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   68.140958] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   78.231084] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   78.231091] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.231095] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.231098] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.231101] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.231103] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.231106] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.231109] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.231112] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.231114] 
[   78.281029] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   78.281032] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.281035] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.281038] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.281041] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.281044] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.281047] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.281050] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.281053] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.281055] 
[   78.330842] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   78.330845] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.330848] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.330851] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.330854] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.330857] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.330860] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.330862] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.330865] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.330867] 
[   78.380751] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   78.380755] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.380758] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.380761] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.380764] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.380767] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.380770] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.380773] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.380775] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   78.380778] 
[   78.380782] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   78.380785] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   88.499185] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   88.499206] <3>00 00 00 1f 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.499214] <3>00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.499221] <3>00 00 00 00 00 00 00 00 00 00 07 00 00 00 00 00  ................
[   88.499228] <3>00 00 0f 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.499235] <3>00 00 00 ff 00 00 00 00 00 00 00 00 00 0f 00 00  ................
[   88.499242] <3>00 00 00 00 00 00 00 7f 00 00 00 00 00 00 00 00  ................
[   88.499248] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.499255] <3>00 00 00 00 00 7f 00 00 00 00 00 00 00 00 00 00  ................
[   88.499260] 
[   88.560434] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 81
[   88.560447] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   88.560456] <3>01 00 00 ff 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.560464] <3>00 00 00 00 00 3f 00 00 00 00 00 00 00 00 00 00  .....?..........
[   88.560471] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.560477] <3>00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.560484] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 0f 00  ................
[   88.560490] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.560497] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.560504] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.560509] 
[   88.629692] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 209
[   88.629706] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   88.629716] <3>ff 01 0f 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.629723] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.629730] <3>00 00 00 7f 00 00 00 00 00 00 3f 00 00 00 00 00  ..........?.....
[   88.629737] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 03 00 00  ................
[   88.629744] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.629751] <3>00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.629757] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.629764] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.629769] 
[   88.683580] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   88.683597] <3>00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.683605] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.683612] <3>00 00 00 00 01 00 00 00 00 01 00 00 00 00 00 00  ................
[   88.683618] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.683625] <3>00 00 00 00 0f 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.683632] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.683639] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   88.683646] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 01 00 00  ................
[   88.683651] 
[   88.683663] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   88.683672] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   91.042592] exe (2195): /proc/2195/oom_adj is deprecated, please use /proc/2195/oom_score_adj instead.
[   98.744226] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   98.744242] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.744250] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.744257] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.744264] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.744271] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.744277] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.744284] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.744291] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.744296] 
[   98.795046] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   98.795054] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.795062] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.795069] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.795076] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.795083] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.795090] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.795097] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.795104] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.795110] 
[   98.845863] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   98.845871] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.845879] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.845886] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.845892] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.845899] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.845906] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.845913] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.845920] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.845925] 
[   98.896903] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   98.896911] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.896918] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.896926] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.896933] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.896940] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.896947] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.896954] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.896961] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.896966] 
[   98.896977] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   98.896986] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[  108.985597] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  108.985613] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  108.985621] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  108.985629] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  108.985636] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 01  ................
[  108.985643] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  108.985650] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  108.985657] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  108.985664] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  108.985669] 
[  109.038109] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  109.038120] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.038128] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 01  ................
[  109.038134] <3>00 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00  ................
[  109.038141] <3>00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00  ................
[  109.038148] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.038155] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.038161] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.038168] <3>00 00 00 00 00 00 01 00 00 00 00 00 00 00 00 00  ................
[  109.038173] 
[  109.090794] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  109.090803] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.090810] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.090817] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.090823] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 03 00 00  ................
[  109.090830] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.090837] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.090844] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.090850] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.090855] 
[  109.141404] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  109.141411] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.141418] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.141426] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.141432] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.141439] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.141446] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.141453] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.141460] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  109.141465] 
[  109.141476] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[  109.141485] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID

```

I2C output:

```
routh@ashley-laptop ~ $ sudo i2cdetect -l
[sudo] password for routh: 
i2c-0	i2c       	Radeon i2c bit bus 0xc0         	I2C adapter
i2c-1	i2c       	Radeon i2c bit bus 0x90         	I2C adapter
i2c-2	i2c       	Radeon i2c bit bus 0x91         	I2C adapter
i2c-3	i2c       	Radeon i2c bit bus 0x92         	I2C adapter
i2c-4	smbus     	SMBus PIIX4 adapter at 0b00     	SMBus adapter
routh@ashley-laptop ~ $ sudo i2cdetect 1
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-1.
I will probe address range 0x03-0x77.
Continue? [Y/n] 
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --                         
routh@ashley-laptop ~ $ sudo i2cdetect 2
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-2.
I will probe address range 0x03-0x77.
Continue? [Y/n] 
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: 50 -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --                         
routh@ashley-laptop ~ $ sudo i2cdetect 3
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-3.
I will probe address range 0x03-0x77.
Continue? [Y/n] 
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          03 04 05 06 07 08 09 0a 0b 0c 0d 0e 0f 
10: 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 
20: 20 21 22 23 24 25 26 27 28 29 2a 2b 2c 2d 2e 2f 
30: 30 31 32 33 34 35 36 37 38 39 3a 3b 3c 3d 3e 3f 
40: 40 41 42 43 44 45 46 47 48 49 4a 4b 4c 4d 4e 4f 
50: 50 51 52 53 54 55 56 57 58 59 5a 5b 5c 5d 5e 5f 
60: 60 61 62 63 64 65 66 67 68 69 6a 6b 6c 6d 6e 6f 
70: 70 71 72 73 74 75 76 77                         
routh@ashley-laptop ~ $ sudo i2cdetect 4
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-4.
I will probe address range 0x03-0x77.
Continue? [Y/n] 
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- 38 -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: 50 -- 52 -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- 69 -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --                         
routh@ashley-laptop ~ $ 

```


Is it just me or does it look like the kernel is only trying one of these every time??

---

### Post by rdratlos on 2011-08-06
> **Routhy said:**
> I thought that was very odd as well, especially since that's not the results from i2C. i2C detects the monitor attached to adapter 3 with a proper edid.


dmesg after reboot: (as much of it as the backlog would let me grab)

Is it just me or does it look like the kernel is only trying one of these every time??

Would it be possible for you, to get somehow the dmesg from the beginning. I would like to check the drm and radeon information during setup, before I start any kernel patch work. If you can't get it using the dmesg command copy and paste the kernel messages directly from the /var/log/dmesg or from /var/log/messages.

---

### Post by Routhinator on 2011-08-06
> **rdratlos said:**
> Would it be possible for you, to get somehow the dmesg from the beginning. I would like to check the drm and radeon information during setup, before I start any kernel patch work. If you can't get it using the dmesg command copy and paste the kernel messages directly from the /var/log/dmesg or from /var/log/messages.

Ok, I had to hit the /var/log/dmesg because even after a fresh boot and outputting the dmesg results to a txt file there was too much output and it was still being cut off at about 5.xxxx

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-10-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 (Ubuntu 2.6.38-10.46-generic 2.6.38.7)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077c0d000 (usable)
[    0.000000]  BIOS-e820: 0000000077c0d000 - 0000000077cb8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077cb8000 - 0000000077cf0000 (usable)
[    0.000000]  BIOS-e820: 0000000077cf0000 - 0000000077cf1000 (reserved)
[    0.000000]  BIOS-e820: 0000000077cf1000 - 0000000077d30000 (usable)
[    0.000000]  BIOS-e820: 0000000077d30000 - 0000000077d33000 (reserved)
[    0.000000]  BIOS-e820: 0000000077d33000 - 0000000077dbb000 (usable)
[    0.000000]  BIOS-e820: 0000000077dbb000 - 0000000077dbf000 (reserved)
[    0.000000]  BIOS-e820: 0000000077dbf000 - 0000000077e85000 (usable)
[    0.000000]  BIOS-e820: 0000000077e85000 - 0000000077ebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077ebf000 - 0000000077eef000 (usable)
[    0.000000]  BIOS-e820: 0000000077eef000 - 0000000077eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077eff000 - 0000000077f00000 (usable)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: TOSHIBA Satellite L300D/, BIOS 1.70    09/16/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x77f00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00FFF00000 mask FFFFF00000 write-protect
[    0.000000]   1 base 0000000000 mask FFC0000000 write-back
[    0.000000]   2 base 0040000000 mask FFE0000000 write-back
[    0.000000]   3 base 0060000000 mask FFF0000000 write-back
[    0.000000]   4 base 0070000000 mask FFF8000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35c9a000 - 36e45000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 TOSINV)
[    0.000000] ACPI: XSDT 77efe120 0005C (v01 TOSINV TOSINV00 00000003      01000013)
[    0.000000] ACPI: FACP 77efd000 000F4 (v04 TOSINV TOSINV00 00000003 MSFT 01000013)
[    0.000000] ACPI: DSDT 77ef2000 071F8 (v01 TOSINV TOSINV00 F0000000 MSFT 01000013)
[    0.000000] ACPI: FACS 77e8e000 00040
[    0.000000] ACPI: HPET 77efc000 00038 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 77efb000 00084 (v02 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 77efa000 0003C (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 77ef1000 00176 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 77ef0000 00028 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 77eef000 00210 (v01 AMD    PowerNow 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1031MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00077f00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00077c0d
[    0.000000]     0: 0x00077cb8 -> 0x00077cf0
[    0.000000]     0: 0x00077cf1 -> 0x00077d30
[    0.000000]     0: 0x00077d33 -> 0x00077dbb
[    0.000000]     0: 0x00077dbf -> 0x00077e85
[    0.000000]     0: 0x00077ebf -> 0x00077eef
[    0.000000]     0: 0x00077eff -> 0x00077f00
[    0.000000] On node 0 totalpages: 490898
[    0.000000] free_area_init_node: node 0, pgdat c1784140, node_mem_map f4d9a200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2063 pages used for memmap
[    0.000000]   HighMem zone: 261622 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 77f00000 (gap: 77f00000:7c100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487059
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=32b6c5c5-2114-4113-a197-b230bc6543dd ro noapic
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9824960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00077f00)
[    0.000000] Memory: 1910124k/1965056k available (5190k kernel code, 53468k reserved, 2539k data, 700k init, 1054740k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc1511841 - 0xc178c4c0   (2539 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1511841   (5190 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:304 16
[    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1895.403 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 3790.80 BogoMIPS (lpj=7581612)
[    0.004032] pid_max: default: 32768 minimum: 301
[    0.004072] Security Framework initialized
[    0.004100] AppArmor: AppArmor initialized
[    0.004107] Yama: becoming mindful.
[    0.008048] Mount-cache hash table entries: 512
[    0.008229] Initializing cgroup subsys ns
[    0.008239] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.008254] Initializing cgroup subsys cpuacct
[    0.008266] Initializing cgroup subsys memory
[    0.008282] Initializing cgroup subsys devices
[    0.008292] Initializing cgroup subsys freezer
[    0.008300] Initializing cgroup subsys net_cls
[    0.008309] Initializing cgroup subsys blkio
[    0.008355] CPU: Physical Processor ID: 0
[    0.008363] CPU: Processor Core ID: 0
[    0.008371] mce: CPU supports 5 MCE banks
[    0.008389] using C1E aware idle routine
[    0.011181] ACPI: Core revision 20110112
[    0.011195] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.011354] ACPI: Forced DSDT copy: length 0x071F8 copied locally, original unmapped
[    0.018669] ACPI: setting ELCR to 0200 (from 0c20)
[    0.020039] ftrace: allocating 23648 entries in 47 pages
[    0.024087] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.024104] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[    0.028001] Performance Events: AMD PMU driver.
[    0.028001] ... version:                0
[    0.028001] ... bit width:              48
[    0.028001] ... generic registers:      4
[    0.028001] ... value mask:             0000ffffffffffff
[    0.028001] ... max period:             00007fffffffffff
[    0.028001] ... fixed-purpose events:   0
[    0.028001] ... event mask:             000000000000000f
[    0.028001] CPU 1 irqstacks, hard=f40d8000 soft=f40da000
[    0.028001] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.008000] System has AMD C1E enabled
[    0.112074] Switch to broadcast mode on CPU1
[    0.112077] Brought up 2 CPUs
[    0.112080] Total of 2 processors activated (7581.34 BogoMIPS).
[    0.112411] Switch to broadcast mode on CPU0
[    0.112411] devtmpfs: initialized
[    0.113495] print_constraints: dummy: 
[    0.113539] Time: 15:18:53  Date: 08/06/11
[    0.113592] NET: Registered protocol family 16
[    0.113648] Trying to unpack rootfs image as initramfs...
[    0.113772] EISA bus registered
[    0.113787] TOM: 0000000080000000 aka 2048M
[    0.113802] ACPI: bus type pci registered
[    0.113893] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
[    0.113906] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
[    0.113913] PCI: Using MMCONFIG for extended config space
[    0.113919] PCI: Using configuration type 1 for base access
[    0.115258] bio: create slab <bio-0> at 0
[    0.117622] ACPI: EC: Look up EC in DSDT
[    0.119278] ACPI: Executed 1 blocks of module-level executable AML code
[    0.646893] Freeing initrd memory: 18092k freed
[    2.596231] ACPI: Interpreter enabled
[    2.596245] ACPI: (supports S0 S3 S4 S5)
[    2.596284] ACPI: Using PIC for interrupt routing
[    2.617761] ACPI: Power Resource [PFA1] (off)
[    2.618202] ACPI: EC: GPE = 0x7, I/O: command/status = 0x66, data = 0x62
[    2.632332] ACPI: No dock devices found.
[    2.632340] HEST: Table not found.
[    2.632348] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    2.632898] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    2.633968] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    2.633977] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    2.633986] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    2.633995] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    2.634005] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    2.634014] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    2.634024] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    2.634033] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    2.634042] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    2.634052] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    2.634061] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    2.634070] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    2.634080] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    2.634089] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    2.634099] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    2.634108] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xf3ffffff]
[    2.634118] pci_root PNP0A08:00: host bridge window [mem 0xf8000000-0xffffffff]
[    2.634127] pci_root PNP0A08:00: host bridge window [mem 0xfff00000-0xffffffff]
[    2.634140] pci_root PNP0A08:00: host bridge window expanded to [mem 0xf8000000-0xffffffff]; [mem 0xfff00000-0xffffffff] ignored
[    2.634156] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000cd7ff]
[    2.634181] pci 0000:00:00.0: [1002:7910] type 0 class 0x000600
[    2.634220] pci 0000:00:01.0: [1002:7912] type 1 class 0x000604
[    2.634271] pci 0000:00:04.0: [1002:7914] type 1 class 0x000604
[    2.634308] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    2.634312] pci 0000:00:04.0: PME# disabled
[    2.634331] pci 0000:00:05.0: [1002:7915] type 1 class 0x000604
[    2.634367] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    2.634371] pci 0000:00:05.0: PME# disabled
[    2.634390] pci 0000:00:06.0: [1002:7916] type 1 class 0x000604
[    2.634427] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    2.634431] pci 0000:00:06.0: PME# disabled
[    2.634473] pci 0000:00:12.0: [1002:4380] type 0 class 0x000101
[    2.634496] pci 0000:00:12.0: reg 10: [io  0x7038-0x703f]
[    2.634509] pci 0000:00:12.0: reg 14: [io  0x704c-0x704f]
[    2.634522] pci 0000:00:12.0: reg 18: [io  0x7030-0x7037]
[    2.634535] pci 0000:00:12.0: reg 1c: [io  0x7048-0x704b]
[    2.634548] pci 0000:00:12.0: reg 20: [io  0x7010-0x701f]
[    2.634561] pci 0000:00:12.0: reg 24: [mem 0x8e409000-0x8e4093ff]
[    2.634588] pci 0000:00:12.0: set SATA to AHCI mode
[    2.634627] pci 0000:00:13.0: [1002:4387] type 0 class 0x000c03
[    2.634645] pci 0000:00:13.0: reg 10: [mem 0x8e408000-0x8e408fff]
[    2.634726] pci 0000:00:13.1: [1002:4388] type 0 class 0x000c03
[    2.634744] pci 0000:00:13.1: reg 10: [mem 0x8e407000-0x8e407fff]
[    2.634825] pci 0000:00:13.2: [1002:4389] type 0 class 0x000c03
[    2.634843] pci 0000:00:13.2: reg 10: [mem 0x8e406000-0x8e406fff]
[    2.634923] pci 0000:00:13.3: [1002:438a] type 0 class 0x000c03
[    2.634941] pci 0000:00:13.3: reg 10: [mem 0x8e405000-0x8e405fff]
[    2.635022] pci 0000:00:13.4: [1002:438b] type 0 class 0x000c03
[    2.635040] pci 0000:00:13.4: reg 10: [mem 0x8e404000-0x8e404fff]
[    2.635128] pci 0000:00:13.5: [1002:4386] type 0 class 0x000c03
[    2.635152] pci 0000:00:13.5: reg 10: [mem 0x8e409400-0x8e4094ff]
[    2.635241] pci 0000:00:13.5: supports D1 D2
[    2.635243] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    2.635249] pci 0000:00:13.5: PME# disabled
[    2.635276] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    2.635304] pci 0000:00:14.0: reg 10: [io  0x0b00-0x0b0f]
[    2.635398] pci 0000:00:14.1: [1002:438c] type 0 class 0x000101
[    2.635416] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    2.635429] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    2.635442] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    2.635454] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    2.635467] pci 0000:00:14.1: reg 20: [io  0x7000-0x700f]
[    2.635513] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    2.635541] pci 0000:00:14.2: reg 10: [mem 0x8e400000-0x8e403fff 64bit]
[    2.635616] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    2.635621] pci 0000:00:14.2: PME# disabled
[    2.635641] pci 0000:00:14.3: [1002:438d] type 0 class 0x000601
[    2.635734] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    2.635792] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    2.635821] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    2.635846] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    2.635872] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    2.635939] pci 0000:01:05.0: [1002:791f] type 0 class 0x000300
[    2.635953] pci 0000:01:05.0: reg 10: [mem 0x80000000-0x87ffffff 64bit pref]
[    2.635963] pci 0000:01:05.0: reg 18: [mem 0x8e300000-0x8e30ffff 64bit]
[    2.635971] pci 0000:01:05.0: reg 20: [io  0x6000-0x60ff]
[    2.635979] pci 0000:01:05.0: reg 24: [mem 0x8e200000-0x8e2fffff]
[    2.635996] pci 0000:01:05.0: supports D1 D2
[    2.636018] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.636029] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
[    2.636033] pci 0000:00:01.0:   bridge window [mem 0x8e200000-0x8e3fffff]
[    2.636039] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x87ffffff 64bit pref]
[    2.636073] pci 0000:00:04.0: PCI bridge to [bus 09-0a]
[    2.636083] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
[    2.636087] pci 0000:00:04.0:   bridge window [mem 0x8d200000-0x8e1fffff]
[    2.636093] pci 0000:00:04.0:   bridge window [mem 0x88000000-0x88ffffff 64bit pref]
[    2.636142] pci 0000:03:00.0: [10ec:8136] type 0 class 0x000200
[    2.636174] pci 0000:03:00.0: reg 10: [io  0x3000-0x30ff]
[    2.636201] pci 0000:03:00.0: reg 18: [mem 0x89010000-0x89010fff 64bit pref]
[    2.636219] pci 0000:03:00.0: reg 20: [mem 0x89000000-0x8900ffff 64bit pref]
[    2.636232] pci 0000:03:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    2.636268] pci 0000:03:00.0: supports D1 D2
[    2.636271] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.636277] pci 0000:03:00.0: PME# disabled
[    2.644184] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    2.644194] pci 0000:00:05.0:   bridge window [io  0x3000-0x4fff]
[    2.644199] pci 0000:00:05.0:   bridge window [mem 0x8c200000-0x8d1fffff]
[    2.644205] pci 0000:00:05.0:   bridge window [mem 0x89000000-0x8a0fffff 64bit pref]
[    2.644258] pci 0000:04:00.0: [168c:001c] type 0 class 0x000200
[    2.644280] pci 0000:04:00.0: reg 10: [mem 0x8b100000-0x8b10ffff 64bit]
[    2.644379] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    2.644398] pci 0000:00:06.0: PCI bridge to [bus 04-04]
[    2.644408] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    2.644412] pci 0000:00:06.0:   bridge window [mem 0x8b100000-0x8c1fffff]
[    2.644418] pci 0000:00:06.0:   bridge window [mem 0x8a100000-0x8b0fffff 64bit pref]
[    2.644496] pci 0000:00:14.4: PCI bridge to [bus 80-8f] (subtractive decode)
[    2.644508] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    2.644515] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.644521] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.644525] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    2.644529] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    2.644532] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    2.644536] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    2.644540] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    2.644544] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    2.644547] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    2.644551] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    2.644555] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    2.644558] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    2.644562] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    2.644566] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    2.644570] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    2.644573] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    2.644577] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xf3ffffff] (subtractive decode)
[    2.644581] pci 0000:00:14.4:   bridge window [mem 0xf8000000-0xffffffff] (subtractive decode)
[    2.644604] pci_bus 0000:00: on NUMA node 0
[    2.644609] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.644714] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    2.644772] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    2.644837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    2.644899] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    2.644995] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    2.645039]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    2.651517] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    2.651583] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[    2.651644] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[    2.651705] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[    2.651766] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.651830] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.651895] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *10 11 12 14 15)
[    2.651956] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.652110] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    2.652122] vgaarb: loaded
[    2.652419] SCSI subsystem initialized
[    2.652449] libata version 3.00 loaded.
[    2.652449] usbcore: registered new interface driver usbfs
[    2.652449] usbcore: registered new interface driver hub
[    2.652449] usbcore: registered new device driver usb
[    2.652449] wmi: Mapper loaded
[    2.652449] PCI: Using ACPI for IRQ routing
[    2.652449] PCI: pci_cache_line_size set to 64 bytes
[    2.652449] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    2.652449] reserve RAM buffer: 0000000077c0d000 - 0000000077ffffff 
[    2.652449] reserve RAM buffer: 0000000077cf0000 - 0000000077ffffff 
[    2.652449] reserve RAM buffer: 0000000077d30000 - 0000000077ffffff 
[    2.652449] reserve RAM buffer: 0000000077dbb000 - 0000000077ffffff 
[    2.652449] reserve RAM buffer: 0000000077e85000 - 0000000077ffffff 
[    2.652449] reserve RAM buffer: 0000000077eef000 - 0000000077ffffff 
[    2.652449] reserve RAM buffer: 0000000077f00000 - 0000000077ffffff 
[    2.652563] NetLabel: Initializing
[    2.652569] NetLabel:  domain hash size = 128
[    2.652575] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.652595] NetLabel:  unlabeled traffic allowed by default
[    2.652670] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    2.652682] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    2.654734] Switching to clocksource hpet
[    2.654741] Switched to NOHz mode on CPU #0
[    2.654754] Switched to NOHz mode on CPU #1
[    2.661562] AppArmor: AppArmor Filesystem Enabled
[    2.661609] pnp: PnP ACPI init
[    2.661634] ACPI: bus type pnp registered
[    2.662431] pnp 00:00: [bus 00-ff]
[    2.662435] pnp 00:00: [io  0x0000-0x0cf7 window]
[    2.662438] pnp 00:00: [io  0x0d00-0xffff window]
[    2.662442] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    2.662445] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    2.662448] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    2.662451] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    2.662455] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    2.662458] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    2.662461] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    2.662464] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    2.662467] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    2.662470] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    2.662473] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    2.662476] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    2.662480] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    2.662483] pnp 00:00: [mem 0x80000000-0xf3ffffff window]
[    2.662486] pnp 00:00: [mem 0xf8000000-0xffffffff window]
[    2.662489] pnp 00:00: [io  0x0cf8-0x0cff]
[    2.662492] pnp 00:00: [mem 0xfff00000-0xffffffff]
[    2.662567] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    2.662670] pnp 00:01: [io  0x0000-0x000f]
[    2.662674] pnp 00:01: [io  0x0081-0x008f]
[    2.662676] pnp 00:01: [io  0x00c0-0x00df]
[    2.662680] pnp 00:01: [dma 4]
[    2.662720] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    2.662732] pnp 00:02: [io  0x00f0-0x00fe]
[    2.662736] pnp 00:02: [irq 13]
[    2.662773] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    2.662808] pnp 00:03: [io  0x0070-0x0071]
[    2.662811] pnp 00:03: [irq 8]
[    2.662850] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.662861] pnp 00:04: [io  0x0061]
[    2.662902] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    2.662915] pnp 00:05: [io  0x0060]
[    2.662918] pnp 00:05: [io  0x0064]
[    2.662921] pnp 00:05: [irq 1]
[    2.662959] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    2.662970] pnp 00:06: [irq 12]
[    2.663010] pnp 00:06: Plug and Play ACPI device, IDs SYN1913 SYN1900 SYN0002 PNP0f13 (active)
[    2.663028] pnp 00:07: [io  0x0010-0x001f]
[    2.663031] pnp 00:07: [io  0x002e-0x002f]
[    2.663034] pnp 00:07: [io  0x0068]
[    2.663037] pnp 00:07: [io  0x006c]
[    2.663040] pnp 00:07: [io  0x0072-0x0073]
[    2.663043] pnp 00:07: [io  0x0080]
[    2.663045] pnp 00:07: [io  0x00b0-0x00b1]
[    2.663048] pnp 00:07: [io  0x0092]
[    2.663051] pnp 00:07: [io  0x0400-0x04cf]
[    2.663054] pnp 00:07: [io  0x04d0-0x04d1]
[    2.663057] pnp 00:07: [io  0x04d6]
[    2.663060] pnp 00:07: [io  0x05a0-0x05bf]
[    2.663063] pnp 00:07: [io  0x0680-0x06ff]
[    2.663066] pnp 00:07: [io  0x077a]
[    2.663069] pnp 00:07: [io  0x0c00-0x0c01]
[    2.663072] pnp 00:07: [io  0x0c14]
[    2.663074] pnp 00:07: [io  0x0c50-0x0c52]
[    2.663077] pnp 00:07: [io  0x0c6c]
[    2.663080] pnp 00:07: [io  0x0c6f]
[    2.663083] pnp 00:07: [io  0x0cd0-0x0cdb]
[    2.663086] pnp 00:07: [io  0x0022-0x0023]
[    2.663089] pnp 00:07: [io  0x0800-0x087f]
[    2.663092] pnp 00:07: [io  0x0b10-0x0b1f]
[    2.663097] pnp 00:07: [io  0x0cdc-0x0cdf]
[    2.663100] pnp 00:07: [mem 0xff800100-0xff80017f]
[    2.663213] system 00:07: [io  0x0400-0x04cf] has been reserved
[    2.663223] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    2.663231] system 00:07: [io  0x04d6] has been reserved
[    2.663239] system 00:07: [io  0x05a0-0x05bf] has been reserved
[    2.663246] system 00:07: [io  0x0680-0x06ff] has been reserved
[    2.663254] system 00:07: [io  0x077a] has been reserved
[    2.663262] system 00:07: [io  0x0c00-0x0c01] has been reserved
[    2.663270] system 00:07: [io  0x0c14] has been reserved
[    2.663278] system 00:07: [io  0x0c50-0x0c52] has been reserved
[    2.663286] system 00:07: [io  0x0c6c] has been reserved
[    2.663293] system 00:07: [io  0x0c6f] has been reserved
[    2.663301] system 00:07: [io  0x0cd0-0x0cdb] has been reserved
[    2.663309] system 00:07: [io  0x0800-0x087f] has been reserved
[    2.663317] system 00:07: [io  0x0b10-0x0b1f] has been reserved
[    2.663325] system 00:07: [io  0x0cdc-0x0cdf] has been reserved
[    2.663335] system 00:07: [mem 0xff800100-0xff80017f] has been reserved
[    2.663344] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.663611] pnp 00:08: [mem 0x00000000-0x0009ffff]
[    2.663614] pnp 00:08: [mem 0x000ec000-0x000fffff]
[    2.663617] pnp 00:08: [mem 0x00100000-0x7fffffff]
[    2.663620] pnp 00:08: [mem 0xf4000000-0xf7ffffff]
[    2.663623] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    2.663626] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    2.663696] system 00:08: [mem 0x00000000-0x0009ffff] could not be reserved
[    2.663706] system 00:08: [mem 0x000ec000-0x000fffff] could not be reserved
[    2.663715] system 00:08: [mem 0x00100000-0x7fffffff] could not be reserved
[    2.663723] system 00:08: [mem 0xf4000000-0xf7ffffff] has been reserved
[    2.663732] system 00:08: [mem 0xfec00000-0xfec00fff] has been reserved
[    2.663741] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    2.663749] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.664169] pnp: PnP ACPI: found 9 devices
[    2.664176] ACPI: ACPI bus type pnp unregistered
[    2.664183] PnPBIOS: Disabled by ACPI PNP
[    2.701064] pci 0000:03:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    2.701111] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.701119] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
[    2.701128] pci 0000:00:01.0:   bridge window [mem 0x8e200000-0x8e3fffff]
[    2.701137] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x87ffffff 64bit pref]
[    2.701148] pci 0000:00:04.0: PCI bridge to [bus 09-0a]
[    2.701156] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
[    2.701166] pci 0000:00:04.0:   bridge window [mem 0x8d200000-0x8e1fffff]
[    2.701175] pci 0000:00:04.0:   bridge window [mem 0x88000000-0x88ffffff 64bit pref]
[    2.701191] pci 0000:03:00.0: BAR 6: assigned [mem 0x89020000-0x8903ffff pref]
[    2.701201] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    2.701208] pci 0000:00:05.0:   bridge window [io  0x3000-0x4fff]
[    2.701217] pci 0000:00:05.0:   bridge window [mem 0x8c200000-0x8d1fffff]
[    2.701225] pci 0000:00:05.0:   bridge window [mem 0x89000000-0x8a0fffff 64bit pref]
[    2.701237] pci 0000:00:06.0: PCI bridge to [bus 04-04]
[    2.701244] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    2.701253] pci 0000:00:06.0:   bridge window [mem 0x8b100000-0x8c1fffff]
[    2.701261] pci 0000:00:06.0:   bridge window [mem 0x8a100000-0x8b0fffff 64bit pref]
[    2.701273] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
[    2.701285] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    2.701296] pci 0000:00:14.4:   bridge window [mem disabled]
[    2.701305] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    2.701323] pci 0000:00:01.0: setting latency timer to 64
[    2.701330] pci 0000:00:04.0: setting latency timer to 64
[    2.701336] pci 0000:00:05.0: setting latency timer to 64
[    2.701342] pci 0000:00:06.0: setting latency timer to 64
[    2.701351] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.701354] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.701358] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.701361] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.701364] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.701368] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.701372] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    2.701375] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    2.701379] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    2.701382] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    2.701385] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    2.701389] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    2.701392] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    2.701396] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    2.701399] pci_bus 0000:00: resource 18 [mem 0x80000000-0xf3ffffff]
[    2.701402] pci_bus 0000:00: resource 19 [mem 0xf8000000-0xffffffff]
[    2.701406] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
[    2.701409] pci_bus 0000:01: resource 1 [mem 0x8e200000-0x8e3fffff]
[    2.701413] pci_bus 0000:01: resource 2 [mem 0x80000000-0x87ffffff 64bit pref]
[    2.701417] pci_bus 0000:09: resource 0 [io  0x5000-0x5fff]
[    2.701420] pci_bus 0000:09: resource 1 [mem 0x8d200000-0x8e1fffff]
[    2.701424] pci_bus 0000:09: resource 2 [mem 0x88000000-0x88ffffff 64bit pref]
[    2.701427] pci_bus 0000:03: resource 0 [io  0x3000-0x4fff]
[    2.701430] pci_bus 0000:03: resource 1 [mem 0x8c200000-0x8d1fffff]
[    2.701434] pci_bus 0000:03: resource 2 [mem 0x89000000-0x8a0fffff 64bit pref]
[    2.701438] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    2.701441] pci_bus 0000:04: resource 1 [mem 0x8b100000-0x8c1fffff]
[    2.701445] pci_bus 0000:04: resource 2 [mem 0x8a100000-0x8b0fffff 64bit pref]
[    2.701448] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
[    2.701452] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
[    2.701455] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
[    2.701459] pci_bus 0000:80: resource 6 [mem 0x000a0000-0x000bffff]
[    2.701462] pci_bus 0000:80: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.701466] pci_bus 0000:80: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.701469] pci_bus 0000:80: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.701472] pci_bus 0000:80: resource 10 [mem 0x000d0000-0x000d3fff]
[    2.701476] pci_bus 0000:80: resource 11 [mem 0x000d4000-0x000d7fff]
[    2.701479] pci_bus 0000:80: resource 12 [mem 0x000d8000-0x000dbfff]
[    2.701482] pci_bus 0000:80: resource 13 [mem 0x000dc000-0x000dffff]
[    2.701486] pci_bus 0000:80: resource 14 [mem 0x000e0000-0x000e3fff]
[    2.701489] pci_bus 0000:80: resource 15 [mem 0x000e4000-0x000e7fff]
[    2.701492] pci_bus 0000:80: resource 16 [mem 0x000e8000-0x000ebfff]
[    2.701496] pci_bus 0000:80: resource 17 [mem 0x000ec000-0x000effff]
[    2.701499] pci_bus 0000:80: resource 18 [mem 0x80000000-0xf3ffffff]
[    2.701503] pci_bus 0000:80: resource 19 [mem 0xf8000000-0xffffffff]
[    2.701551] NET: Registered protocol family 2
[    2.701638] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.701960] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.702644] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.702992] TCP: Hash tables configured (established 131072 bind 65536)
[    2.703002] TCP reno registered
[    2.703010] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    2.703028] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    2.703153] NET: Registered protocol family 1
[    4.300038] pci 0000:00:13.5: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    4.300064] PCI: CLS mismatch (64 != 32), using 64 bytes
[    4.300079] pci 0000:01:05.0: Boot video device
[    4.300117] Simple Boot Flag at 0x44 set to 0x1
[    4.300386] cpufreq-nforce2: No nForce2 chipset.
[    4.300551] audit: initializing netlink socket (disabled)
[    4.300566] type=2000 audit(1312643937.296:1): initialized
[    4.312848] highmem bounce pool size: 64 pages
[    4.312862] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    4.315136] VFS: Disk quotas dquot_6.5.2
[    4.315223] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.316138] fuse init (API version 7.16)
[    4.316259] msgmni has been set to 1706
[    4.316662] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.316725] io scheduler noop registered
[    4.316738] io scheduler deadline registered
[    4.316773] io scheduler cfq registered (default)
[    4.316942] pcieport 0000:00:04.0: setting latency timer to 64
[    4.316987] pcieport 0000:00:04.0: irq 16 for MSI/MSI-X
[    4.317047] pcieport 0000:00:05.0: setting latency timer to 64
[    4.317078] pcieport 0000:00:05.0: irq 17 for MSI/MSI-X
[    4.317131] pcieport 0000:00:06.0: setting latency timer to 64
[    4.317162] pcieport 0000:00:06.0: irq 18 for MSI/MSI-X
[    4.317254] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.317293] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.317478] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.317581] ACPI: AC Adapter [ADP0] (on-line)
[    4.317676] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    4.317690] ACPI: Power Button [PWRB]
[    4.317748] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    4.332077] ACPI: Lid Switch [LID]
[    4.332202] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.332215] ACPI: Power Button [PWRF]
[    4.332331] ACPI: Fan [FAN1] (off)
[    4.332471] ACPI: acpi_idle registered with cpuidle
[    4.332523] ACPI: processor limited to max C-state 1
[    4.352205] thermal LNXTHERM:00: registered as thermal_zone0
[    4.352218] ACPI: Thermal Zone [THZN] (65 C)
[    4.352314] ERST: Table is not found!
[    4.352437] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.352613] isapnp: Scanning for PnP cards...
[    4.357370] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.357395] ACPI: Battery Slot [BAT0] (battery present)
[    4.712300] isapnp: No Plug & Play device found
[    4.876381] Linux agpgart interface v0.103
[    4.878219] brd: module loaded
[    4.878991] loop: module loaded
[    4.879135] i2c-core: driver [adp5520] using legacy suspend method
[    4.879143] i2c-core: driver [adp5520] using legacy resume method
[    4.879455] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    4.879464] PCI: setting IRQ 11 as level-triggered
[    4.879472] pata_acpi 0000:00:14.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.879526] pata_acpi 0000:00:14.1: setting latency timer to 64
[    4.880065] Fixed MDIO Bus: probed
[    4.880128] PPP generic driver version 2.4.2
[    4.880208] tun: Universal TUN/TAP device driver, 1.6
[    4.880215] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.880336] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.880421] ehci_hcd 0000:00:13.5: power state changed by ACPI to D0
[    4.880436] ehci_hcd 0000:00:13.5: power state changed by ACPI to D0
[    4.880530] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    4.880540] ehci_hcd 0000:00:13.5: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.880574] ehci_hcd 0000:00:13.5: setting latency timer to 64
[    4.880578] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    4.880634] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    4.880728] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    4.880757] ehci_hcd 0000:00:13.5: debug port 1
[    4.880783] ehci_hcd 0000:00:13.5: irq 11, io mem 0x8e409400
[    4.892040] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    4.892250] hub 1-0:1.0: USB hub found
[    4.892260] hub 1-0:1.0: 10 ports detected
[    4.892394] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.892425] ohci_hcd 0000:00:13.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.892456] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    4.892461] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.892522] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    4.892596] ohci_hcd 0000:00:13.0: irq 11, io mem 0x8e408000
[    4.952182] hub 2-0:1.0: USB hub found
[    4.952198] hub 2-0:1.0: 2 ports detected
[    4.952390] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    4.952398] PCI: setting IRQ 5 as level-triggered
[    4.952404] ohci_hcd 0000:00:13.1: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    4.952430] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    4.952435] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.952500] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    4.952568] ohci_hcd 0000:00:13.1: irq 5, io mem 0x8e407000
[    5.012160] hub 3-0:1.0: USB hub found
[    5.012175] hub 3-0:1.0: 2 ports detected
[    5.012396] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    5.012406] ohci_hcd 0000:00:13.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    5.012437] ohci_hcd 0000:00:13.2: setting latency timer to 64
[    5.012442] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    5.012506] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    5.016075] ohci_hcd 0000:00:13.2: irq 11, io mem 0x8e406000
[    5.076162] hub 4-0:1.0: USB hub found
[    5.076177] hub 4-0:1.0: 2 ports detected
[    5.076283] ohci_hcd 0000:00:13.3: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    5.076307] ohci_hcd 0000:00:13.3: setting latency timer to 64
[    5.076312] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    5.076374] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    5.076438] ohci_hcd 0000:00:13.3: irq 5, io mem 0x8e405000
[    5.136175] hub 5-0:1.0: USB hub found
[    5.136191] hub 5-0:1.0: 2 ports detected
[    5.136290] ohci_hcd 0000:00:13.4: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    5.136318] ohci_hcd 0000:00:13.4: setting latency timer to 64
[    5.136322] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    5.136383] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    5.136448] ohci_hcd 0000:00:13.4: irq 11, io mem 0x8e404000
[    5.196170] hub 6-0:1.0: USB hub found
[    5.196185] hub 6-0:1.0: 2 ports detected
[    5.196294] uhci_hcd: USB Universal Host Controller Interface driver
[    5.196403] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    5.222434] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.222446] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.222632] mousedev: PS/2 mouse device common for all mice
[    5.223559] rtc_cmos 00:03: RTC can wake from S4
[    5.223667] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    5.223709] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    5.223832] device-mapper: uevent: version 1.0.3
[    5.223949] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    5.224121] device-mapper: multipath: version 1.2.0 loaded
[    5.224130] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.224243] EISA: Probing bus 0 at eisa.0
[    5.224250] EISA: Cannot allocate resource for mainboard
[    5.224257] Cannot allocate resource for EISA slot 1
[    5.224264] Cannot allocate resource for EISA slot 2
[    5.224270] Cannot allocate resource for EISA slot 3
[    5.224277] Cannot allocate resource for EISA slot 4
[    5.224283] Cannot allocate resource for EISA slot 5
[    5.224290] Cannot allocate resource for EISA slot 6
[    5.224296] Cannot allocate resource for EISA slot 7
[    5.224302] Cannot allocate resource for EISA slot 8
[    5.224309] EISA: Detected 0 cards.
[    5.224421] cpuidle: using governor ladder
[    5.224433] cpuidle: using governor menu
[    5.224784] TCP cubic registered
[    5.224955] NET: Registered protocol family 10
[    5.225648] NET: Registered protocol family 17
[    5.225680] Registering the dns_resolver key type
[    5.225724] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 (2 cpu cores) (version 2.20.00)
[    5.225818] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x12
[    5.225826] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[    5.225834] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[    5.225841] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1a
[    5.225930] Using IPI No-Shortcut mode
[    5.226069] PM: Hibernation image not present or could not be loaded.
[    5.226088] registered taskstats version 1
[    5.226381]   Magic number: 7:324:335
[    5.226418] tty tty56: hash matches
[    5.226440] ohci_hcd 0000:00:13.1: hash matches
[    5.226508] rtc_cmos 00:03: setting system clock to 2011-08-06 15:18:58 UTC (1312643938)
[    5.226520] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.226527] EDD information not available.
[    5.226685] Freeing unused kernel memory: 700k freed
[    5.227148] Write protecting the kernel text: 5192k
[    5.227210] Write protecting the kernel read-only data: 2148k
[    5.253885] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    5.260651] <30>udev[66]: starting version 167
[    5.344288] scsi0 : pata_atiixp
[    5.348065] scsi1 : pata_atiixp
[    5.348886] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x7000 irq 14
[    5.348896] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x7008 irq 15
[    5.361097] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.361139] r8169 0000:03:00.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    5.361187] r8169 0000:03:00.0: setting latency timer to 64
[    5.361238] r8169 0000:03:00.0: irq 19 for MSI/MSI-X
[    5.361844] r8169 0000:03:00.0: eth0: RTL8102e at 0xf804c000, 00:1e:33:97:a3:7a, XID 14a00000 IRQ 19
[    5.372084] usb 1-10: new high speed USB device using ehci_hcd and address 4
[    5.424501] acpi device:03: registered as cooling_device3
[    5.424596] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[    5.424681] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    5.512548] ata1.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.40, max UDMA/33
[    5.528511] ata1.00: configured for UDMA/33
[    5.528642] usbcore: registered new interface driver uas
[    5.531134] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.40 PQ: 0 ANSI: 5
[    5.533479] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.533490] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.533659] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.533756] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.544455] ahci 0000:00:12.0: version 3.0
[    5.544574] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[    5.544586] PCI: setting IRQ 10 as level-triggered
[    5.544593] ahci 0000:00:12.0: PCI INT A -> Link[LNKG] -> GSI 10 (level, low) -> IRQ 10
[    5.544633] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    5.544736] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    5.544748] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    5.554042] scsi2 : ahci
[    5.555510] scsi3 : ahci
[    5.555760] scsi4 : ahci
[    5.556116] scsi5 : ahci
[    5.556286] ata3: SATA max UDMA/133 abar m1024@0x8e409000 port 0x8e409100 irq 10
[    5.556298] ata4: SATA max UDMA/133 abar m1024@0x8e409000 port 0x8e409180 irq 10
[    5.556308] ata5: SATA max UDMA/133 abar m1024@0x8e409000 port 0x8e409200 irq 10
[    5.556319] ata6: SATA max UDMA/133 abar m1024@0x8e409000 port 0x8e409280 irq 10
[    5.573245] Initializing USB Mass Storage driver...
[    5.573371] [drm] Initialized drm 1.1.0 20060810
[    5.573916] scsi6 : usb-storage 1-10:1.0
[    5.574134] usbcore: registered new interface driver usb-storage
[    5.574142] USB Mass Storage support registered.
[    5.788038] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    5.876065] ata5: SATA link down (SStatus 0 SControl 300)
[    5.876113] ata4: SATA link down (SStatus 0 SControl 300)
[    5.876159] ata6: SATA link down (SStatus 0 SControl 300)
[    6.220042] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    6.332039] ata3: softreset failed (device not ready)
[    6.332057] ata3: applying SB600 PMP SRST workaround and retrying
[    6.457673] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input5
[    6.457861] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:13.1-1/input0
[    6.457962] usbcore: registered new interface driver usbhid
[    6.457969] usbhid: USB HID core driver
[    6.504055] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.505150] ata3.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC70P, max UDMA/100
[    6.505159] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    6.505169] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    6.506427] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    6.506435] ata3.00: configured for UDMA/100
[    6.506643] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    6.506888] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.507031] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    6.507183] sd 2:0:0:0: [sda] Write Protect is off
[    6.507192] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.507249] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.574532] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.575371] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.581137] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    6.916874]  sda: sda1 sda2 < sda5 sda6 >
[    6.917404] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.983362] [drm] radeon defaulting to kernel modesetting.
[    6.983374] [drm] radeon kernel modesetting enabled.
[    6.983481] radeon 0000:01:05.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    6.985325] [drm] initializing kernel modesetting (RS690 0x1002:0x791F).
[    6.985380] [drm] register mmio base: 0x8E300000
[    6.985386] [drm] register mmio size: 65536
[    6.986657] ATOM BIOS: ATI
[    6.986680] radeon 0000:01:05.0: VRAM: 128M 0x0000000078000000 - 0x000000007FFFFFFF (128M used)
[    6.986692] radeon 0000:01:05.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[    6.986726] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    6.986733] [drm] Driver supports precise vblank timestamp query.
[    6.986750] [drm] radeon: irq initialized.
[    6.986907] [drm] Detected VRAM RAM=128M, BAR=128M
[    6.986922] [drm] RAM width 128bits DDR
[    6.987088] [TTM] Zone  kernel: Available graphics memory: 437088 kiB.
[    6.987104] [TTM] Zone highmem: Available graphics memory: 964458 kiB.
[    6.987111] [TTM] Initializing pool allocator.
[    6.987143] [drm] radeon: 128M of VRAM memory ready
[    6.987151] [drm] radeon: 512M of GTT memory ready.
[    6.987182] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    6.995931] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[    7.005314] radeon 0000:01:05.0: WB enabled
[    7.005404] [drm] Loading RS690/RS740 Microcode
[    7.008073] [drm] radeon: ring at 0x0000000080001000
[    7.008102] [drm] ring test succeeded in 1 usecs
[    7.008279] [drm] radeon: ib pool ready.
[    7.008373] [drm] ib test succeeded in 0 usecs
[    7.008380] [drm] Enabling audio support
[    7.009154] [drm] Radeon Display Connectors
[    7.009165] [drm] Connector 0:
[    7.009170] [drm]   VGA
[    7.009175] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[    7.009184] [drm]   Encoders:
[    7.009188] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    7.009194] [drm] Connector 1:
[    7.009198] [drm]   LVDS
[    7.009203] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[    7.009211] [drm]   Encoders:
[    7.009216] [drm]     LCD1: INTERNAL_LVTM1
[    7.009221] [drm] Connector 2:
[    7.009225] [drm]   HDMI-A
[    7.009229] [drm]   HPD2
[    7.009234] [drm]   DDC: 0x7e40 0x7e60 0x7e44 0x7e64 0x7e48 0x7e68 0x7e4c 0x7e6c
[    7.009242] [drm]   Encoders:
[    7.009247] [drm]     DFP2: INTERNAL_DDI
[    7.010147] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input6
[    7.010346] sony 0003:054C:0268.0002: input,hiddev0,hidraw1: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:13.0-2/input0
[    7.115743] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.115757] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.115761] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.115764] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.115766] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.115769] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.115772] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.115775] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.115778] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.115780] 
[    7.165399] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.165406] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.165409] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.165411] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.165414] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.165417] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.165420] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.165423] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.165426] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.165428] 
[    7.215074] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.215081] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.215083] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.215086] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.215089] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.215092] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.215095] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.215098] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.215100] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.215103] 
[    7.264750] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.264757] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.264760] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.264763] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.264766] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.264768] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.264771] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.264774] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.264778] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.264780] 
[    7.264786] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[    7.756189] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.756203] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.756206] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.756209] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.756212] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.756215] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.756218] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.756221] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.756223] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.756226] 
[    7.805820] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.805827] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.805830] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.805832] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.805835] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.805838] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.805841] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.805844] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.805847] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.805849] 
[    7.855454] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.855461] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.855464] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.855467] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.855470] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.855473] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.855476] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.855479] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.855481] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.855484] 
[    7.905049] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.905056] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.905059] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.905062] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.905065] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.905068] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.905070] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.905073] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.905076] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.905079] 
[    7.905085] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[    7.905093] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[    7.909682] [drm] fb mappable at 0x80040000
[    7.909688] [drm] vram apper at 0x80000000
[    7.909693] [drm] size 4096000
[    7.909698] [drm] fb depth is 24
[    7.909703] [drm]    pitch is 5120
[    7.909806] fbcon: radeondrmfb (fb0) is primary device
[    8.072058] Console: switching to colour frame buffer device 160x50
[    8.078396] fb0: radeondrmfb frame buffer device
[    8.078441] drm: registered panic notifier
[    8.078487] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
[    8.415788] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.415852] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.415855] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.415858] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.415861] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.415864] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.415867] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.415870] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.415872] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.415875] 
[    8.465524] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.465575] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.465578] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.465581] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.465584] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.465587] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.465590] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.465592] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.465595] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.465597] 
[    8.515261] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.515313] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.515316] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.515319] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.515322] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.515325] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.515328] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.515330] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.515333] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.515336] 
[    8.565000] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.565054] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.565057] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.565060] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.565063] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.565065] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.565068] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.565071] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.565074] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.565076] 
[    8.565097] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[    8.565155] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[    8.618216] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.618268] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.618271] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.618274] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.618277] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.618280] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.618283] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.618286] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.618289] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.618291] 
[    8.667951] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.668016] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.668019] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.668022] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.668025] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.668028] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.668031] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.668034] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.668037] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.668039] 
[    8.717731] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.717783] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.717787] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.717789] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.717792] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.717795] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.717798] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.717801] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.717804] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.717806] 
[    8.767475] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.767526] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.767529] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.767532] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.767535] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.767538] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.767541] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.767544] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.767546] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.767549] 
[    8.767567] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[    8.767624] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[    8.803936] Btrfs loaded
[    8.811924] xor: automatically using best checksumming function: pIII_sse
[    8.828019]    pIII_sse  :  5629.000 MB/sec
[    8.828059] xor: using function: pIII_sse (5629.000 MB/sec)
[    8.831637] device-mapper: dm-raid45: initialized v0.2594b
[    9.085850] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   18.135183] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   18.135242] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.135245] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.135248] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.135251] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.135254] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.135257] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.135260] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.135262] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.135265] 
[   18.185103] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   18.185152] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.185155] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.185158] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.185161] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.185164] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.185167] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.185170] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.185173] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.185175] 
[   18.234957] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   18.235006] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.235009] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.235012] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.235015] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.235018] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.235020] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.235023] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.235026] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.235028] 
[   18.285027] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   18.285077] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.285080] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.285083] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.285086] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.285089] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.285092] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.285094] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.285097] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.285099] 
[   18.285118] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   18.285179] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   21.038926] <30>udev[362]: starting version 167
[   21.071602] lp: driver loaded but no devices found
[   21.083676] Adding 4907004k swap on /dev/sda6.  Priority:-1 extents:1 across:4907004k 
[   21.089175] i2c /dev entries driver
[   21.134087] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.262876] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   21.354729] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   21.396460] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   21.397765] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   21.397905] SP5100 TCO timer: Watchdog reboot not detected.
[   21.398003] SP5100 TCO timer: initialized (0xf80660f0). heartbeat=60 sec (nowayout=0)
[   21.445417] cfg80211: Calling CRDA to update world regulatory domain
[   21.780746] ath5k 0000:04:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   21.780761] ath5k 0000:04:00.0: setting latency timer to 64
[   21.780832] ath5k 0000:04:00.0: registered as 'phy0'
[   21.874966] HDA Intel 0000:00:14.2: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   21.935569] hda_codec: ALC268: BIOS auto-probing.
[   21.943938] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   21.944238] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   22.261828] cfg80211: World regulatory domain updated:
[   22.261834] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.261838] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.261842] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.261845] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.261848] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.261852] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.278260] ath: EEPROM regdomain: 0x65
[   22.278264] ath: EEPROM indicates we should expect a direct regpair map
[   22.278269] ath: Country alpha2 being used: 00
[   22.278271] ath: Regpair used: 0x65
[   22.278276] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   22.278280] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278282] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   22.278286] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278289] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   22.278292] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278295] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   22.278298] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278301] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   22.278304] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278307] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   22.278310] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278313] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   22.278317] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278319] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   22.278323] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278325] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   22.278329] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278332] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   22.278335] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278338] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   22.278341] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278344] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   22.278347] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278350] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   22.278354] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.278356] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   22.278422] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   22.290870] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   22.292604] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   22.669220] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04711/0xa04000/0x0
[   22.669228] synaptics: Toshiba Satellite L300D detected, limiting rate to 40pps.
[   22.758617] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   26.818257] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: user_xattr
[   28.375016] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   28.375075] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.375078] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.375081] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.375084] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.375087] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.375090] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.375093] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.375096] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.375098] 
[   28.425053] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   28.425104] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.425107] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.425110] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.425113] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.425116] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.425119] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.425121] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.425124] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.425126] 
[   28.491844] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   28.491904] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.491907] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.491910] <3>00 7f 3f 00 00 00 00 00 00 00 00 00 00 00 00 00  ..?.............
[   28.491913] <3>03 00 00 00 00 00 00 00 03 ff 00 00 00 00 00 00  ................
[   28.491916] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.491919] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 01  ................
[   28.491921] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.491924] <3>00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00  ................
[   28.491926] 
[   28.573535] ppdev: user-space parallel port driver
[   28.628300] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   28.628359] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.628363] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.628366] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.628369] <3>00 00 00 00 00 00 00 00 00 00 00 00 01 00 00 00  ................
[   28.628371] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.628374] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   28.628377] <3>00 00 00 00 00 00 3f 00 00 00 00 07 00 07 03 00  ......?.........
[   28.628380] <3>00 00 3f 00 00 00 00 00 00 00 00 00 00 00 00 00  ..?.............
[   28.628382] 
[   28.628387] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   28.628392] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   28.679545] r8169 0000:03:00.0: eth0: link down
[   28.679861] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.691653] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.143458] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   29.143467] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.143470] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.143473] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.143476] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.143479] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0f  ................
[   29.143482] <3>00 00 00 00 00 00 00 00 00 1f 00 00 00 00 00 00  ................
[   29.143485] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.143487] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.143489] 
[   29.194250] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   29.194256] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.194259] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.194261] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.194264] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.194267] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.194270] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.194273] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.194276] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.194278] 
[   29.244567] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   29.244571] <3>00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.244574] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.244577] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.244580] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.244583] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.244586] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.244588] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.244591] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.244593] 
[   29.296343] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   29.296349] <3>00 00 00 00 00 00 01 00 00 00 00 00 00 00 00 00  ................
[   29.296352] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.296355] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.296358] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.296361] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.296364] <3>00 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.296367] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.296370] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.296372] 
[   29.296377] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   29.296382] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   29.350036] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   29.350040] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.350043] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.350046] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.350049] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.350052] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.350055] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.350057] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.350060] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.350062] 
[   29.400144] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   29.400147] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.400150] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.400153] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.400156] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.400159] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.400161] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.400164] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.400167] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.400169] 
[   29.450206] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   29.450210] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.450213] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.450215] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.450218] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.450221] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.450224] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.450227] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.450229] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.450232] 
[   29.500341] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   29.500346] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.500349] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.500352] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.500355] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.500357] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.500360] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.500363] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.500366] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   29.500368] 
[   29.500372] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   29.500376] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
```

---

### Post by rdratlos on 2011-08-07
> **Routhy said:**
> Ok, I had to hit the /var/log/dmesg because even  after a fresh boot and outputting the dmesg results to a txt file there  was too much output and it was still being cut off at about 5.xxxx



OK. I've got the required information. The patch is in  Launchpad PPA (linux_2.6.38-10.47~lp722806thor2). Please follow the  instructions in [http://ubuntuforums.org/showpost.php?p=11048430&postcount=33](http://ubuntuforums.org/showpost.php?p=11048430&postcount=33) to update your system to the patched kernel. 

Once, you've tested it, please post again the complete dmesg. Good luck.

---

### Post by HunkirDowne on 2011-08-08
> **rdratlos said:**
> OK. I've got the required information. The patch is in  Launchpad PPA (linux_2.6.38-10.47~lp722806thor2). Please follow the  instructions in [http://ubuntuforums.org/showpost.php?p=11048430&postcount=33](http://ubuntuforums.org/showpost.php?p=11048430&postcount=33) to update your system to the patched kernel. 

Once, you've tested it, please post again the complete dmesg. Good luck.

Color me possibly confused, but I sense a potential duplication of efforts.  I have had this or a similar problem for some time now and have seen relief of sorts with sid so I think that the solution may already be in the works -- i.e., should appear in testing (and therefore Ubuntu) soon.

My new drm message reads:
> [   14.212655] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   14.212713] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   14.212788] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: detected RS690 floating bus bug, stopping ddc detect


Perhaps this is just the result of patchworks and not a true solution but I thought it noteworthy just the same.

---

### Post by rdratlos on 2011-08-08
> **HunkirDowne said:**
> Color me possibly confused, but I sense a potential duplication of efforts.  I have had this or a similar problem for some time now and have seen relief of sorts with sid so I think that the solution may already be in the works -- i.e., should appear in testing (and therefore Ubuntu) soon.

My new drm message reads:


Perhaps this is just the result of patchworks and not a true solution but I thought it noteworthy just the same.

You're right. There is another patch, which made it's way into the Linux kernel a week before and therefore got into Ubuntu oneiric and maybe also others. But kernel people's intention is to remove this patch and stay with the vendor/device specific solution.

> We also may want to revert 4a9a8b71e12d41abb71c4e741bff524f016cfef4
once this patch goes in, otherwise we may remove the ddc bus
unnecessarily on some systems.

---

### Post by Routhinator on 2011-08-10
> **rdratlos said:**
> OK. I've got the required information. The patch is in  Launchpad PPA (linux_2.6.38-10.47~lp722806thor2). Please follow the  instructions in [http://ubuntuforums.org/showpost.php?p=11048430&postcount=33](http://ubuntuforums.org/showpost.php?p=11048430&postcount=33) to update your system to the patched kernel. 

Once, you've tested it, please post again the complete dmesg. Good luck.

*sigh* Well it was a few days before I was able to try it. Just did however without success. Kernel patch is in, but the EDID spam starts up at 7.xxx and keeps going:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-10-generic (buildd@aluminium) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #47~lp722806thor2-Ubuntu SMP Sun Aug 7 20:26:28 UTC 2011 (Ubuntu 2.6.38-10.47~lp722806thor2-generic 2.6.38.7)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077c0d000 (usable)
[    0.000000]  BIOS-e820: 0000000077c0d000 - 0000000077cb8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077cb8000 - 0000000077cf0000 (usable)
[    0.000000]  BIOS-e820: 0000000077cf0000 - 0000000077cf1000 (reserved)
[    0.000000]  BIOS-e820: 0000000077cf1000 - 0000000077d30000 (usable)
[    0.000000]  BIOS-e820: 0000000077d30000 - 0000000077d33000 (reserved)
[    0.000000]  BIOS-e820: 0000000077d33000 - 0000000077dbb000 (usable)
[    0.000000]  BIOS-e820: 0000000077dbb000 - 0000000077dbf000 (reserved)
[    0.000000]  BIOS-e820: 0000000077dbf000 - 0000000077e85000 (usable)
[    0.000000]  BIOS-e820: 0000000077e85000 - 0000000077ebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077ebf000 - 0000000077eef000 (usable)
[    0.000000]  BIOS-e820: 0000000077eef000 - 0000000077eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077eff000 - 0000000077f00000 (usable)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: TOSHIBA Satellite L300D/, BIOS 1.70    09/16/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x77f00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00FFF00000 mask FFFFF00000 write-protect
[    0.000000]   1 base 0000000000 mask FFC0000000 write-back
[    0.000000]   2 base 0040000000 mask FFE0000000 write-back
[    0.000000]   3 base 0060000000 mask FFF0000000 write-back
[    0.000000]   4 base 0070000000 mask FFF8000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35c98000 - 36e44000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 TOSINV)
[    0.000000] ACPI: XSDT 77efe120 0005C (v01 TOSINV TOSINV00 00000003      01000013)
[    0.000000] ACPI: FACP 77efd000 000F4 (v04 TOSINV TOSINV00 00000003 MSFT 01000013)
[    0.000000] ACPI: DSDT 77ef2000 071F8 (v01 TOSINV TOSINV00 F0000000 MSFT 01000013)
[    0.000000] ACPI: FACS 77e8e000 00040
[    0.000000] ACPI: HPET 77efc000 00038 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 77efb000 00084 (v02 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 77efa000 0003C (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 77ef1000 00176 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 77ef0000 00028 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 77eef000 00210 (v01 AMD    PowerNow 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1031MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00077f00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00077c0d
[    0.000000]     0: 0x00077cb8 -> 0x00077cf0
[    0.000000]     0: 0x00077cf1 -> 0x00077d30
[    0.000000]     0: 0x00077d33 -> 0x00077dbb
[    0.000000]     0: 0x00077dbf -> 0x00077e85
[    0.000000]     0: 0x00077ebf -> 0x00077eef
[    0.000000]     0: 0x00077eff -> 0x00077f00
[    0.000000] On node 0 totalpages: 490898
[    0.000000] free_area_init_node: node 0, pgdat c1784140, node_mem_map f4d98200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2063 pages used for memmap
[    0.000000]   HighMem zone: 261622 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 77f00000 (gap: 77f00000:7c100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487059
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=32b6c5c5-2114-4113-a197-b230bc6543dd ro noapic
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9824960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00077f00)
[    0.000000] Memory: 1910120k/1965056k available (5190k kernel code, 53472k reserved, 2539k data, 700k init, 1054740k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc1511841 - 0xc178c4c0   (2539 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1511841   (5190 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:304 16
[    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1895.689 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 3791.37 BogoMIPS (lpj=7582756)
[    0.004032] pid_max: default: 32768 minimum: 301
[    0.004072] Security Framework initialized
[    0.004100] AppArmor: AppArmor initialized
[    0.004107] Yama: becoming mindful.
[    0.004194] Mount-cache hash table entries: 512
[    0.004376] Initializing cgroup subsys ns
[    0.004386] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004401] Initializing cgroup subsys cpuacct
[    0.004413] Initializing cgroup subsys memory
[    0.004429] Initializing cgroup subsys devices
[    0.004438] Initializing cgroup subsys freezer
[    0.004447] Initializing cgroup subsys net_cls
[    0.004455] Initializing cgroup subsys blkio
[    0.004502] CPU: Physical Processor ID: 0
[    0.004509] CPU: Processor Core ID: 0
[    0.004518] mce: CPU supports 5 MCE banks
[    0.004535] using C1E aware idle routine
[    0.010767] ACPI: Core revision 20110112
[    0.010780] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.010940] ACPI: Forced DSDT copy: length 0x071F8 copied locally, original unmapped
[    0.018224] ACPI: setting ELCR to 0200 (from 0c20)
[    0.020038] ftrace: allocating 23648 entries in 47 pages
[    0.024088] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.024103] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[    0.028001] Performance Events: AMD PMU driver.
[    0.028001] ... version:                0
[    0.028001] ... bit width:              48
[    0.028001] ... generic registers:      4
[    0.028001] ... value mask:             0000ffffffffffff
[    0.028001] ... max period:             00007fffffffffff
[    0.028001] ... fixed-purpose events:   0
[    0.028001] ... event mask:             000000000000000f
[    0.028001] CPU 1 irqstacks, hard=f40d8000 soft=f40da000
[    0.028001] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.008000] System has AMD C1E enabled
[    0.008000] Switch to broadcast mode on CPU1
[    0.112090] Brought up 2 CPUs
[    0.112103] Total of 2 processors activated (7581.95 BogoMIPS).
[    0.112432] Switch to broadcast mode on CPU0
[    0.112432] devtmpfs: initialized
[    0.113495] print_constraints: dummy: 
[    0.113540] Time: 12:53:35  Date: 08/10/11
[    0.113593] NET: Registered protocol family 16
[    0.113647] Trying to unpack rootfs image as initramfs...
[    0.113772] EISA bus registered
[    0.113787] TOM: 0000000080000000 aka 2048M
[    0.113802] ACPI: bus type pci registered
[    0.113894] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
[    0.113906] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
[    0.113914] PCI: Using MMCONFIG for extended config space
[    0.113920] PCI: Using configuration type 1 for base access
[    0.128181] bio: create slab <bio-0> at 0
[    0.129816] ACPI: EC: Look up EC in DSDT
[    0.131471] ACPI: Executed 1 blocks of module-level executable AML code
[    0.646785] Freeing initrd memory: 18096k freed
[    2.600231] ACPI: Interpreter enabled
[    2.600245] ACPI: (supports S0 S3 S4 S5)
[    2.600283] ACPI: Using PIC for interrupt routing
[    2.625764] ACPI: Power Resource [PFA1] (off)
[    2.626205] ACPI: EC: GPE = 0x7, I/O: command/status = 0x66, data = 0x62
[    2.640333] ACPI: No dock devices found.
[    2.640341] HEST: Table not found.
[    2.640348] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    2.640906] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    2.641984] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    2.641994] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    2.642002] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    2.642012] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    2.642021] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    2.642031] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    2.642040] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    2.642049] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    2.642059] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    2.642068] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    2.642078] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    2.642087] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    2.642096] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    2.642106] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    2.642115] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    2.642125] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xf3ffffff]
[    2.642134] pci_root PNP0A08:00: host bridge window [mem 0xf8000000-0xffffffff]
[    2.642144] pci_root PNP0A08:00: host bridge window [mem 0xfff00000-0xffffffff]
[    2.642156] pci_root PNP0A08:00: host bridge window expanded to [mem 0xf8000000-0xffffffff]; [mem 0xfff00000-0xffffffff] ignored
[    2.642172] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000cd7ff]
[    2.642197] pci 0000:00:00.0: [1002:7910] type 0 class 0x000600
[    2.642236] pci 0000:00:01.0: [1002:7912] type 1 class 0x000604
[    2.642287] pci 0000:00:04.0: [1002:7914] type 1 class 0x000604
[    2.642324] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    2.642328] pci 0000:00:04.0: PME# disabled
[    2.642347] pci 0000:00:05.0: [1002:7915] type 1 class 0x000604
[    2.642383] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    2.642387] pci 0000:00:05.0: PME# disabled
[    2.642405] pci 0000:00:06.0: [1002:7916] type 1 class 0x000604
[    2.642441] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    2.642445] pci 0000:00:06.0: PME# disabled
[    2.642488] pci 0000:00:12.0: [1002:4380] type 0 class 0x000101
[    2.642510] pci 0000:00:12.0: reg 10: [io  0x7038-0x703f]
[    2.642523] pci 0000:00:12.0: reg 14: [io  0x704c-0x704f]
[    2.642536] pci 0000:00:12.0: reg 18: [io  0x7030-0x7037]
[    2.642548] pci 0000:00:12.0: reg 1c: [io  0x7048-0x704b]
[    2.642561] pci 0000:00:12.0: reg 20: [io  0x7010-0x701f]
[    2.642574] pci 0000:00:12.0: reg 24: [mem 0x8e409000-0x8e4093ff]
[    2.642600] pci 0000:00:12.0: set SATA to AHCI mode
[    2.642640] pci 0000:00:13.0: [1002:4387] type 0 class 0x000c03
[    2.642657] pci 0000:00:13.0: reg 10: [mem 0x8e408000-0x8e408fff]
[    2.642738] pci 0000:00:13.1: [1002:4388] type 0 class 0x000c03
[    2.642756] pci 0000:00:13.1: reg 10: [mem 0x8e407000-0x8e407fff]
[    2.642837] pci 0000:00:13.2: [1002:4389] type 0 class 0x000c03
[    2.642854] pci 0000:00:13.2: reg 10: [mem 0x8e406000-0x8e406fff]
[    2.642935] pci 0000:00:13.3: [1002:438a] type 0 class 0x000c03
[    2.642952] pci 0000:00:13.3: reg 10: [mem 0x8e405000-0x8e405fff]
[    2.643032] pci 0000:00:13.4: [1002:438b] type 0 class 0x000c03
[    2.643050] pci 0000:00:13.4: reg 10: [mem 0x8e404000-0x8e404fff]
[    2.643137] pci 0000:00:13.5: [1002:4386] type 0 class 0x000c03
[    2.643161] pci 0000:00:13.5: reg 10: [mem 0x8e409400-0x8e4094ff]
[    2.643249] pci 0000:00:13.5: supports D1 D2
[    2.643252] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    2.643257] pci 0000:00:13.5: PME# disabled
[    2.643284] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    2.643312] pci 0000:00:14.0: reg 10: [io  0x0b00-0x0b0f]
[    2.643406] pci 0000:00:14.1: [1002:438c] type 0 class 0x000101
[    2.643424] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    2.643437] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    2.643450] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    2.643462] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    2.643475] pci 0000:00:14.1: reg 20: [io  0x7000-0x700f]
[    2.643522] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    2.643550] pci 0000:00:14.2: reg 10: [mem 0x8e400000-0x8e403fff 64bit]
[    2.643622] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    2.643628] pci 0000:00:14.2: PME# disabled
[    2.643648] pci 0000:00:14.3: [1002:438d] type 0 class 0x000601
[    2.643740] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    2.643798] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    2.643828] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    2.643852] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    2.643877] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    2.643943] pci 0000:01:05.0: [1002:791f] type 0 class 0x000300
[    2.643958] pci 0000:01:05.0: reg 10: [mem 0x80000000-0x87ffffff 64bit pref]
[    2.643967] pci 0000:01:05.0: reg 18: [mem 0x8e300000-0x8e30ffff 64bit]
[    2.643975] pci 0000:01:05.0: reg 20: [io  0x6000-0x60ff]
[    2.643982] pci 0000:01:05.0: reg 24: [mem 0x8e200000-0x8e2fffff]
[    2.644000] pci 0000:01:05.0: supports D1 D2
[    2.644022] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.644032] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
[    2.644037] pci 0000:00:01.0:   bridge window [mem 0x8e200000-0x8e3fffff]
[    2.644042] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x87ffffff 64bit pref]
[    2.644076] pci 0000:00:04.0: PCI bridge to [bus 09-0a]
[    2.644086] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
[    2.644090] pci 0000:00:04.0:   bridge window [mem 0x8d200000-0x8e1fffff]
[    2.644096] pci 0000:00:04.0:   bridge window [mem 0x88000000-0x88ffffff 64bit pref]
[    2.644146] pci 0000:03:00.0: [10ec:8136] type 0 class 0x000200
[    2.644178] pci 0000:03:00.0: reg 10: [io  0x3000-0x30ff]
[    2.644205] pci 0000:03:00.0: reg 18: [mem 0x89010000-0x89010fff 64bit pref]
[    2.644222] pci 0000:03:00.0: reg 20: [mem 0x89000000-0x8900ffff 64bit pref]
[    2.644235] pci 0000:03:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    2.644271] pci 0000:03:00.0: supports D1 D2
[    2.644274] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.644279] pci 0000:03:00.0: PME# disabled
[    2.652184] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    2.652195] pci 0000:00:05.0:   bridge window [io  0x3000-0x4fff]
[    2.652199] pci 0000:00:05.0:   bridge window [mem 0x8c200000-0x8d1fffff]
[    2.652205] pci 0000:00:05.0:   bridge window [mem 0x89000000-0x8a0fffff 64bit pref]
[    2.652256] pci 0000:04:00.0: [168c:001c] type 0 class 0x000200
[    2.652279] pci 0000:04:00.0: reg 10: [mem 0x8b100000-0x8b10ffff 64bit]
[    2.652377] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    2.652396] pci 0000:00:06.0: PCI bridge to [bus 04-04]
[    2.652406] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    2.652411] pci 0000:00:06.0:   bridge window [mem 0x8b100000-0x8c1fffff]
[    2.652417] pci 0000:00:06.0:   bridge window [mem 0x8a100000-0x8b0fffff 64bit pref]
[    2.652494] pci 0000:00:14.4: PCI bridge to [bus 80-8f] (subtractive decode)
[    2.652506] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    2.652512] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.652519] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.652523] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    2.652526] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    2.652530] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    2.652533] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    2.652537] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    2.652541] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    2.652545] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    2.652548] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    2.652552] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    2.652556] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    2.652560] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    2.652563] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    2.652567] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    2.652571] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    2.652574] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xf3ffffff] (subtractive decode)
[    2.652578] pci 0000:00:14.4:   bridge window [mem 0xf8000000-0xffffffff] (subtractive decode)
[    2.652601] pci_bus 0000:00: on NUMA node 0
[    2.652606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.652710] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    2.652767] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    2.652832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    2.652893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    2.652990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    2.653032]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    2.659506] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    2.659570] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[    2.659631] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[    2.659693] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[    2.659753] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.659816] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.659880] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *10 11 12 14 15)
[    2.659941] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.660094] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    2.660106] vgaarb: loaded
[    2.660402] SCSI subsystem initialized
[    2.660432] libata version 3.00 loaded.
[    2.660432] usbcore: registered new interface driver usbfs
[    2.660432] usbcore: registered new interface driver hub
[    2.660432] usbcore: registered new device driver usb
[    2.660432] wmi: Mapper loaded
[    2.660432] PCI: Using ACPI for IRQ routing
[    2.660432] PCI: pci_cache_line_size set to 64 bytes
[    2.660432] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    2.660432] reserve RAM buffer: 0000000077c0d000 - 0000000077ffffff 
[    2.660432] reserve RAM buffer: 0000000077cf0000 - 0000000077ffffff 
[    2.660432] reserve RAM buffer: 0000000077d30000 - 0000000077ffffff 
[    2.660432] reserve RAM buffer: 0000000077dbb000 - 0000000077ffffff 
[    2.660432] reserve RAM buffer: 0000000077e85000 - 0000000077ffffff 
[    2.660432] reserve RAM buffer: 0000000077eef000 - 0000000077ffffff 
[    2.660432] reserve RAM buffer: 0000000077f00000 - 0000000077ffffff 
[    2.660564] NetLabel: Initializing
[    2.660570] NetLabel:  domain hash size = 128
[    2.660576] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.660596] NetLabel:  unlabeled traffic allowed by default
[    2.660672] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    2.660684] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    2.662738] Switching to clocksource hpet
[    2.662746] Switched to NOHz mode on CPU #0
[    2.662759] Switched to NOHz mode on CPU #1
[    2.669525] AppArmor: AppArmor Filesystem Enabled
[    2.669573] pnp: PnP ACPI init
[    2.669598] ACPI: bus type pnp registered
[    2.670403] pnp 00:00: [bus 00-ff]
[    2.670408] pnp 00:00: [io  0x0000-0x0cf7 window]
[    2.670411] pnp 00:00: [io  0x0d00-0xffff window]
[    2.670414] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    2.670417] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    2.670421] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    2.670424] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    2.670427] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    2.670430] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    2.670434] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    2.670437] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    2.670440] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    2.670444] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    2.670447] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    2.670450] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    2.670454] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    2.670457] pnp 00:00: [mem 0x80000000-0xf3ffffff window]
[    2.670460] pnp 00:00: [mem 0xf8000000-0xffffffff window]
[    2.670463] pnp 00:00: [io  0x0cf8-0x0cff]
[    2.670467] pnp 00:00: [mem 0xfff00000-0xffffffff]
[    2.670542] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    2.670644] pnp 00:01: [io  0x0000-0x000f]
[    2.670647] pnp 00:01: [io  0x0081-0x008f]
[    2.670650] pnp 00:01: [io  0x00c0-0x00df]
[    2.670653] pnp 00:01: [dma 4]
[    2.670693] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    2.670704] pnp 00:02: [io  0x00f0-0x00fe]
[    2.670709] pnp 00:02: [irq 13]
[    2.670745] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    2.670781] pnp 00:03: [io  0x0070-0x0071]
[    2.670784] pnp 00:03: [irq 8]
[    2.670822] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.670833] pnp 00:04: [io  0x0061]
[    2.670874] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    2.670887] pnp 00:05: [io  0x0060]
[    2.670890] pnp 00:05: [io  0x0064]
[    2.670893] pnp 00:05: [irq 1]
[    2.670931] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    2.670942] pnp 00:06: [irq 12]
[    2.670983] pnp 00:06: Plug and Play ACPI device, IDs SYN1913 SYN1900 SYN0002 PNP0f13 (active)
[    2.671001] pnp 00:07: [io  0x0010-0x001f]
[    2.671004] pnp 00:07: [io  0x002e-0x002f]
[    2.671007] pnp 00:07: [io  0x0068]
[    2.671010] pnp 00:07: [io  0x006c]
[    2.671012] pnp 00:07: [io  0x0072-0x0073]
[    2.671015] pnp 00:07: [io  0x0080]
[    2.671018] pnp 00:07: [io  0x00b0-0x00b1]
[    2.671021] pnp 00:07: [io  0x0092]
[    2.671024] pnp 00:07: [io  0x0400-0x04cf]
[    2.671027] pnp 00:07: [io  0x04d0-0x04d1]
[    2.671030] pnp 00:07: [io  0x04d6]
[    2.671032] pnp 00:07: [io  0x05a0-0x05bf]
[    2.671036] pnp 00:07: [io  0x0680-0x06ff]
[    2.671039] pnp 00:07: [io  0x077a]
[    2.671041] pnp 00:07: [io  0x0c00-0x0c01]
[    2.671044] pnp 00:07: [io  0x0c14]
[    2.671047] pnp 00:07: [io  0x0c50-0x0c52]
[    2.671050] pnp 00:07: [io  0x0c6c]
[    2.671052] pnp 00:07: [io  0x0c6f]
[    2.671055] pnp 00:07: [io  0x0cd0-0x0cdb]
[    2.671058] pnp 00:07: [io  0x0022-0x0023]
[    2.671061] pnp 00:07: [io  0x0800-0x087f]
[    2.671064] pnp 00:07: [io  0x0b10-0x0b1f]
[    2.671069] pnp 00:07: [io  0x0cdc-0x0cdf]
[    2.671073] pnp 00:07: [mem 0xff800100-0xff80017f]
[    2.671184] system 00:07: [io  0x0400-0x04cf] has been reserved
[    2.671194] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    2.671201] system 00:07: [io  0x04d6] has been reserved
[    2.671209] system 00:07: [io  0x05a0-0x05bf] has been reserved
[    2.671217] system 00:07: [io  0x0680-0x06ff] has been reserved
[    2.671225] system 00:07: [io  0x077a] has been reserved
[    2.671233] system 00:07: [io  0x0c00-0x0c01] has been reserved
[    2.671241] system 00:07: [io  0x0c14] has been reserved
[    2.671248] system 00:07: [io  0x0c50-0x0c52] has been reserved
[    2.671256] system 00:07: [io  0x0c6c] has been reserved
[    2.671264] system 00:07: [io  0x0c6f] has been reserved
[    2.671271] system 00:07: [io  0x0cd0-0x0cdb] has been reserved
[    2.671279] system 00:07: [io  0x0800-0x087f] has been reserved
[    2.671287] system 00:07: [io  0x0b10-0x0b1f] has been reserved
[    2.671295] system 00:07: [io  0x0cdc-0x0cdf] has been reserved
[    2.671304] system 00:07: [mem 0xff800100-0xff80017f] has been reserved
[    2.671314] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.671586] pnp 00:08: [mem 0x00000000-0x0009ffff]
[    2.671589] pnp 00:08: [mem 0x000ec000-0x000fffff]
[    2.671592] pnp 00:08: [mem 0x00100000-0x7fffffff]
[    2.671595] pnp 00:08: [mem 0xf4000000-0xf7ffffff]
[    2.671598] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    2.671601] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    2.671671] system 00:08: [mem 0x00000000-0x0009ffff] could not be reserved
[    2.671681] system 00:08: [mem 0x000ec000-0x000fffff] could not be reserved
[    2.671690] system 00:08: [mem 0x00100000-0x7fffffff] could not be reserved
[    2.671699] system 00:08: [mem 0xf4000000-0xf7ffffff] has been reserved
[    2.671707] system 00:08: [mem 0xfec00000-0xfec00fff] has been reserved
[    2.671716] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    2.671725] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.672148] pnp: PnP ACPI: found 9 devices
[    2.672155] ACPI: ACPI bus type pnp unregistered
[    2.672162] PnPBIOS: Disabled by ACPI PNP
[    2.709023] pci 0000:03:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    2.709069] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.709078] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
[    2.709086] pci 0000:00:01.0:   bridge window [mem 0x8e200000-0x8e3fffff]
[    2.709095] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x87ffffff 64bit pref]
[    2.709107] pci 0000:00:04.0: PCI bridge to [bus 09-0a]
[    2.709115] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
[    2.709125] pci 0000:00:04.0:   bridge window [mem 0x8d200000-0x8e1fffff]
[    2.709135] pci 0000:00:04.0:   bridge window [mem 0x88000000-0x88ffffff 64bit pref]
[    2.709150] pci 0000:03:00.0: BAR 6: assigned [mem 0x89020000-0x8903ffff pref]
[    2.709160] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    2.709167] pci 0000:00:05.0:   bridge window [io  0x3000-0x4fff]
[    2.709176] pci 0000:00:05.0:   bridge window [mem 0x8c200000-0x8d1fffff]
[    2.709185] pci 0000:00:05.0:   bridge window [mem 0x89000000-0x8a0fffff 64bit pref]
[    2.709196] pci 0000:00:06.0: PCI bridge to [bus 04-04]
[    2.709204] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    2.709212] pci 0000:00:06.0:   bridge window [mem 0x8b100000-0x8c1fffff]
[    2.709221] pci 0000:00:06.0:   bridge window [mem 0x8a100000-0x8b0fffff 64bit pref]
[    2.709233] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
[    2.709244] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    2.709255] pci 0000:00:14.4:   bridge window [mem disabled]
[    2.709264] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    2.709283] pci 0000:00:01.0: setting latency timer to 64
[    2.709290] pci 0000:00:04.0: setting latency timer to 64
[    2.709296] pci 0000:00:05.0: setting latency timer to 64
[    2.709302] pci 0000:00:06.0: setting latency timer to 64
[    2.709311] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.709315] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.709318] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.709322] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.709325] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.709329] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.709332] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    2.709336] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    2.709339] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    2.709343] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    2.709346] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    2.709349] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    2.709353] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    2.709356] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    2.709360] pci_bus 0000:00: resource 18 [mem 0x80000000-0xf3ffffff]
[    2.709363] pci_bus 0000:00: resource 19 [mem 0xf8000000-0xffffffff]
[    2.709367] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
[    2.709370] pci_bus 0000:01: resource 1 [mem 0x8e200000-0x8e3fffff]
[    2.709373] pci_bus 0000:01: resource 2 [mem 0x80000000-0x87ffffff 64bit pref]
[    2.709377] pci_bus 0000:09: resource 0 [io  0x5000-0x5fff]
[    2.709380] pci_bus 0000:09: resource 1 [mem 0x8d200000-0x8e1fffff]
[    2.709384] pci_bus 0000:09: resource 2 [mem 0x88000000-0x88ffffff 64bit pref]
[    2.709387] pci_bus 0000:03: resource 0 [io  0x3000-0x4fff]
[    2.709391] pci_bus 0000:03: resource 1 [mem 0x8c200000-0x8d1fffff]
[    2.709394] pci_bus 0000:03: resource 2 [mem 0x89000000-0x8a0fffff 64bit pref]
[    2.709398] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    2.709401] pci_bus 0000:04: resource 1 [mem 0x8b100000-0x8c1fffff]
[    2.709405] pci_bus 0000:04: resource 2 [mem 0x8a100000-0x8b0fffff 64bit pref]
[    2.709408] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
[    2.709411] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
[    2.709415] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
[    2.709418] pci_bus 0000:80: resource 6 [mem 0x000a0000-0x000bffff]
[    2.709421] pci_bus 0000:80: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.709425] pci_bus 0000:80: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.709428] pci_bus 0000:80: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.709432] pci_bus 0000:80: resource 10 [mem 0x000d0000-0x000d3fff]
[    2.709435] pci_bus 0000:80: resource 11 [mem 0x000d4000-0x000d7fff]
[    2.709438] pci_bus 0000:80: resource 12 [mem 0x000d8000-0x000dbfff]
[    2.709442] pci_bus 0000:80: resource 13 [mem 0x000dc000-0x000dffff]
[    2.709445] pci_bus 0000:80: resource 14 [mem 0x000e0000-0x000e3fff]
[    2.709449] pci_bus 0000:80: resource 15 [mem 0x000e4000-0x000e7fff]
[    2.709452] pci_bus 0000:80: resource 16 [mem 0x000e8000-0x000ebfff]
[    2.709456] pci_bus 0000:80: resource 17 [mem 0x000ec000-0x000effff]
[    2.709459] pci_bus 0000:80: resource 18 [mem 0x80000000-0xf3ffffff]
[    2.709462] pci_bus 0000:80: resource 19 [mem 0xf8000000-0xffffffff]
[    2.709510] NET: Registered protocol family 2
[    2.709596] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.709923] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.710607] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.710961] TCP: Hash tables configured (established 131072 bind 65536)
[    2.710971] TCP reno registered
[    2.710979] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    2.710998] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    2.711124] NET: Registered protocol family 1
[    4.308037] pci 0000:00:13.5: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    4.308063] PCI: CLS mismatch (64 != 32), using 64 bytes
[    4.308079] pci 0000:01:05.0: Boot video device
[    4.308117] Simple Boot Flag at 0x44 set to 0x1
[    4.308387] cpufreq-nforce2: No nForce2 chipset.
[    4.308553] audit: initializing netlink socket (disabled)
[    4.308568] type=2000 audit(1312980819.304:1): initialized
[    4.320848] highmem bounce pool size: 64 pages
[    4.320860] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    4.323125] VFS: Disk quotas dquot_6.5.2
[    4.323212] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.324092] fuse init (API version 7.16)
[    4.324213] msgmni has been set to 1706
[    4.324616] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.324680] io scheduler noop registered
[    4.324693] io scheduler deadline registered
[    4.324730] io scheduler cfq registered (default)
[    4.324900] pcieport 0000:00:04.0: setting latency timer to 64
[    4.324945] pcieport 0000:00:04.0: irq 16 for MSI/MSI-X
[    4.325004] pcieport 0000:00:05.0: setting latency timer to 64
[    4.325037] pcieport 0000:00:05.0: irq 17 for MSI/MSI-X
[    4.325089] pcieport 0000:00:06.0: setting latency timer to 64
[    4.325121] pcieport 0000:00:06.0: irq 18 for MSI/MSI-X
[    4.325212] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.325251] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.325432] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.325532] ACPI: AC Adapter [ADP0] (on-line)
[    4.325625] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    4.325639] ACPI: Power Button [PWRB]
[    4.325698] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    4.360033] ACPI: Lid Switch [LID]
[    4.360141] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.360154] ACPI: Power Button [PWRF]
[    4.360255] ACPI: Fan [FAN1] (off)
[    4.360411] ACPI: acpi_idle registered with cpuidle
[    4.360444] ACPI: processor limited to max C-state 1
[    4.381422] thermal LNXTHERM:00: registered as thermal_zone0
[    4.381435] ACPI: Thermal Zone [THZN] (61 C)
[    4.381528] ERST: Table is not found!
[    4.381693] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.381845] isapnp: Scanning for PnP cards...
[    4.385679] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.385702] ACPI: Battery Slot [BAT0] (battery present)
[    4.740639] isapnp: No Plug & Play device found
[    4.924379] Linux agpgart interface v0.103
[    4.926219] brd: module loaded
[    4.926985] loop: module loaded
[    4.927135] i2c-core: driver [adp5520] using legacy suspend method
[    4.927143] i2c-core: driver [adp5520] using legacy resume method
[    4.927451] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    4.927460] PCI: setting IRQ 11 as level-triggered
[    4.927467] pata_acpi 0000:00:14.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.927521] pata_acpi 0000:00:14.1: setting latency timer to 64
[    4.928070] Fixed MDIO Bus: probed
[    4.928132] PPP generic driver version 2.4.2
[    4.928208] tun: Universal TUN/TAP device driver, 1.6
[    4.928215] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.928336] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.928418] ehci_hcd 0000:00:13.5: power state changed by ACPI to D0
[    4.928433] ehci_hcd 0000:00:13.5: power state changed by ACPI to D0
[    4.928526] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    4.928535] ehci_hcd 0000:00:13.5: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.928569] ehci_hcd 0000:00:13.5: setting latency timer to 64
[    4.928574] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    4.928632] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    4.928726] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    4.928756] ehci_hcd 0000:00:13.5: debug port 1
[    4.928782] ehci_hcd 0000:00:13.5: irq 11, io mem 0x8e409400
[    4.940041] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    4.940259] hub 1-0:1.0: USB hub found
[    4.940269] hub 1-0:1.0: 10 ports detected
[    4.940403] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.940434] ohci_hcd 0000:00:13.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.940466] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    4.940471] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.940528] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    4.940597] ohci_hcd 0000:00:13.0: irq 11, io mem 0x8e408000
[    5.000183] hub 2-0:1.0: USB hub found
[    5.000199] hub 2-0:1.0: 2 ports detected
[    5.000395] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    5.000403] PCI: setting IRQ 5 as level-triggered
[    5.000409] ohci_hcd 0000:00:13.1: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    5.000435] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    5.000440] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.000505] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    5.000575] ohci_hcd 0000:00:13.1: irq 5, io mem 0x8e407000
[    5.060167] hub 3-0:1.0: USB hub found
[    5.060183] hub 3-0:1.0: 2 ports detected
[    5.060400] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    5.060409] ohci_hcd 0000:00:13.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    5.060439] ohci_hcd 0000:00:13.2: setting latency timer to 64
[    5.060444] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    5.060507] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    5.064073] ohci_hcd 0000:00:13.2: irq 11, io mem 0x8e406000
[    5.124172] hub 4-0:1.0: USB hub found
[    5.124187] hub 4-0:1.0: 2 ports detected
[    5.124296] ohci_hcd 0000:00:13.3: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    5.124321] ohci_hcd 0000:00:13.3: setting latency timer to 64
[    5.124326] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    5.124389] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    5.128070] ohci_hcd 0000:00:13.3: irq 5, io mem 0x8e405000
[    5.188177] hub 5-0:1.0: USB hub found
[    5.188193] hub 5-0:1.0: 2 ports detected
[    5.188290] ohci_hcd 0000:00:13.4: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    5.188319] ohci_hcd 0000:00:13.4: setting latency timer to 64
[    5.188324] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    5.188383] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    5.188445] ohci_hcd 0000:00:13.4: irq 11, io mem 0x8e404000
[    5.248172] hub 6-0:1.0: USB hub found
[    5.248187] hub 6-0:1.0: 2 ports detected
[    5.248298] uhci_hcd: USB Universal Host Controller Interface driver
[    5.248407] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    5.272911] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.272924] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.273106] mousedev: PS/2 mouse device common for all mice
[    5.274684] rtc_cmos 00:03: RTC can wake from S4
[    5.274792] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    5.274833] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    5.274955] device-mapper: uevent: version 1.0.3
[    5.275068] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    5.275224] device-mapper: multipath: version 1.2.0 loaded
[    5.275232] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.275342] EISA: Probing bus 0 at eisa.0
[    5.275349] EISA: Cannot allocate resource for mainboard
[    5.275357] Cannot allocate resource for EISA slot 1
[    5.275363] Cannot allocate resource for EISA slot 2
[    5.275370] Cannot allocate resource for EISA slot 3
[    5.275376] Cannot allocate resource for EISA slot 4
[    5.275383] Cannot allocate resource for EISA slot 5
[    5.275389] Cannot allocate resource for EISA slot 6
[    5.275396] Cannot allocate resource for EISA slot 7
[    5.275402] Cannot allocate resource for EISA slot 8
[    5.275409] EISA: Detected 0 cards.
[    5.275522] cpuidle: using governor ladder
[    5.275533] cpuidle: using governor menu
[    5.275888] TCP cubic registered
[    5.276076] NET: Registered protocol family 10
[    5.276768] NET: Registered protocol family 17
[    5.276802] Registering the dns_resolver key type
[    5.276840] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 (2 cpu cores) (version 2.20.00)
[    5.276934] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x12
[    5.276942] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[    5.276950] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[    5.276958] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1a
[    5.277045] Using IPI No-Shortcut mode
[    5.277187] PM: Hibernation image not present or could not be loaded.
[    5.277207] registered taskstats version 1
[    5.277503]   Magic number: 7:374:885
[    5.277616] rtc_cmos 00:03: setting system clock to 2011-08-10 12:53:40 UTC (1312980820)
[    5.277628] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.277635] EDD information not available.
[    5.277795] Freeing unused kernel memory: 700k freed
[    5.278264] Write protecting the kernel text: 5192k
[    5.278326] Write protecting the kernel read-only data: 2148k
[    5.306363] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    5.312068] usb 1-10: new high speed USB device using ehci_hcd and address 3
[    5.312231] <30>udev[66]: starting version 167
[    5.441921] scsi0 : pata_atiixp
[    5.445672] scsi1 : pata_atiixp
[    5.446470] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x7000 irq 14
[    5.446480] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x7008 irq 15
[    5.465081] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.465123] r8169 0000:03:00.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    5.465172] r8169 0000:03:00.0: setting latency timer to 64
[    5.465223] r8169 0000:03:00.0: irq 19 for MSI/MSI-X
[    5.465829] r8169 0000:03:00.0: eth0: RTL8102e at 0xf803c000, 00:1e:33:97:a3:7a, XID 14a00000 IRQ 19
[    5.474296] acpi device:03: registered as cooling_device3
[    5.474404] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[    5.474485] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    5.493304] [drm] Initialized drm 1.1.0 20060810
[    5.515776] usbcore: registered new interface driver uas
[    5.604040] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    5.608584] ata1.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.40, max UDMA/33
[    5.630480] ata1.00: configured for UDMA/33
[    5.633131] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.40 PQ: 0 ANSI: 5
[    5.635554] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.635566] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.635741] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.635839] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.656836] ahci 0000:00:12.0: version 3.0
[    5.656956] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[    5.656968] PCI: setting IRQ 10 as level-triggered
[    5.656975] ahci 0000:00:12.0: PCI INT A -> Link[LNKG] -> GSI 10 (level, low) -> IRQ 10
[    5.657016] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    5.657163] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    5.657176] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    5.658079] Initializing USB Mass Storage driver...
[    5.659180] scsi3 : ahci
[    5.659488] scsi4 : ahci
[    5.659671] scsi5 : ahci
[    5.659829] scsi6 : ahci
[    5.660068] ata3: SATA max UDMA/133 abar m1024@0x8e409000 port 0x8e409100 irq 10
[    5.660081] ata4: SATA max UDMA/133 abar m1024@0x8e409000 port 0x8e409180 irq 10
[    5.660092] ata5: SATA max UDMA/133 abar m1024@0x8e409000 port 0x8e409200 irq 10
[    5.660103] ata6: SATA max UDMA/133 abar m1024@0x8e409000 port 0x8e409280 irq 10
[    5.660850] scsi2 : usb-storage 1-10:1.0
[    5.661321] usbcore: registered new interface driver usb-storage
[    5.661333] USB Mass Storage support registered.
[    5.980061] ata4: SATA link down (SStatus 0 SControl 300)
[    5.980114] ata6: SATA link down (SStatus 0 SControl 300)
[    5.980162] ata5: SATA link down (SStatus 0 SControl 300)
[    6.432037] ata3: softreset failed (device not ready)
[    6.432053] ata3: applying SB600 PMP SRST workaround and retrying
[    6.604045] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.605138] ata3.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC70P, max UDMA/100
[    6.605147] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    6.605157] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    6.606414] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    6.606422] ata3.00: configured for UDMA/100
[    6.606617] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    6.606870] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    6.607016] sd 3:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    6.607173] sd 3:0:0:0: [sda] Write Protect is off
[    6.607189] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.607248] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.662413] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.663211] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.669138] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    7.027537]  sda: sda1 sda2 < sda5 sda6 >
[    7.028096] sd 3:0:0:0: [sda] Attached SCSI disk
[    7.040820] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input5
[    7.041134] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:13.1-1/input0
[    7.041441] usbcore: registered new interface driver usbhid
[    7.041451] usbhid: USB HID core driver
[    7.076322] [drm] radeon defaulting to kernel modesetting.
[    7.076336] [drm] radeon kernel modesetting enabled.
[    7.076509] radeon 0000:01:05.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    7.078277] [drm] initializing kernel modesetting (RS690 0x1002:0x791F 0x1179:0xFF68).
[    7.078331] [drm] register mmio base: 0x8E300000
[    7.078337] [drm] register mmio size: 65536
[    7.079528] ATOM BIOS: ATI
[    7.079553] radeon 0000:01:05.0: VRAM: 128M 0x0000000078000000 - 0x000000007FFFFFFF (128M used)
[    7.079565] radeon 0000:01:05.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[    7.079590] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    7.079597] [drm] Driver supports precise vblank timestamp query.
[    7.079614] [drm] radeon: irq initialized.
[    7.079769] [drm] Detected VRAM RAM=128M, BAR=128M
[    7.079783] [drm] RAM width 128bits DDR
[    7.079906] [TTM] Zone  kernel: Available graphics memory: 437088 kiB.
[    7.079922] [TTM] Zone highmem: Available graphics memory: 964458 kiB.
[    7.079929] [TTM] Initializing pool allocator.
[    7.079957] [drm] radeon: 128M of VRAM memory ready
[    7.079965] [drm] radeon: 512M of GTT memory ready.
[    7.080064] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    7.088778] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[    7.098369] radeon 0000:01:05.0: WB enabled
[    7.098451] [drm] Loading RS690/RS740 Microcode
[    7.101197] [drm] radeon: ring at 0x0000000080001000
[    7.101226] [drm] ring test succeeded in 1 usecs
[    7.101479] [drm] radeon: ib pool ready.
[    7.101563] [drm] ib test succeeded in 0 usecs
[    7.101571] [drm] Enabling audio support
[    7.103082] [drm] Radeon Display Connectors
[    7.103093] [drm] Connector 0:
[    7.103098] [drm]   VGA
[    7.103104] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[    7.103112] [drm]   Encoders:
[    7.103117] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    7.103123] [drm] Connector 1:
[    7.103127] [drm]   LVDS
[    7.103132] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[    7.103141] [drm]   Encoders:
[    7.103145] [drm]     LCD1: INTERNAL_LVTM1
[    7.103150] [drm] Connector 2:
[    7.103155] [drm]   HDMI-A
[    7.103159] [drm]   HPD2
[    7.103164] [drm]   DDC: 0x7e40 0x7e60 0x7e44 0x7e64 0x7e48 0x7e68 0x7e4c 0x7e6c
[    7.103173] [drm]   Encoders:
[    7.103177] [drm]     DFP2: INTERNAL_DDI
[    7.105161] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[    7.158391] [drm] Radeon display connector LVDS-1: Found valid EDID
[    7.209737] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.209747] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.209750] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.209753] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.209756] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.209759] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.209762] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.209765] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.209768] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.209770] 
[    7.259407] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.259414] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.259417] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.259420] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.259423] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.259425] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.259428] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.259431] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.259434] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.259437] 
[    7.309078] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.309085] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.309088] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.309091] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.309094] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.309097] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.309100] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.309103] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.309106] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.309108] 
[    7.358736] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.358743] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.358746] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.358749] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.358752] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.358755] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.358758] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.358761] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.358764] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.358766] 
[    7.358772] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[    7.358781] [drm] Radeon display connector HDMI-A-1: No monitor connected or invalid EDID
[    7.852271] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.852287] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.852290] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.852293] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.852296] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.852299] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.852302] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.852305] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.852308] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.852310] 
[    7.901882] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.901889] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.901892] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.901895] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.901898] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.901901] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.901904] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.901907] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.901910] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.901912] 
[    7.951502] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    7.951509] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.951512] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.951515] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.951517] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.951520] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.951523] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.951526] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.951529] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    7.951531] 
[    8.001128] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.001135] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.001138] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.001141] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.001143] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.001146] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.001149] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.001152] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.001155] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.001157] 
[    8.001163] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[    8.001171] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[    8.005907] [drm] fb mappable at 0x80040000
[    8.005913] [drm] vram apper at 0x80000000
[    8.005918] [drm] size 4096000
[    8.005923] [drm] fb depth is 24
[    8.005928] [drm]    pitch is 5120
[    8.006029] fbcon: radeondrmfb (fb0) is primary device
[    8.168061] Console: switching to colour frame buffer device 160x50
[    8.174377] fb0: radeondrmfb frame buffer device
[    8.174421] drm: registered panic notifier
[    8.174466] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
[    8.511891] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.511955] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.511958] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.511961] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.511964] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.511967] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.511970] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.511973] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.511975] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.511978] 
[    8.561615] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.561667] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.561670] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.561673] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.561676] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.561679] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.561682] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.561684] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.561687] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.561689] 
[    8.611324] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.611377] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.611380] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.611383] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.611386] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.611389] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.611392] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.611395] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.611398] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.611400] 
[    8.661061] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.661113] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.661116] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.661121] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.661124] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.661127] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.661130] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.661133] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.661136] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.661138] 
[    8.661158] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[    8.661217] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[    8.714276] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.714328] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.714331] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.714334] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.714337] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.714339] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.714342] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.714345] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.714348] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.714350] 
[    8.763977] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.764041] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.764044] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.764047] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.764050] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.764053] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.764056] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.764059] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.764062] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.764064] 
[    8.813714] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.813767] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.813770] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.813773] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.813776] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.813779] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.813782] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.813785] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.813788] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.813790] 
[    8.863411] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    8.863462] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.863465] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.863468] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.863471] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.863474] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.863477] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.863480] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.863483] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[    8.863485] 
[    8.863502] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[    8.863560] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[    8.900043] Btrfs loaded
[    8.908081] xor: automatically using best checksumming function: pIII_sse
[    8.928024]    pIII_sse  :  5740.000 MB/sec
[    8.928063] xor: using function: pIII_sse (5740.000 MB/sec)
[    8.931634] device-mapper: dm-raid45: initialized v0.2594b
[    9.229725] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.371520] Adding 4907004k swap on /dev/sda6.  Priority:-1 extents:1 across:4907004k 
[   12.162734] <30>udev[376]: starting version 167
[   12.943869] lp: driver loaded but no devices found
[   13.434273] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   13.479830] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.481634] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   13.527773] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   13.528056] SP5100 TCO timer: Watchdog reboot not detected.
[   13.528963] SP5100 TCO timer: initialized (0xf80860f0). heartbeat=60 sec (nowayout=0)
[   13.970019] i2c /dev entries driver
[   14.253054] cfg80211: Calling CRDA to update world regulatory domain
[   14.320234] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04711/0xa04000/0x0
[   14.320242] synaptics: Toshiba Satellite L300D detected, limiting rate to 40pps.
[   14.398668] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   14.754497] ath5k 0000:04:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   14.754512] ath5k 0000:04:00.0: setting latency timer to 64
[   14.754583] ath5k 0000:04:00.0: registered as 'phy0'
[   15.250900] ath: EEPROM regdomain: 0x65
[   15.250904] ath: EEPROM indicates we should expect a direct regpair map
[   15.250909] ath: Country alpha2 being used: 00
[   15.250911] ath: Regpair used: 0x65
[   15.250915] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.250919] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250922] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.250926] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250928] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.250932] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250934] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.250938] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250941] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.250944] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250947] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.250950] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250953] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.250956] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250959] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.250962] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250965] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.250968] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250971] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.250975] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250977] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.250981] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250983] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.250987] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250990] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.250993] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.250996] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   15.251070] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   15.582534] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.583333] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   15.683957] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   15.683966] cfg80211: World regulatory domain updated:
[   15.683969] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.683973] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.683977] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.683980] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.683983] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.683987] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.091008] HDA Intel 0000:00:14.2: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   16.205568] hda_codec: ALC268: BIOS auto-probing.
[   16.213680] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   16.213843] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   17.008551] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.400845] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: user_xattr
[   18.263625] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   18.263684] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 03 00  ................
[   18.263688] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.263691] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.263694] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.263697] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.263699] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.263702] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.263705] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.263707] 
[   18.313383] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   18.313433] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.313435] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.313438] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.313441] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.313444] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.313447] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.313450] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.313452] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.313455] 
[   18.363392] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   18.363445] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.363448] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.363450] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.363453] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.363456] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.363459] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.363462] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.363465] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.363467] 
[   18.413170] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   18.413220] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.413224] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.413227] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.413230] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.413232] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.413235] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.413238] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.413241] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.413243] 
[   18.413248] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   18.413252] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   18.891978] ppdev: user-space parallel port driver
[   22.840821] r8169 0000:03:00.0: eth0: link down
[   22.841127] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.852121] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.365280] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   25.365287] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.365290] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.365294] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.365297] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.365300] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.365302] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.365305] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.365308] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.365310] 
[   25.415034] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   25.415037] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.415040] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.415043] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.415046] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.415049] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.415052] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.415055] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.415058] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.415060] 
[   25.464774] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   25.464777] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.464780] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.464783] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.464787] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.464790] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.464793] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.464795] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.464798] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.464801] 
[   25.514491] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   25.514494] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.514497] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.514501] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.514503] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.514506] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.514509] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.514512] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.514515] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.514517] 
[   25.514522] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   25.514526] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   25.567580] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   25.567583] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.567586] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.567589] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.567592] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.567595] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.567598] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.567601] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.567604] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.567606] 
[   25.617319] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   25.617322] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.617325] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.617328] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.617331] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.617334] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.617337] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.617340] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.617343] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.617345] 
[   25.667035] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   25.667038] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.667042] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.667045] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.667048] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.667051] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.667054] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.667057] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.667060] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.667062] 
[   25.716899] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   25.716902] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.716905] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.716908] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.716911] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.716914] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.716917] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.716920] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.716923] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.716925] 
[   25.716928] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   25.716932] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   25.925666] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   25.925673] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.925676] <3>00 00 00 00 00 00 00 00 01 01 01 01 00 7f 00 00  ................
[   25.925679] <3>00 00 00 00 00 07 00 00 00 00 00 00 00 00 00 00  ................
[   25.925682] <3>00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 ff  ................
[   25.925685] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.925688] <3>00 00 00 00 00 00 0f 00 00 00 00 00 00 00 00 00  ................
[   25.925691] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.925694] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   25.925696] 
[   26.010816] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   26.010824] <3>00 00 00 00 00 00 ff 00 00 00 00 00 00 00 00 00  ................
[   26.010828] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.010831] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.010834] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.010836] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0f  ................
[   26.010839] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.010842] <3>00 00 00 00 00 00 00 00 00 00 7f 00 00 00 00 00  ................
[   26.010845] <3>00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00 00  ................
[   26.010847] 
[   26.062974] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   26.062981] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.062985] <3>00 00 3f 00 00 00 00 00 00 00 00 00 00 00 00 00  ..?.............
[   26.062988] <3>00 00 00 00 ff 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.062991] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.062994] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.062997] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.062999] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.063002] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.063004] 
[   26.113513] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   26.113521] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.113524] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.113527] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.113530] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.113532] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.113535] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.113538] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.113541] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.113543] 
[   26.113547] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   26.113552] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
[   26.169285] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   26.169293] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.169296] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.169299] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.169301] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.169304] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.169307] <3>00 00 00 00 00 00 00 7f 00 00 00 00 00 00 00 00  ................
[   26.169310] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.169313] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.169315] 
[   26.220237] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   26.220244] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.220247] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.220250] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.220253] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.220256] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.220258] <3>00 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.220261] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.220264] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.220266] 
[   26.270386] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   26.270390] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.270393] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.270396] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.270399] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.270401] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.270404] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.270407] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.270410] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.270412] 
[   26.320276] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   26.320279] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.320283] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.320286] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.320289] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.320292] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.320295] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.320298] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.320300] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   26.320303] 
[   26.320307] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[   26.320311] [drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
```



I still cannot help but feel there is something wrong with this vendor/device solution. The only device on my system that has all 0's is the first one. The other 3 have information in the EDIDs. To me this clearly shows that the kernel is probing the same device 4 times (likely my external monitor port, which would make sense for it to be blank) and not checking the other three. I haven't studied kernel source, however from the programming logic I do understand, this seems to show a flaw.

---

### Post by rdratlos on 2011-08-11
> **Routhy said:**
> *sigh* Well it was a few days before I was able to try it. Just did however without success. Kernel patch is in, but the EDID spam starts up at 7.xxx and keeps going:

I still cannot help but feel there is something wrong with this vendor/device solution. The only device on my system that has all 0's is the first one. The other 3 have information in the EDIDs. To me this clearly shows that the kernel is probing the same device 4 times (likely my external monitor port, which would make sense for it to be blank) and not checking the other three. I haven't studied kernel source, however from the programming logic I do understand, this seems to show a flaw.

Sorry, my mistake. That's why I asked to attach the new dmesg. The sub-vendor ID in the patch is wrong. Unfortunately, the kernel logs this information only when using the extended DDC probing patch. Without it, we have to rely on the lspci output. If a vendor has more than one ID, this may lead to the problem that we have here.

I will correct the patch and build it tonight (linux_2.6.38-10.47~lp722806thor3). Once it is in the PPA, your system should automatically inform you and ask you for update.

Please test it again. If the EDID spam (except of four EDID dumps) is gone, please confirm it to the forum. You don't need to post dmesg again in this case.

---

### Post by Routhinator on 2011-08-14
> **rdratlos said:**
> Sorry, my mistake. That's why I asked to attach the new dmesg. The sub-vendor ID in the patch is wrong. Unfortunately, the kernel logs this information only when using the extended DDC probing patch. Without it, we have to rely on the lspci output. If a vendor has more than one ID, this may lead to the problem that we have here.

I will correct the patch and build it tonight (linux_2.6.38-10.47~lp722806thor3). Once it is in the PPA, your system should automatically inform you and ask you for update.

Please test it again. If the EDID spam (except of four EDID dumps) is gone, please confirm it to the forum. You don't need to post dmesg again in this case.

Ok, got to test this update finally. It worked! I finally no longer have spam, and additionally the computer is running faster, cooler and I FINALLY have some kind og 3D acceleration going on with the radeon driver. About time! This fix needs to be committed to the main kernel.

---

### Post by GavinP on 2011-08-20
Still not resolved I'm afraid - even with the latest PPA kernel:

...
[  195.225610] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  195.225612] 
[  196.117467] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  196.117471] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  196.117474] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  196.117477] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  196.117479] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  196.117482] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  196.117484] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  196.117487] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  196.117489] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  196.117492] 
[  197.008141] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  197.008145] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.008148] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.008150] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.008153] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.008155] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.008158] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.008160] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.008163] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.008165] 
[  197.898332] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  197.898338] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.898341] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.898344] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.898347] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.898349] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.898352] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.898354] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.898357] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  197.898359] 
[  197.898364] radeon 0000:01:00.0: DVI-I-1: EDID block 0 invalid.
[  197.898367] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[  208.893299] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  208.893306] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  208.893309] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  208.893311] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  208.893314] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  208.893316] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  208.893319] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  208.893321] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  208.893324] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  208.893326] 
[  209.820291] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  209.820296] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  209.820298] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  209.820301] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  209.820303] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  209.820306] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  209.820308] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  209.820311] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  209.820313] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  209.820316] 
[  210.745588] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  210.745594] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  210.745597] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  210.745599] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  210.745602] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  210.745604] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  210.745607] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  210.745610] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  210.745612] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  210.745614] 
[  211.668921] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  211.668926] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  211.668929] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  211.668932] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  211.668934] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  211.668937] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  211.668939] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  211.668942] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  211.668944] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  211.668946] 
[  211.668951] radeon 0000:01:00.0: DVI-I-1: EDID block 0 invalid.
[  211.668955] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[  222.715643] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  222.715649] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  222.715652] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  222.715655] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  222.715657] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  222.715660] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  222.715663] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  222.715665] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  222.715668] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  222.715670] 
[  223.669141] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  223.669146] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  223.669148] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  223.669151] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  223.669154] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  223.669156] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  223.669159] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  223.669161] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  223.669164] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  223.669166] 
[  224.620099] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  224.620103] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  224.620106] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  224.620109] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  224.620111] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  224.620114] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  224.620116] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  224.620119] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  224.620121] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  224.620123] 
[  225.567933] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  225.567937] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  225.567940] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  225.567942] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  225.567945] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  225.567948] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  225.567950] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  225.567953] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  225.567955] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  225.567957] 
[  225.567962] radeon 0000:01:00.0: DVI-I-1: EDID block 0 invalid.
[  225.567965] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[  237.530504] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  237.530512] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  237.530515] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  237.530517] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  237.530520] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  237.530523] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  237.530525] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  237.530528] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  237.530530] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  237.530532] 
[  239.353682] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  239.353689] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.353692] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.353694] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.353697] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.353699] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.353702] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.353704] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.353707] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.353709] 
[  241.007219] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  241.007226] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  241.007229] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  241.007232] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  241.007234] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  241.007237] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  241.007239] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  241.007242] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  241.007244] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  241.007246] 
[  242.484065] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  242.484073] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  242.484076] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  242.484079] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  242.484081] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  242.484084] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  242.484086] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  242.484089] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  242.484091] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  242.484093] 
[  242.484099] radeon 0000:01:00.0: DVI-I-1: EDID block 0 invalid.
[  242.484103] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[  253.526307] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  253.526314] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  253.526317] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  253.526320] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  253.526322] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  253.526325] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  253.526327] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  253.526330] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  253.526332] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  253.526334] 
[  254.475511] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  254.475515] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  254.475518] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  254.475520] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  254.475523] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  254.475525] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  254.475528] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  254.475530] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  254.475533] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  254.475535] 
[  255.864069] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  255.864078] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  255.864081] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  255.864084] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  255.864086] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  255.864089] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  255.864091] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  255.864094] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  255.864097] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  255.864099] 
[  257.548863] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  257.548871] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  257.548874] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  257.548877] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  257.548879] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  257.548882] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  257.548884] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  257.548887] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  257.548889] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  257.548891] 
[  257.548897] radeon 0000:01:00.0: DVI-I-1: EDID block 0 invalid.
[  257.548901] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[  268.567362] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  268.567369] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  268.567372] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  268.567375] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  268.567377] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  268.567380] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  268.567383] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  268.567385] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  268.567388] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  268.567390] 
[  269.517875] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  269.517880] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  269.517883] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  269.517885] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  269.517888] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  269.517890] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  269.517893] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  269.517895] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  269.517898] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  269.517900] 
[  270.466909] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  270.466914] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  270.466917] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  270.466919] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  270.466922] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  270.466924] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  270.466927] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  270.466929] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  270.466932] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  270.466934] 
[  271.413314] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  271.413319] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  271.413322] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  271.413325] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  271.413327] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  271.413330] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  271.413332] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  271.413335] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  271.413338] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  271.413340] 
[  271.413345] radeon 0000:01:00.0: DVI-I-1: EDID block 0 invalid.
[  271.413348] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[  282.497196] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  282.497203] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  282.497206] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  282.497209] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  282.497212] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  282.497214] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  282.497217] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  282.497219] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  282.497222] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  282.497224] 
[  283.437941] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  283.437949] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  283.437952] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  283.437955] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  283.437957] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  283.437960] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  283.437962] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  283.437965] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  283.437967] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  283.437969] 
[  284.400365] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  284.400372] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  284.400375] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  284.400378] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  284.400381] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  284.400383] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  284.400386] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  284.400388] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  284.400391] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  284.400393] 
[  285.376388] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  285.376395] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  285.376398] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  285.376401] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  285.376404] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  285.376406] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  285.376409] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  285.376411] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  285.376414] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  285.376416] 
[  285.376420] radeon 0000:01:00.0: DVI-I-1: EDID block 0 invalid.
[  285.376425] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID

Thanks

Gavin

---

### Post by stijngysemans on 2011-08-26
I also have this issue (EDID_BLOCK_VALID) which blocks the system.

---

### Post by rdratlos on 2011-09-05
> **GavinP said:**
> Still not resolved I'm afraid - even with the latest PPA kernel:

.

Thanks

Gavin

Dear all, 

if you want to get the EDID flooding problem fixed on your system please always post the following information:

[LIST=1]
[*]A complete dmesg log from its beginning at boot start until the following line:
```
[drm] Initialized radeon ... 
```
[*]The output of the command 
```
lspci -v
```
[/LIST]
Please install the PPA kernel for your Ubuntu version beforehand, even though it does not help you, yet. But the fixed kernel provides valuable information to you me, that is required to really fix the problem also for your system.

BR

rdratlos

---

### Post by tieri on 2011-10-26
Hello. I think that i have this same issue whit ubuntu 11.10.
Is there a solution or work around for this?

Here is my dmesg log
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=5ce61936-7a64-4d30-94a0-1d226e39a412 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: System manufacturer System Product Name/M2A-VM HDMI, BIOS ASUS M2A-VM HDMI ACPI BIOS Revision 2201 10/22/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
[    0.000000]   3 base 00CFF00000 mask FFFFF00000 uncachable
[    0.000000]   4 base 0100000000 mask FFE0000000 write-back
[    0.000000]   5 base 0120000000 mask FFF0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3327MB, range: 1MB, type UC
[    0.000000] reg 4, base: 4GB, range: 512MB, type WB
[    0.000000] reg 5, base: 4608MB, range: 256MB, type WB
[    0.000000] total RAM covered: 3327M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3327MB, range: 1MB, type UC
[    0.000000] e820 update range: 00000000cff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfee0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f6560] f6560
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfee0000
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfee0000 page 4k
[    0.000000] kernel direct mapping tables up to cfee0000 @ cfeda000-cfee0000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 12fffa000-130000000
[    0.000000] RAMDISK: 3661c000 - 37306000
[    0.000000] ACPI: RSDP 00000000000f8210 00024 (v02 ATI   )
[    0.000000] ACPI: XSDT 00000000cfee3100 0004C (v01 ATI    ASUSACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 00000000cfee8500 000F4 (v03 ATI    ASUSACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 00000000cfee3280 05210 (v01 ATI    ASUSACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfee0000 00040
[    0.000000] ACPI: SSDT 00000000cfee8740 0028A (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 00000000cfee8a40 00038 (v01 ATI    ASUSACPI 42302E31 AWRD 00000098)
[    0.000000] ACPI: MCFG 00000000cfee8ac0 0003C (v01 ATI    ASUSACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 00000000cfee8640 00084 (v01 ATI    ASUSACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012b600000-ffff88012effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfee0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048175
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8200 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfee0000 - 00000000cfee3000
[    0.000000] PM: Registered nosave memory: 00000000cfee3000 - 00000000cfef0000
[    0.000000] PM: Registered nosave memory: 00000000cfef0000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88012fc00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031146
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=5ce61936-7a64-4d30-94a0-1d226e39a412 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ c4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 3974564k/4980736k available (6104k kernel code, 788036k absent, 218136k reserved, 4880k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2600.125 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.008006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5200.25 BogoMIPS (lpj=10400500)
[    0.008010] pid_max: default: 32768 minimum: 301
[    0.008039] Security Framework initialized
[    0.008054] AppArmor: AppArmor initialized
[    0.008055] Yama: becoming mindful.
[    0.008476] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013719] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.015071] Mount-cache hash table entries: 256
[    0.015232] Initializing cgroup subsys cpuacct
[    0.015238] Initializing cgroup subsys memory
[    0.015248] Initializing cgroup subsys devices
[    0.015250] Initializing cgroup subsys freezer
[    0.015252] Initializing cgroup subsys net_cls
[    0.015254] Initializing cgroup subsys blkio
[    0.015263] Initializing cgroup subsys perf_event
[    0.015291] tseg: 00cff00000
[    0.015293] CPU: Physical Processor ID: 0
[    0.015295] CPU: Processor Core ID: 0
[    0.015297] mce: CPU supports 5 MCE banks
[    0.015307] using AMD E400 aware idle routine
[    0.016716] ACPI: Core revision 20110413
[    0.020041] ftrace: allocating 25651 entries in 101 pages
[    0.024609] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.065675] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
[    0.068003] Performance Events: AMD PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      4
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000000f
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9a000
[    0.152057] Brought up 2 CPUs
[    0.152060] Total of 2 processors activated (10400.02 BogoMIPS).
[    0.152537] devtmpfs: initialized
[    0.152537] PM: Registering ACPI NVS region at cfee0000 (12288 bytes)
[    0.153452] print_constraints: dummy: 
[    0.153478] Time:  4:00:44  Date: 10/26/11
[    0.153521] NET: Registered protocol family 16
[    0.153558] Trying to unpack rootfs image as initramfs...
[    0.153650] node 0 link 0: io port [c000, ffff]
[    0.153653] TOM: 00000000d0000000 aka 3328M
[    0.153655] node 0 link 0: mmio [a0000, bffff]
[    0.153658] node 0 link 0: mmio [d0000000, dfffffff]
[    0.153660] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.153663] node 0 link 0: mmio [e0000000, e03fffff]
[    0.153665] TOM2: 0000000130000000 aka 4864M
[    0.153667] bus: [00, 03] on node 0 link 0
[    0.153670] bus: 00 index 0 [io  0x0000-0xffff]
[    0.153672] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.153674] bus: 00 index 2 [mem 0xd0000000-0xefffffff]
[    0.153676] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.153678] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
[    0.153688] ACPI: bus type pci registered
[    0.153746] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.153749] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.176748] PCI: Using configuration type 1 for base access
[    0.177571] bio: create slab <bio-0> at 0
[    0.178387] ACPI: EC: Look up EC in DSDT
[    0.182350] ACPI: Interpreter enabled
[    0.182353] ACPI: (supports S0 S1 S3 S4 S5)
[    0.182373] ACPI: Using IOAPIC for interrupt routing
[    0.186229] ACPI: No dock devices found.
[    0.186232] HEST: Table not found.
[    0.186235] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.186304] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.186439] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.186442] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.186444] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.186446] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.186449] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xfebfffff]
[    0.186460] pci 0000:00:00.0: [1002:7910] type 0 class 0x000600
[    0.186491] pci 0000:00:02.0: [1002:7913] type 1 class 0x000604
[    0.186512] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.186515] pci 0000:00:02.0: PME# disabled
[    0.186533] pci 0000:00:07.0: [1002:7917] type 1 class 0x000604
[    0.186553] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.186556] pci 0000:00:07.0: PME# disabled
[    0.186586] pci 0000:00:12.0: [1002:4380] type 0 class 0x000101
[    0.186604] pci 0000:00:12.0: reg 10: [io  0xff00-0xff07]
[    0.186614] pci 0000:00:12.0: reg 14: [io  0xfe00-0xfe03]
[    0.186624] pci 0000:00:12.0: reg 18: [io  0xfd00-0xfd07]
[    0.186634] pci 0000:00:12.0: reg 1c: [io  0xfc00-0xfc03]
[    0.186644] pci 0000:00:12.0: reg 20: [io  0xfb00-0xfb0f]
[    0.186655] pci 0000:00:12.0: reg 24: [mem 0xfe02f000-0xfe02f3ff]
[    0.186676] pci 0000:00:12.0: set SATA to AHCI mode
[    0.186706] pci 0000:00:13.0: [1002:4387] type 0 class 0x000c03
[    0.186720] pci 0000:00:13.0: reg 10: [mem 0xfe02e000-0xfe02efff]
[    0.186787] pci 0000:00:13.1: [1002:4388] type 0 class 0x000c03
[    0.186801] pci 0000:00:13.1: reg 10: [mem 0xfe02d000-0xfe02dfff]
[    0.186871] pci 0000:00:13.2: [1002:4389] type 0 class 0x000c03
[    0.186885] pci 0000:00:13.2: reg 10: [mem 0xfe02c000-0xfe02cfff]
[    0.186952] pci 0000:00:13.3: [1002:438a] type 0 class 0x000c03
[    0.186966] pci 0000:00:13.3: reg 10: [mem 0xfe02b000-0xfe02bfff]
[    0.187032] pci 0000:00:13.4: [1002:438b] type 0 class 0x000c03
[    0.187046] pci 0000:00:13.4: reg 10: [mem 0xfe02a000-0xfe02afff]
[    0.187119] pci 0000:00:13.5: [1002:4386] type 0 class 0x000c03
[    0.187139] pci 0000:00:13.5: reg 10: [mem 0xfe029000-0xfe0290ff]
[    0.187211] pci 0000:00:13.5: supports D1 D2
[    0.187213] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.187217] pci 0000:00:13.5: PME# disabled
[    0.187240] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.187262] pci 0000:00:14.0: reg 10: [io  0x0b00-0x0b0f]
[    0.187340] pci 0000:00:14.1: [1002:438c] type 0 class 0x000101
[    0.187354] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.187364] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.187374] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.187384] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.187394] pci 0000:00:14.1: reg 20: [io  0xf900-0xf90f]
[    0.187433] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.187455] pci 0000:00:14.2: reg 10: [mem 0xfe020000-0xfe023fff 64bit]
[    0.187515] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.187519] pci 0000:00:14.2: PME# disabled
[    0.187534] pci 0000:00:14.3: [1002:438d] type 0 class 0x000601
[    0.187612] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.187660] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.187677] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.187692] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.187708] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.187758] pci 0000:01:00.0: [1002:94c3] type 0 class 0x000300
[    0.187772] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.187782] pci 0000:01:00.0: reg 18: [mem 0xfdbf0000-0xfdbfffff 64bit]
[    0.187790] pci 0000:01:00.0: reg 20: [io  0xde00-0xdeff]
[    0.187802] pci 0000:01:00.0: reg 30: [mem 0xfdbc0000-0xfdbdffff pref]
[    0.187819] pci 0000:01:00.0: supports D1 D2
[    0.192026] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.192030] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.192033] pci 0000:00:02.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.192037] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.192076] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.192091] pci 0000:02:00.0: reg 10: [io  0xee00-0xeeff]
[    0.192115] pci 0000:02:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit]
[    0.192143] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.192179] pci 0000:02:00.0: supports D1 D2
[    0.192181] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.192185] pci 0000:02:00.0: PME# disabled
[    0.192204] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.192211] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.192214] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.192217] pci 0000:00:07.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.192221] pci 0000:00:07.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.192251] pci 0000:03:05.0: [1131:7146] type 0 class 0x000480
[    0.192269] pci 0000:03:05.0: reg 10: [mem 0xfdeff000-0xfdeff1ff]
[    0.192356] pci 0000:03:06.0: [1131:7146] type 0 class 0x000480
[    0.192373] pci 0000:03:06.0: reg 10: [mem 0xfdefe000-0xfdefe1ff]
[    0.192463] pci 0000:03:07.0: [1106:3044] type 0 class 0x000c00
[    0.192486] pci 0000:03:07.0: reg 10: [mem 0xfdefd000-0xfdefd7ff]
[    0.192500] pci 0000:03:07.0: reg 14: [io  0xcf00-0xcf7f]
[    0.192582] pci 0000:03:07.0: supports D2
[    0.192584] pci 0000:03:07.0: PME# supported from D2 D3hot D3cold
[    0.192589] pci 0000:03:07.0: PME# disabled
[    0.192636] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.192641] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    0.192645] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.192650] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff pref]
[    0.192653] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.192655] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.192658] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.192660] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.192663] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xfebfffff] (subtractive decode)
[    0.192676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.192883] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.192970] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.193011] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.193052]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.193055]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.193057] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.209021] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.209065] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.209108] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.209151] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.209193] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11)
[    0.209235] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11)
[    0.209279] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
[    0.209325] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.209446] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.209450] vgaarb: loaded
[    0.209451] vgaarb: bridge control possible 0000:01:00.0
[    0.209661] SCSI subsystem initialized
[    0.209753] libata version 3.00 loaded.
[    0.209810] usbcore: registered new interface driver usbfs
[    0.209821] usbcore: registered new interface driver hub
[    0.209853] usbcore: registered new device driver usb
[    0.209942] PCI: Using ACPI for IRQ routing
[    0.218991] PCI: pci_cache_line_size set to 64 bytes
[    0.219085] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.219087] reserve RAM buffer: 00000000cfee0000 - 00000000cfffffff 
[    0.219205] NetLabel: Initializing
[    0.219207] NetLabel:  domain hash size = 128
[    0.219208] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.219220] NetLabel:  unlabeled traffic allowed by default
[    0.219267] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.219271] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.221055] Switching to clocksource hpet
[    0.222518] Switched to NOHz mode on CPU #0
[    0.222567] Switched to NOHz mode on CPU #1
[    0.227373] AppArmor: AppArmor Filesystem Enabled
[    0.227412] pnp: PnP ACPI init
[    0.227432] ACPI: bus type pnp registered
[    0.227567] pnp 00:00: [bus 00-ff]
[    0.227570] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.227572] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.227574] pnp 00:00: [io  0x0d00-0xffff window]
[    0.227576] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.227578] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.227581] pnp 00:00: [mem 0xd0000000-0xfebfffff window]
[    0.227640] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.227720] pnp 00:01: [io  0x4100-0x411f]
[    0.227723] pnp 00:01: [io  0x0228-0x022f]
[    0.227724] pnp 00:01: [io  0x040b]
[    0.227726] pnp 00:01: [io  0x04d6]
[    0.227728] pnp 00:01: [io  0x0c00-0x0c01]
[    0.227730] pnp 00:01: [io  0x0c14]
[    0.227731] pnp 00:01: [io  0x0c50-0x0c52]
[    0.227738] pnp 00:01: [io  0x0c6c-0x0c6d]
[    0.227739] pnp 00:01: [io  0x0c6f]
[    0.227741] pnp 00:01: [io  0x0cd0-0x0cd1]
[    0.227743] pnp 00:01: [io  0x0cd2-0x0cd3]
[    0.227745] pnp 00:01: [io  0x0cd4-0x0cdf]
[    0.227747] pnp 00:01: [io  0x4000-0x40fe]
[    0.227748] pnp 00:01: [io  0x4210-0x4217]
[    0.227750] pnp 00:01: [io  0x0b10-0x0b1f]
[    0.227752] pnp 00:01: [mem 0x00000000-0x00000fff window]
[    0.227755] pnp 00:01: [mem 0xfee00400-0xfee00fff window]
[    0.227800] pnp 00:01: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:02:00.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.227837] system 00:01: [io  0x4100-0x411f] has been reserved
[    0.227840] system 00:01: [io  0x0228-0x022f] has been reserved
[    0.227843] system 00:01: [io  0x040b] has been reserved
[    0.227845] system 00:01: [io  0x04d6] has been reserved
[    0.227848] system 00:01: [io  0x0c00-0x0c01] has been reserved
[    0.227850] system 00:01: [io  0x0c14] has been reserved
[    0.227853] system 00:01: [io  0x0c50-0x0c52] has been reserved
[    0.227855] system 00:01: [io  0x0c6c-0x0c6d] has been reserved
[    0.227858] system 00:01: [io  0x0c6f] has been reserved
[    0.227860] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
[    0.227862] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
[    0.227865] system 00:01: [io  0x0cd4-0x0cdf] has been reserved
[    0.227867] system 00:01: [io  0x4000-0x40fe] has been reserved
[    0.227870] system 00:01: [io  0x4210-0x4217] has been reserved
[    0.227872] system 00:01: [io  0x0b10-0x0b1f] has been reserved
[    0.227876] system 00:01: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.227880] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.228024] pnp 00:02: [dma 4]
[    0.228026] pnp 00:02: [io  0x0000-0x000f]
[    0.228028] pnp 00:02: [io  0x0080-0x0090]
[    0.228030] pnp 00:02: [io  0x0094-0x009f]
[    0.228032] pnp 00:02: [io  0x00c0-0x00df]
[    0.228063] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.228109] pnp 00:03: [irq 0 disabled]
[    0.228124] pnp 00:03: [irq 8]
[    0.228126] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.228152] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.228178] pnp 00:04: [io  0x0070-0x0073]
[    0.228204] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.228212] pnp 00:05: [io  0x0061]
[    0.228244] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.228256] pnp 00:06: [io  0x00f0-0x00ff]
[    0.228264] pnp 00:06: [irq 13]
[    0.228290] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.228333] pnp 00:07: [io  0x0010-0x001f]
[    0.228334] pnp 00:07: [io  0x0022-0x003f]
[    0.228336] pnp 00:07: [io  0x0044-0x005f]
[    0.228338] pnp 00:07: [io  0x0062-0x0063]
[    0.228340] pnp 00:07: [io  0x0065-0x006f]
[    0.228341] pnp 00:07: [io  0x0074-0x007f]
[    0.228343] pnp 00:07: [io  0x0091-0x0093]
[    0.228345] pnp 00:07: [io  0x00a2-0x00bf]
[    0.228347] pnp 00:07: [io  0x00e0-0x00ef]
[    0.228349] pnp 00:07: [io  0x04d0-0x04d1]
[    0.228350] pnp 00:07: [io  0x0220-0x0225]
[    0.228406] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.228408] system 00:07: [io  0x0220-0x0225] has been reserved
[    0.228411] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.228568] pnp 00:08: [io  0x03f0-0x03f5]
[    0.228570] pnp 00:08: [io  0x03f7]
[    0.228578] pnp 00:08: [irq 6]
[    0.228580] pnp 00:08: [dma 2]
[    0.228622] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.228826] pnp 00:09: [io  0x03f8-0x03ff]
[    0.228838] pnp 00:09: [irq 4]
[    0.228896] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.229220] pnp 00:0a: [io  0x0378-0x037f]
[    0.229229] pnp 00:0a: [irq 7]
[    0.229279] pnp 00:0a: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.229397] pnp 00:0b: [irq 12]
[    0.229436] pnp 00:0b: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.229458] pnp 00:0c: [io  0x0060]
[    0.229460] pnp 00:0c: [io  0x0064]
[    0.229468] pnp 00:0c: [irq 1]
[    0.229510] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.229553] pnp 00:0d: [mem 0xe0000000-0xefffffff]
[    0.229608] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
[    0.229612] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.229781] pnp 00:0e: [mem 0x000cf000-0x000cffff]
[    0.229783] pnp 00:0e: [mem 0x000f0000-0x000f7fff]
[    0.229785] pnp 00:0e: [mem 0x000f8000-0x000fbfff]
[    0.229787] pnp 00:0e: [mem 0x000fc000-0x000fffff]
[    0.229789] pnp 00:0e: [mem 0xcfef0000-0xcffeffff]
[    0.229791] pnp 00:0e: [mem 0xfed00000-0xfed000ff]
[    0.229793] pnp 00:0e: [mem 0xcfee0000-0xcfefffff]
[    0.229795] pnp 00:0e: [mem 0xffff0000-0xffffffff]
[    0.229797] pnp 00:0e: [mem 0x00000000-0x0009ffff]
[    0.229799] pnp 00:0e: [mem 0x00100000-0xcfedffff]
[    0.229801] pnp 00:0e: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.229803] pnp 00:0e: [mem 0xfec00000-0xfec00fff]
[    0.229805] pnp 00:0e: [mem 0xfee00000-0xfee00fff]
[    0.229806] pnp 00:0e: [mem 0xfff80000-0xfffeffff]
[    0.229873] system 00:0e: [mem 0x000cf000-0x000cffff] has been reserved
[    0.229876] system 00:0e: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.229879] system 00:0e: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.229882] system 00:0e: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.229885] system 00:0e: [mem 0xcfef0000-0xcffeffff] could not be reserved
[    0.229887] system 00:0e: [mem 0xfed00000-0xfed000ff] has been reserved
[    0.229890] system 00:0e: [mem 0xcfee0000-0xcfefffff] could not be reserved
[    0.229893] system 00:0e: [mem 0xffff0000-0xffffffff] has been reserved
[    0.229895] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.229898] system 00:0e: [mem 0x00100000-0xcfedffff] could not be reserved
[    0.229901] system 00:0e: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.229904] system 00:0e: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.229907] system 00:0e: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.229910] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.229917] pnp: PnP ACPI: found 15 devices
[    0.229918] ACPI: ACPI bus type pnp unregistered
[    0.235957] PCI: max bus depth: 1 pci_try_num: 2
[    0.235978] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.235981] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.235984] pci 0000:00:02.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.235988] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.236015] pci 0000:02:00.0: BAR 6: assigned [mem 0xfdc00000-0xfdc1ffff pref]
[    0.236018] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.236020] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.236023] pci 0000:00:07.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.236026] pci 0000:00:07.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.236032] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.236035] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    0.236040] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.236045] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff pref]
[    0.236057] pci 0000:00:02.0: setting latency timer to 64
[    0.236062] pci 0000:00:07.0: setting latency timer to 64
[    0.236070] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.236072] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.236075] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.236077] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.236079] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xfebfffff]
[    0.236081] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.236084] pci_bus 0000:01: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.236086] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.236088] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.236091] pci_bus 0000:02: resource 1 [mem 0xfdf00000-0xfdffffff]
[    0.236093] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.236096] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.236098] pci_bus 0000:03: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.236100] pci_bus 0000:03: resource 2 [mem 0xfdd00000-0xfddfffff pref]
[    0.236102] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.236104] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.236107] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.236109] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    0.236111] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xfebfffff]
[    0.236162] NET: Registered protocol family 2
[    0.236338] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.238059] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.243647] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.244343] TCP: Hash tables configured (established 524288 bind 65536)
[    0.244346] TCP reno registered
[    0.244362] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.244414] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.244586] NET: Registered protocol family 1
[    0.456069] pci 0000:01:00.0: Boot video device
[    0.456084] PCI: CLS 32 bytes, default 64
[    0.457001] PCI-DMA: Disabling AGP.
[    0.457093] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    0.457094] PCI-DMA: using GART IOMMU.
[    0.457098] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.460768] audit: initializing netlink socket (disabled)
[    0.460781] type=2000 audit(1319601643.456:1): initialized
[    0.496452] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.528461] VFS: Disk quotas dquot_6.5.2
[    0.528526] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.529156] fuse init (API version 7.16)
[    0.529244] msgmni has been set to 7891
[    0.529604] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.529636] io scheduler noop registered
[    0.529638] io scheduler deadline registered
[    0.529684] io scheduler cfq registered (default)
[    0.529832] pcieport 0000:00:02.0: setting latency timer to 64
[    0.529861] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.529935] pcieport 0000:00:07.0: setting latency timer to 64
[    0.529955] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
[    0.530014] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.530037] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.530168] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.530174] ACPI: Power Button [PWRB]
[    0.530218] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.530221] ACPI: Power Button [PWRF]
[    0.530273] ACPI: Fan [FAN] (on)
[    0.530279] ACPI: acpi_idle registered with cpuidle
[    0.531769] ACPI Warning: For \_TZ_.THRM._PSL: Return Package has no elements (empty) (20110413/nspredef-456)
[    0.531775] ACPI: [Package] has zero elements (ffff880126ca5ac0)
[    0.531777] ACPI: Invalid passive threshold
[    0.531949] thermal LNXTHERM:00: registered as thermal_zone0
[    0.531952] ACPI: Thermal Zone [THRM] (40 C)
[    0.531974] ERST: Table is not found!
[    0.532113] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.552610] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.605445] Freeing initrd memory: 13224k freed
[    0.688614] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.688922] Linux agpgart interface v0.103
[    0.690035] brd: module loaded
[    0.690565] loop: module loaded
[    0.690885] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.691344] Fixed MDIO Bus: probed
[    0.691369] PPP generic driver version 2.4.2
[    0.691415] tun: Universal TUN/TAP device driver, 1.6
[    0.691417] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.691512] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.691571] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.691601] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.691667] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.691702] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.691717] ehci_hcd 0000:00:13.5: debug port 1
[    0.691753] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
[    0.700021] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.700152] hub 1-0:1.0: USB hub found
[    0.700157] hub 1-0:1.0: 10 ports detected
[    0.700265] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.700318] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.700335] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.700375] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.700407] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[    0.760097] hub 2-0:1.0: USB hub found
[    0.760103] hub 2-0:1.0: 2 ports detected
[    0.760225] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.760238] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.760281] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.760311] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
[    0.820097] hub 3-0:1.0: USB hub found
[    0.820103] hub 3-0:1.0: 2 ports detected
[    0.820218] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.820231] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.820266] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.820298] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
[    0.880095] hub 4-0:1.0: USB hub found
[    0.880101] hub 4-0:1.0: 2 ports detected
[    0.880208] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.880221] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.880259] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.880275] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
[    0.940092] hub 5-0:1.0: USB hub found
[    0.940099] hub 5-0:1.0: 2 ports detected
[    0.940198] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.940210] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    0.940259] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    0.940277] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
[    1.000095] hub 6-0:1.0: USB hub found
[    1.000101] hub 6-0:1.0: 2 ports detected
[    1.000175] uhci_hcd: USB Universal Host Controller Interface driver
[    1.000264] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.000660] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.000665] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.000734] mousedev: PS/2 mouse device common for all mice
[    1.000837] rtc_cmos 00:04: RTC can wake from S4
[    1.000935] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.000971] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.001077] device-mapper: uevent: version 1.0.3
[    1.001142] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.001151] cpuidle: using governor ladder
[    1.001152] cpuidle: using governor menu
[    1.001154] EFI Variables Facility v0.08 2004-May-17
[    1.001390] TCP cubic registered
[    1.001507] NET: Registered protocol family 10
[    1.002026] NET: Registered protocol family 17
[    1.002044] Registering the dns_resolver key type
[    1.002155] PM: Hibernation image not present or could not be loaded.
[    1.002166] registered taskstats version 1
[    1.013429] usb 1-3: new high speed USB device number 2 using ehci_hcd
[    1.023314]   Magic number: 15:361:10
[    1.023322] hub 5-0:1.0: hash matches
[    1.023433] rtc_cmos 00:04: setting system clock to 2011-10-26 04:00:45 UTC (1319601645)
[    1.023441] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ (2 cpu cores) (version 2.20.00)
[    1.023487] powernow-k8: fid 0x12 (2600 MHz), vid 0x8
[    1.023489] powernow-k8: fid 0x10 (2400 MHz), vid 0xa
[    1.023490] powernow-k8: fid 0xe (2200 MHz), vid 0xc
[    1.023492] powernow-k8: fid 0xc (2000 MHz), vid 0xe
[    1.023493] powernow-k8: fid 0xa (1800 MHz), vid 0x10
[    1.023495] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.023537] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.023538] EDD information not available.
[    1.025305] Freeing unused kernel memory: 984k freed
[    1.025761] Write protecting the kernel read-only data: 10240k
[    1.025964] Freeing unused kernel memory: 20k freed
[    1.030512] Freeing unused kernel memory: 1400k freed
[    1.033083] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.054202] udevd[114]: starting version 173
[    1.122098] ahci 0000:00:12.0: version 3.0
[    1.122133] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.122163] ahci 0000:00:12.0: ASUS M2A-VM: enabling 64bit DMA
[    1.122275] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.122278] ahci 0000:00:12.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.126146] scsi0 : ahci
[    1.127123] scsi1 : ahci
[    1.127900] scsi2 : ahci
[    1.128712] scsi3 : ahci
[    1.128863] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.128867] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.128871] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.128875] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    1.152775] r8168 Gigabit Ethernet driver 8.025.00-NAPI loaded
[    1.152822] r8168 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.152845] r8168 0000:02:00.0: setting latency timer to 64
[    1.152918] r8168 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.153774] eth%d: RTL8168B/8111B at 0xffffc9000064a000, 00:1f:c6:b5:5f:62, IRQ 42
[    1.159050] Floppy drive(s): fd0 is 1.44M
[    1.175985] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    1.175989] eth0: Identified chip type is 'RTL8168B/8111B'.
[    1.175992] r8168  Copyright (C) 2011  Realtek NIC software team <nicfae@realtek.com> 
[    1.175993]  This program comes with ABSOLUTELY NO WARRANTY; for details, please see <http://www.gnu.org/licenses/>. 
[    1.175994]  This is free software, and you are welcome to redistribute it under certain conditions; see <http://www.gnu.org/licenses/>. 
[    1.179773] scsi4 : pata_atiixp
[    1.180383] scsi5 : pata_atiixp
[    1.180718] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    1.180720] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    1.187003] FDC 0 is a post-1991 82077
[    1.215799] usbcore: registered new interface driver uas
[    1.316617] Initializing USB Mass Storage driver...
[    1.316936] scsi6 : usb-storage 1-3:1.0
[    1.317106] scsi7 : usb-storage 1-3:1.1
[    1.317190] usbcore: registered new interface driver usb-storage
[    1.317192] USB Mass Storage support registered.
[    1.448040] ata2: SATA link down (SStatus 0 SControl 300)
[    1.448077] ata3: SATA link down (SStatus 0 SControl 300)
[    1.452037] ata4: SATA link down (SStatus 0 SControl 300)
[    1.732018] ata1: softreset failed (device not ready)
[    1.732022] ata1: applying SB600 PMP SRST workaround and retrying
[    1.904026] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.906152] ata1.00: ATA-8: WDC WD2500BEVT-60ZCT1, 13.01A13, max UDMA/100
[    1.906155] ata1.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.906159] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.908779] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.908781] ata1.00: configured for UDMA/100
[    1.908938] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-6 13.0 PQ: 0 ANSI: 5
[    1.909122] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.909150] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.909229] sd 0:0:0:0: [sda] Write Protect is off
[    1.909231] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.909252] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.955574]  sda: sda1 sda2 < sda5 >
[    1.955924] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.960492] firewire_ohci 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.024101] firewire_ohci: Added fw-ohci device 0000:03:07.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    2.257800] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.319525] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[    2.321378] scsi 7:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[    2.436515] sr0: scsi-1 drive
[    2.436519] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.436625] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    2.436687] sr 6:0:0:0: Attached scsi generic sg1 type 5
[    2.436908] sd 7:0:0:0: Attached scsi generic sg2 type 0
[    2.445394] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[    2.524132] firewire_core: created device fw0: GUID 0011d8000185e0f5, S400
[   14.035266] udevd[355]: starting version 173
[   14.107917] lp: driver loaded but no devices found
[   14.125291] Adding 4191228k swap on /dev/sda5.  Priority:-1 extents:1 across:4191228k 
[   14.141873] [drm] Initialized drm 1.1.0 20060810
[   14.198667] type=1400 audit(1319601658.670:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=433 comm="apparmor_parser"
[   14.199086] type=1400 audit(1319601658.670:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=433 comm="apparmor_parser"
[   14.199354] type=1400 audit(1319601658.670:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=433 comm="apparmor_parser"
[   14.202231] type=1400 audit(1319601658.674:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=493 comm="apparmor_parser"
[   14.241349] parport_pc 00:0a: reported by Plug and Play ACPI
[   14.241408] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   14.286999] [drm] radeon defaulting to kernel modesetting.
[   14.287004] [drm] radeon kernel modesetting enabled.
[   14.291520] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.291526] radeon 0000:01:00.0: setting latency timer to 64
[   14.291768] [drm] initializing kernel modesetting (RV610 0x1002:0x94C3 0x1462:0x1041).
[   14.291798] [drm] register mmio base: 0xFDBF0000
[   14.291800] [drm] register mmio size: 65536
[   14.292174] ATOM BIOS: 113
[   14.292202] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
[   14.292204] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
[   14.292416] [drm] Detected VRAM RAM=256M, BAR=256M
[   14.292421] [drm] RAM width 64bits DDR
[   14.295438] [TTM] Zone  kernel: Available graphics memory: 2028072 kiB.
[   14.295441] [TTM] Initializing pool allocator.
[   14.295474] [drm] radeon: 256M of VRAM memory ready
[   14.295476] [drm] radeon: 512M of GTT memory ready.
[   14.295494] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.295496] [drm] Driver supports precise vblank timestamp query.
[   14.295541] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
[   14.295546] radeon 0000:01:00.0: radeon: using MSI.
[   14.295580] [drm] radeon: irq initialized.
[   14.295587] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   14.298013] [drm] Loading RV610 Microcode
[   14.326863] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   14.327378] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   14.327457] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   14.331059] lp0: using parport0 (interrupt-driven).
[   14.334636] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.400515] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   14.401772] MCE: In-kernel MCE decoding enabled.
[   14.403810] EDAC MC: Ver: 2.1.0
[   14.414032] AMD64 EDAC driver v3.4.0
[   14.421434] EDAC amd64: DRAM ECC disabled.
[   14.421442] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   14.421443]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   14.421445]  (Note that use of the override may cause unknown side effects.)
[   14.439154] IR NEC protocol handler initialized
[   14.442253] saa7146: register extension 'budget_ci dvb'.
[   14.448583] IR RC5(x) protocol handler initialized
[   14.465556] IR RC6 protocol handler initialized
[   14.466139] budget_ci dvb 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   14.466225] saa7146: found saa7146 @ mem ffffc90000662000 (revision 1, irq 20) (0x13c2,0x101a).
[   14.466233] saa7146 (0): dma buffer size 192512
[   14.466235] DVB: registering new adapter (TT-Budget C-1501 PCI)
[   14.470575] RPC: Registered named UNIX socket transport module.
[   14.470579] RPC: Registered udp transport module.
[   14.470581] RPC: Registered tcp transport module.
[   14.470582] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   14.480882] FS-Cache: Loaded
[   14.489604] IR JVC protocol handler initialized
[   14.495949] FS-Cache: Netfs 'nfs' registered for caching
[   14.498442] IR Sony protocol handler initialized
[   14.505418] adapter has MAC addr = 00:d0:5c:c6:4e:d9
[   14.508634] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   14.513864] lirc_dev: IR Remote Control driver registered, major 250 
[   14.514084] IR LIRC bridge handler initialized
[   14.536104] Registered IR keymap rc-tt-1500
[   14.536195] input: Budget-CI dvb ir receiver saa7146 (0) as /devices/pci0000:00/0000:00:14.4/0000:03:05.0/rc/rc0/input3
[   14.536271] rc0: Budget-CI dvb ir receiver saa7146 (0) as /devices/pci0000:00/0000:00:14.4/0000:03:05.0/rc/rc0
[   14.578666] DVB: registering adapter 0 frontend 0 (Philips TDA10023 DVB-C)...
[   14.586483] budget_ci dvb 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.586563] saa7146: found saa7146 @ mem ffffc90000676000 (revision 1, irq 21) (0x13c2,0x101a).
[   14.586570] saa7146 (1): dma buffer size 192512
[   14.586573] DVB: registering new adapter (TT-Budget C-1501 PCI)
[   14.621009] adapter has MAC addr = 00:d0:5c:c6:50:56
[   14.621427] Registered IR keymap rc-tt-1500
[   14.621498] input: Budget-CI dvb ir receiver saa7146 (1) as /devices/pci0000:00/0000:00:14.4/0000:03:06.0/rc/rc1/input4
[   14.621535] rc1: Budget-CI dvb ir receiver saa7146 (1) as /devices/pci0000:00/0000:00:14.4/0000:03:06.0/rc/rc1
[   14.621949] DVB: registering adapter 1 frontend 0 (Philips TDA10023 DVB-C)...
[   14.786339] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.849064] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   14.863500] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.035908] r8168: eth0: link down
[   15.036956] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.039499] ppdev: user-space parallel port driver
[   15.097457] type=1400 audit(1319601659.570:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1021 comm="apparmor_parser"
[   15.097501] type=1400 audit(1319601659.570:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1022 comm="apparmor_parser"
[   15.099495] type=1400 audit(1319601659.570:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1022 comm="apparmor_parser"
[   15.099772] type=1400 audit(1319601659.570:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1022 comm="apparmor_parser"
[   15.105563] type=1400 audit(1319601659.578:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/dhcpd" pid=1023 comm="apparmor_parser"
[   15.110849] type=1400 audit(1319601659.582:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1024 comm="apparmor_parser"
[   15.124723] radeon 0000:01:00.0: WB enabled
[   15.155788] [drm] ring test succeeded in 1 usecs
[   15.155922] [drm] radeon: ib pool ready.
[   15.156051] [drm] ib test succeeded in 0 usecs
[   15.156060] failed to evaluate ATIF got AE_BAD_PARAMETER
[   15.157309] [drm] Radeon Display Connectors
[   15.157312] [drm] Connector 0:
[   15.157314] [drm]   VGA
[   15.157316] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   15.157318] [drm]   Encoders:
[   15.157319] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   15.157320] [drm] Connector 1:
[   15.157322] [drm]   DIN
[   15.157323] [drm]   Encoders:
[   15.157324] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   15.157325] [drm] Connector 2:
[   15.157326] [drm]   DVI-I
[   15.157327] [drm]   HPD1
[   15.157329] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   15.157331] [drm]   Encoders:
[   15.157332] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.157333] [drm]     DFP1: INTERNAL_LVTM1
[   15.167481] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[   15.222188] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   15.222192] Raw EDID:
[   15.222195] <3>00 ff ff ff ff ff ff 00 4c 2d d2 38 32 32 4e 50  ........L-.822NP
[   15.222198] <3>0a 0d 01 03 0f 28 1e 5a eb 02 99 a0 57 49 99 26  .....(.Z....WI.&
[   15.222200] <3>13 48 4c ff ff 80 31 40 45 59 61 59 81 99 a9 4f  .HL...1@EYaY...O
[   15.222202] <3>a9 59 ff ff ff ff ff ff ff ff ff ff ff ff ff ff  .Y..............
[   15.222204] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.222206] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.222208] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.222210] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.222212] 
[   15.229187] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   15.282744] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   15.282748] Raw EDID:
[   15.282751] <3>00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff  ................
[   15.282753] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.282755] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.282757] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.282759] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.282761] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.282763] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.282765] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.282767] 
[   15.367569] init: failsafe main process (726) killed by TERM signal
[   15.370322] init: apport pre-start process (1142) terminated with status 1
[   15.410161] init: apport post-stop process (1196) terminated with status 1
[   15.413883] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 13
[   15.413887] Raw EDID:
[   15.413889] <3>00 ff ff ff ff ff ff 00 4c 2d d2 38 32 32 9d ff  ........L-.822..
[   15.413892] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.413894] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.413896] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.413898] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.413900] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.413902] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.413904] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   15.413905] 
```

And here is my lspci -v
```
$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 826d
	Flags: bus master, 66MHz, medium devsel, latency 64

00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device 81ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: ASUSTeK Computer Inc. Device 81ef
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 81ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f900 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 8249
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: ASUSTeK Computer Inc. Device 81ef
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fdd00000-fddfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO] (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device 1041
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdbf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at de00 [size=256]
	Expansion ROM at fdbc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5B
	Flags: bus master, fast devsel, latency 0, IRQ 42
	I/O ports at ee00 [size=256]
	Memory at fdfff000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8168
	Kernel modules: r8168

03:05.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
	Subsystem: Technotrend Systemtechnik GmbH Device 101a
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fdeff000 (32-bit, non-prefetchable) [size=512]
	Kernel driver in use: budget_ci dvb
	Kernel modules: budget-ci

03:06.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
	Subsystem: Technotrend Systemtechnik GmbH Device 101a
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at fdefe000 (32-bit, non-prefetchable) [size=512]
	Kernel driver in use: budget_ci dvb
	Kernel modules: budget-ci

03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. M4A series motherboard
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at fdefd000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at cf00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
```

Thank you for any help.

---

### Post by JoeFriday49 on 2011-10-26
Let me guess...  You don't have a HDMI monitor plugged into your video card...

---

### Post by tieri on 2011-10-27
> **JoeFriday49 said:**
> Let me guess...  You don't have a HDMI monitor plugged into your video card...

No I do have not. The computer is HTPC server running mythbuntu and mythtvbackend, whit intention to use only CRT-TV (PAL-60) for now. Maby in the future I have the money to buy a flat screen whit HDMI.
For time being, I have also another CRT connected, so it would be easier to configure things.

Have I missed something whit my configuration? I am quite new whit this. Had random freezing, found the error in dmesg and syslog. Googled this and symptoms fit.

---

### Post by rdratlos on 2011-10-27
> **tieri said:**
> No I do have not. The computer is HTPC server running mythbuntu and mythtvbackend, whit intention to use only CRT-TV (PAL-60) for now. Maby in the future I have the money to buy a flat screen whit HDMI.
For time being, I have also another CRT connected, so it would be easier to configure things.

Have I missed something whit my configuration? I am quite new whit this. Had random freezing, found the error in dmesg and syslog. Googled this and symptoms fit.

From the logs it seems to be a problem  with your monitor that is connected to the TV output. As you can see  there is always a correct EDID header from the monitor: "0x00 0xFF 0xFF  0xFF 0xFF 0xFF 0xFF 0x00" but floating EDID data. This is usually caused  by bugs in the monitor's EPROM. The kernel patch, even if modified,  won't help you, as it removes the connector.

It seems that you  have a Samsung monitor connected, that was manufactured in 2003. Have  you tried to connect it to the VGA connector and see if it works there?

---

### Post by JoeFriday49 on 2011-10-27
> **tieri said:**
> No I do have not. >>  Have I missed something whit my configuration?

No unfortunately you have not missed anything.  This is a problem with the kernel and has been around for a looong time now...  You can fix your problem by simply plugging in a HDMI monitor.  Mine will have to wait on the kernel fix as my card doesn't have a HDMI jack, but it does contain a chipset that thinks it has one...  

If only the code could be patched to poll for errors once and then quit everything would be fine.

---

### Post by rdratlos on 2011-10-29
> **JoeFriday49 said:**
> 
If only the code could be patched to poll for errors once and then quit everything would be fine.

So why don't you just ask? We've solved this problem for a couple of boards now. 

Just follow the hints of my post of September 5th and you'll get a patched kernel version. If you already have Ubuntu Oneiric you just need to post dmesg and the output of lspci -v. If you have a previous Ubuntu version, please install the patched PPA kernel beforehand.

---

### Post by myhonor on 2011-12-08
> **rdratlos said:**
> In Launchpad PPA you will find a 2.6.32 and 2.6.35 test kernel for Ubuntu lucid, where I've  included the Asus M2A-VM patch. Could you please test it and provide me  feedback? 

Test kernel installation procedure:
Add following two lines to file** /etc/apt/sources.list**:

```
deb [http://ppa.launchpad.net/rdratlos/ppa-asusfix/ubuntu](http://ppa.launchpad.net/rdratlos/ppa-asusfix/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/rdratlos/ppa-asusfix/ubuntu](http://ppa.launchpad.net/rdratlos/ppa-asusfix/ubuntu) lucid main 
```Add PPA key to your apt keyring:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 61B873BC
```     Add new test kernel version (2.6.32-33.71+lp722806v1 or 2.6.35-25.44~lucid1+lp722806v1):
```
sudo apt-get update
sudo apt-get upgrade
```After reboot please check dmesg for the correct kernel version and the  drm log entries. There should be four EDID dumps in the log after the  Radeon connectors list and then ... SILENCE. Good luck!
As soon as you have the new dmesg log, please post it.

Is someone still here?I have the same problems too,and I installed ubuntu 11.04. Also my mother board is ASUS m2a-vm,and I use an old philips 17'' CRT with VGA interface with DVI interface idled. Unfortunately my dormitory PC couldn't connect the key server.Actually I couldn't log on any website outside of china!******* GFW!

---

### Post by rdratlos on 2011-12-09
> **myhonor said:**
> Is someone still here?I have the same problems too,and I installed ubuntu 11.04. Also my mother board is ASUS m2a-vm,and I use an old philips 17'' CRT with VGA interface with DVI interface idled. Unfortunately my dormitory PC couldn't connect the key server.Actually I couldn't log on any website outside of china!******* GFW!

We're still there. For Ubuntu 11.04 please follow the instructions in: [http://ubuntuforums.org/showpost.php?p=11048430&postcount=33](http://ubuntuforums.org/showpost.php?p=11048430&postcount=33)
without the i2c stuff. Then provide us with your logs. Of course you need access to Launchpad and Ubuntu servers.

---

### Post by didli on 2011-12-18
> **rdratlos said:**
> During discussion of the kernel driver patch above, Jean Delvare and Alex Deucher from the linux kernel team gave some valuable hints that lead me to a trivial workaround for our problem, until a kernel patch will finally solve it 
(...) Hope this helps you.
Oooooh YES it helps me ! Eventually ! No more headaches ... 
It works straight, no flashing/spamming damned stupid EDID thing anymore ... aaaaah ...
I should buy, for you, Jean Delvare and Alex Deucher, some coffee :) 
Amazing little trick.

---

### Post by cfr42 on 2011-12-28
I am seeing what I think is the same problem. I'm running Linux Mint 12:
```

Linux <computer name> 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

I tried the modprobe.d/options.conf work around but that didn't help although I think I got slightly different output to the logs.

Does anybody know if I can use any of the solutions posted here? Since this is a kernel problem and I'm basically running Ubuntu, that would make sense to me but I'm not sure of the details.

I will post dmesg etc. output but what I'm seeing isn't as detailed as the logs which other people have posted. I'm not sure if this is because I need to install the ppa fix to get that output - or if I even can do that on Mint - or if there's something else I'm missing.

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-14-generic root=UUID=0becc0a5-8e99-45a7-836a-d63a7d67791d ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6d1000 - 00000000bf94a000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf94a000 - 00000000bfb4d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfb4d000 - 00000000bfd1a000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd1a000 - 00000000bfd66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd66000 - 00000000bfd70000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfd70000 - 00000000bfd73000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd73000 - 00000000bfd74000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd74000 - 00000000bfeac000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfeac000 - 00000000bfebd000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfebd000 - 00000000bfecb000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfecb000 - 00000000bfecc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfecc000 - 00000000bfedc000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfedc000 - 00000000bfedd000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfedd000 - 00000000bfede000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfede000 - 00000000bfee4000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfee4000 - 00000000bfef7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfef7000 - 00000000bff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed61000 - 00000000fed71000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed80000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100001000 - 000000021f000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: System manufacturer System Product Name/F1A75-V EVO, BIOS 0404 06/13/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x21f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF00000000 write-back
[    0.000000]   1 base 00BFF00000 mask FFFFF00000 uncachable
[    0.000000]   2 base 00C0000000 mask FFC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000023f000000 aka 9200M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3071MB, range: 1MB, type UC
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 3071M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbff00 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcfd0] fcfd0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000bff00000
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bff00000 page 4k
[    0.000000] kernel direct mapping tables up to bff00000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000021f000000
[    0.000000]  0100000000 - 0200000000 page 1G
[    0.000000]  0200000000 - 021f000000 page 2M
[    0.000000] kernel direct mapping tables up to 21f000000 @ bfefe000-bff00000
[    0.000000] RAMDISK: 365b0000 - 372d0000
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000bfd66068 00054 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000bfd6d648 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110413/tbfadt-560)
[    0.000000] ACPI: DSDT 00000000bfd66150 074F1 (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bfedef80 00040
[    0.000000] ACPI: APIC 00000000bfd6d740 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000bfd6d7b8 0003C (v01 A M I  GMCH945. 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bfd6d7f8 00038 (v01 ALASKA    A M I 01072009 AMI  00000004)
[    0.000000] ACPI: SSDT 00000000bfd6d830 007FE (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 00000000bfd6e030 01923 (v02    AMD     ALIB 00000001 MSFT 04000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000021f000000
[    0.000000] Initmem setup node 0 0000000000000000-000000021f000000
[    0.000000]   NODE_DATA [000000021effb000 - 000000021effffff]
[    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880216e00000-ffff88021d7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0021f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf6d1
[    0.000000]     0: 0x000bfb4d -> 0x000bfd1a
[    0.000000]     0: 0x000bfd73 -> 0x000bfd74
[    0.000000]     0: 0x000bfef7 -> 0x000bff00
[    0.000000]     0: 0x00100001 -> 0x0021f000
[    0.000000] On node 0 totalpages: 1959989
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 766176 pages, LIFO batch:31
[    0.000000]   Normal zone: 16072 pages used for memmap
[    0.000000]   Normal zone: 1159479 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 3, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf6d1000 - 00000000bf94a000
[    0.000000] PM: Registered nosave memory: 00000000bf94a000 - 00000000bfb4d000
[    0.000000] PM: Registered nosave memory: 00000000bfd1a000 - 00000000bfd66000
[    0.000000] PM: Registered nosave memory: 00000000bfd66000 - 00000000bfd70000
[    0.000000] PM: Registered nosave memory: 00000000bfd70000 - 00000000bfd73000
[    0.000000] PM: Registered nosave memory: 00000000bfd74000 - 00000000bfeac000
[    0.000000] PM: Registered nosave memory: 00000000bfeac000 - 00000000bfebd000
[    0.000000] PM: Registered nosave memory: 00000000bfebd000 - 00000000bfecb000
[    0.000000] PM: Registered nosave memory: 00000000bfecb000 - 00000000bfecc000
[    0.000000] PM: Registered nosave memory: 00000000bfecc000 - 00000000bfedc000
[    0.000000] PM: Registered nosave memory: 00000000bfedc000 - 00000000bfedd000
[    0.000000] PM: Registered nosave memory: 00000000bfedd000 - 00000000bfede000
[    0.000000] PM: Registered nosave memory: 00000000bfede000 - 00000000bfee4000
[    0.000000] PM: Registered nosave memory: 00000000bfee4000 - 00000000bfef7000
[    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed01000
[    0.000000] PM: Registered nosave memory: 00000000fed01000 - 00000000fed61000
[    0.000000] PM: Registered nosave memory: 00000000fed61000 - 00000000fed71000
[    0.000000] PM: Registered nosave memory: 00000000fed71000 - 00000000fed80000
[    0.000000] PM: Registered nosave memory: 00000000fed80000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 0000000100000000 - 0000000100001000
[    0.000000] Allocating PCI resources starting at bff00000 (gap: bff00000:20100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88021ec00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1929576
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-14-generic root=UUID=0becc0a5-8e99-45a7-836a-d63a7d67791d ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7637916k/8896512k available (6109k kernel code, 1056556k absent, 202040k reserved, 4876k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 62914560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2699.852 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5399.70 BogoMIPS (lpj=10799408)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004031] Security Framework initialized
[    0.004044] AppArmor: AppArmor initialized
[    0.004047] Yama: becoming mindful.
[    0.004695] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.006772] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.008317] Mount-cache hash table entries: 256
[    0.008428] Initializing cgroup subsys cpuacct
[    0.008434] Initializing cgroup subsys memory
[    0.008443] Initializing cgroup subsys devices
[    0.008446] Initializing cgroup subsys freezer
[    0.008449] Initializing cgroup subsys net_cls
[    0.008452] Initializing cgroup subsys blkio
[    0.008458] Initializing cgroup subsys perf_event
[    0.008483] tseg: 00bff00000
[    0.008485] CPU: Physical Processor ID: 0
[    0.008487] CPU: Processor Core ID: 0
[    0.008490] mce: CPU supports 6 MCE banks
[    0.010750] ACPI: Core revision 20110413
[    0.016011] ftrace: allocating 25647 entries in 101 pages
[    0.020339] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.060539] CPU0: AMD A4-3400 APU with Radeon(tm) HD Graphics stepping 00
[    0.064003] Performance Events: AMD PMU driver.
[    0.064003] ... version:                0
[    0.064003] ... bit width:              48
[    0.064003] ... generic registers:      4
[    0.064003] ... value mask:             0000ffffffffffff
[    0.064003] ... max period:             00007fffffffffff
[    0.064003] ... fixed-purpose events:   0
[    0.064003] ... event mask:             000000000000000f
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 99000
[    0.152017] Brought up 2 CPUs
[    0.152020] Total of 2 processors activated (10800.00 BogoMIPS).
[    0.152349] devtmpfs: initialized
[    0.152349] PM: Registering ACPI NVS region at bf94a000 (2109440 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfd1a000 (311296 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfd70000 (12288 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfeac000 (69632 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfecb000 (4096 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfedc000 (4096 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfede000 (24576 bytes)
[    0.153201] print_constraints: dummy: 
[    0.153221] Time:  1:58:19  Date: 12/28/11
[    0.153255] NET: Registered protocol family 16
[    0.153265] Trying to unpack rootfs image as initramfs...
[    0.153412] Extended Config Space enabled on 0 nodes
[    0.153432] ACPI: bus type pci registered
[    0.153480] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.153486] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.188040] PCI: Using configuration type 1 for base access
[    0.188681] bio: create slab <bio-0> at 0
[    0.188991] ACPI: EC: Look up EC in DSDT
[    0.189855] ACPI: Executed 1 blocks of module-level executable AML code
[    0.192996] ACPI Error: [RAMB] Namespace lookup failure, AE_NOT_FOUND (20110413/psargs-359)
[    0.193005] ACPI Exception: AE_NOT_FOUND, Could not execute arguments for [RAMW] (Region) (20110413/nsinit-349)
[    0.193370] ACPI: Interpreter enabled
[    0.193374] ACPI: (supports S0 S3 S4 S5)
[    0.193391] ACPI: Using IOAPIC for interrupt routing
[    0.326512] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    0.326682] ACPI: No dock devices found.
[    0.326685] HEST: Table not found.
[    0.326689] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.326932] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.327118] pci_root PNP0A03:00: host bridge window [io  0x0000-0x03af]
[    0.327122] pci_root PNP0A03:00: host bridge window [io  0x03e0-0x0cf7]
[    0.327125] pci_root PNP0A03:00: host bridge window [io  0x03b0-0x03df]
[    0.327128] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.327132] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.327136] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.327139] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xffffffff]
[    0.327153] pci 0000:00:00.0: [1022:1705] type 0 class 0x000600
[    0.327189] pci 0000:00:01.0: [1002:9644] type 0 class 0x000300
[    0.327198] pci 0000:00:01.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.327204] pci 0000:00:01.0: reg 14: [io  0xf000-0xf0ff]
[    0.327210] pci 0000:00:01.0: reg 18: [mem 0xfeb00000-0xfeb3ffff]
[    0.327243] pci 0000:00:01.0: supports D1 D2
[    0.327259] pci 0000:00:01.1: [1002:1714] type 0 class 0x000403
[    0.327267] pci 0000:00:01.1: reg 10: [mem 0xfeb44000-0xfeb47fff]
[    0.327308] pci 0000:00:01.1: supports D1 D2
[    0.327329] pci 0000:00:04.0: [1022:1709] type 1 class 0x000604
[    0.327371] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.327374] pci 0000:00:04.0: PME# disabled
[    0.327392] pci 0000:00:05.0: [1022:170a] type 1 class 0x000604
[    0.327433] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.327436] pci 0000:00:05.0: PME# disabled
[    0.327453] pci 0000:00:06.0: [1022:170b] type 1 class 0x000604
[    0.327494] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.327497] pci 0000:00:06.0: PME# disabled
[    0.327515] pci 0000:00:07.0: [1022:170c] type 1 class 0x000604
[    0.327556] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.327559] pci 0000:00:07.0: PME# disabled
[    0.327599] pci 0000:00:10.0: [1022:7812] type 0 class 0x000c03
[    0.327619] pci 0000:00:10.0: reg 10: [mem 0xfeb4a000-0xfeb4bfff 64bit]
[    0.327700] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
[    0.327705] pci 0000:00:10.0: PME# disabled
[    0.327741] pci 0000:00:10.1: [1022:7812] type 0 class 0x000c03
[    0.327760] pci 0000:00:10.1: reg 10: [mem 0xfeb48000-0xfeb49fff 64bit]
[    0.327842] pci 0000:00:10.1: PME# supported from D0 D3hot D3cold
[    0.327846] pci 0000:00:10.1: PME# disabled
[    0.327878] pci 0000:00:11.0: [1022:7800] type 0 class 0x000101
[    0.327894] pci 0000:00:11.0: reg 10: [io  0xf190-0xf197]
[    0.327903] pci 0000:00:11.0: reg 14: [io  0xf180-0xf183]
[    0.327913] pci 0000:00:11.0: reg 18: [io  0xf170-0xf177]
[    0.327922] pci 0000:00:11.0: reg 1c: [io  0xf160-0xf163]
[    0.327931] pci 0000:00:11.0: reg 20: [io  0xf150-0xf15f]
[    0.327940] pci 0000:00:11.0: reg 24: [mem 0xfeb51000-0xfeb517ff]
[    0.327960] pci 0000:00:11.0: set SATA to AHCI mode
[    0.327987] pci 0000:00:12.0: [1022:7807] type 0 class 0x000c03
[    0.328035] pci 0000:00:12.0: reg 10: [mem 0xfeb50000-0xfeb50fff]
[    0.328103] pci 0000:00:12.2: [1022:7808] type 0 class 0x000c03
[    0.328121] pci 0000:00:12.2: reg 10: [mem 0xfeb4f000-0xfeb4f0ff]
[    0.328189] pci 0000:00:12.2: supports D1 D2
[    0.328190] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.328194] pci 0000:00:12.2: PME# disabled
[    0.328214] pci 0000:00:13.0: [1022:7807] type 0 class 0x000c03
[    0.328227] pci 0000:00:13.0: reg 10: [mem 0xfeb4e000-0xfeb4efff]
[    0.328294] pci 0000:00:13.2: [1022:7808] type 0 class 0x000c03
[    0.328313] pci 0000:00:13.2: reg 10: [mem 0xfeb4d000-0xfeb4d0ff]
[    0.328380] pci 0000:00:13.2: supports D1 D2
[    0.328381] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.328385] pci 0000:00:13.2: PME# disabled
[    0.328405] pci 0000:00:14.0: [1022:780b] type 0 class 0x000c05
[    0.328475] pci 0000:00:14.1: [1022:780c] type 0 class 0x000101
[    0.328488] pci 0000:00:14.1: reg 10: [io  0xf140-0xf147]
[    0.328498] pci 0000:00:14.1: reg 14: [io  0xf130-0xf133]
[    0.328507] pci 0000:00:14.1: reg 18: [io  0xf120-0xf127]
[    0.328516] pci 0000:00:14.1: reg 1c: [io  0xf110-0xf113]
[    0.328525] pci 0000:00:14.1: reg 20: [io  0xf100-0xf10f]
[    0.328560] pci 0000:00:14.2: [1022:780d] type 0 class 0x000403
[    0.328581] pci 0000:00:14.2: reg 10: [mem 0xfeb40000-0xfeb43fff 64bit]
[    0.328636] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.328640] pci 0000:00:14.2: PME# disabled
[    0.328652] pci 0000:00:14.3: [1022:780e] type 0 class 0x000601
[    0.328724] pci 0000:00:14.4: [1022:780f] type 1 class 0x000604
[    0.328762] pci 0000:00:14.5: [1022:7809] type 0 class 0x000c03
[    0.328775] pci 0000:00:14.5: reg 10: [mem 0xfeb4c000-0xfeb4cfff]
[    0.328840] pci 0000:00:18.0: [1022:1700] type 0 class 0x000600
[    0.328871] pci 0000:00:18.1: [1022:1701] type 0 class 0x000600
[    0.328898] pci 0000:00:18.2: [1022:1702] type 0 class 0x000600
[    0.328929] pci 0000:00:18.3: [1022:1703] type 0 class 0x000600
[    0.328964] pci 0000:00:18.4: [1022:1704] type 0 class 0x000600
[    0.328991] pci 0000:00:18.5: [1022:1718] type 0 class 0x000600
[    0.329019] pci 0000:00:18.6: [1022:1716] type 0 class 0x000600
[    0.329046] pci 0000:00:18.7: [1022:1719] type 0 class 0x000600
[    0.329128] pci 0000:01:00.0: [168c:002b] type 0 class 0x000280
[    0.329146] pci 0000:01:00.0: reg 10: [mem 0xfea00000-0xfea0ffff 64bit]
[    0.329216] pci 0000:01:00.0: supports D1
[    0.329217] pci 0000:01:00.0: PME# supported from D0 D1 D3hot
[    0.329221] pci 0000:01:00.0: PME# disabled
[    0.336053] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.336065] pci 0000:00:04.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.336069] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.336073] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.336131] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.336147] pci 0000:02:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.336170] pci 0000:02:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.336186] pci 0000:02:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.336230] pci 0000:02:00.0: supports D1 D2
[    0.336232] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.336236] pci 0000:02:00.0: PME# disabled
[    0.344054] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.344065] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
[    0.344069] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.344074] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.344143] pci 0000:03:00.0: [1b21:1042] type 0 class 0x000c03
[    0.344165] pci 0000:03:00.0: reg 10: [mem 0xfe900000-0xfe907fff 64bit]
[    0.344254] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.344259] pci 0000:03:00.0: PME# disabled
[    0.352054] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.352065] pci 0000:00:06.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.352069] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.352074] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.352138] pci 0000:04:00.0: [1b21:0612] type 0 class 0x000106
[    0.352153] pci 0000:04:00.0: reg 10: [io  0xd050-0xd057]
[    0.352162] pci 0000:04:00.0: reg 14: [io  0xd040-0xd043]
[    0.352172] pci 0000:04:00.0: reg 18: [io  0xd030-0xd037]
[    0.352181] pci 0000:04:00.0: reg 1c: [io  0xd020-0xd023]
[    0.352190] pci 0000:04:00.0: reg 20: [io  0xd000-0xd01f]
[    0.352199] pci 0000:04:00.0: reg 24: [mem 0xfe800000-0xfe8001ff]
[    0.360059] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    0.360070] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
[    0.360073] pci 0000:00:07.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.360078] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.360144] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
[    0.360149] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.360154] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.360158] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.360160] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.360162] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.360164] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.360166] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.360168] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.360170] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.360172] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.360196] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.360390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.360412] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.360435] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.360453] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.360472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.360599]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.360745]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.364675] ACPI: PCI Interrupt Link [LN24] (IRQs *24)
[    0.364703] ACPI: PCI Interrupt Link [LN25] (IRQs *25)
[    0.364728] ACPI: PCI Interrupt Link [LN26] (IRQs *26)
[    0.364752] ACPI: PCI Interrupt Link [LN27] (IRQs *27)
[    0.364775] ACPI: PCI Interrupt Link [LN28] (IRQs *28)
[    0.364799] ACPI: PCI Interrupt Link [LN29] (IRQs *29)
[    0.364822] ACPI: PCI Interrupt Link [LN30] (IRQs *30)
[    0.364846] ACPI: PCI Interrupt Link [LN31] (IRQs *31)
[    0.364870] ACPI: PCI Interrupt Link [LN32] (IRQs *32)
[    0.364893] ACPI: PCI Interrupt Link [LN33] (IRQs *33)
[    0.364917] ACPI: PCI Interrupt Link [LN34] (IRQs *34)
[    0.364941] ACPI: PCI Interrupt Link [LN35] (IRQs *35)
[    0.364964] ACPI: PCI Interrupt Link [LN36] (IRQs *36)
[    0.364988] ACPI: PCI Interrupt Link [LN37] (IRQs *37)
[    0.365012] ACPI: PCI Interrupt Link [LN38] (IRQs *38)
[    0.365036] ACPI: PCI Interrupt Link [LN39] (IRQs *39)
[    0.365063] ACPI: PCI Interrupt Link [LN40] (IRQs *40)
[    0.365087] ACPI: PCI Interrupt Link [LN41] (IRQs *41)
[    0.365110] ACPI: PCI Interrupt Link [LN42] (IRQs *42)
[    0.365134] ACPI: PCI Interrupt Link [LN43] (IRQs *43)
[    0.365158] ACPI: PCI Interrupt Link [LN44] (IRQs *44)
[    0.365182] ACPI: PCI Interrupt Link [LN45] (IRQs *45)
[    0.365206] ACPI: PCI Interrupt Link [LN46] (IRQs *46)
[    0.365230] ACPI: PCI Interrupt Link [LN47] (IRQs *47)
[    0.365254] ACPI: PCI Interrupt Link [LN48] (IRQs *48)
[    0.365281] ACPI: PCI Interrupt Link [LN49] (IRQs *49)
[    0.365307] ACPI: PCI Interrupt Link [LN50] (IRQs *50)
[    0.365331] ACPI: PCI Interrupt Link [LN51] (IRQs *51)
[    0.365356] ACPI: PCI Interrupt Link [LN52] (IRQs *52)
[    0.365380] ACPI: PCI Interrupt Link [LN53] (IRQs *53)
[    0.365404] ACPI: PCI Interrupt Link [LN54] (IRQs *54)
[    0.365428] ACPI: PCI Interrupt Link [LN55] (IRQs *55)
[    0.365456] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 7 10 11 14 15) *0
[    0.365506] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 5 7 10 11 14 15) *0
[    0.365556] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 10 11 14 15) *0
[    0.365605] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 5 7 10 11 14 15) *0
[    0.365645] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 10 11 14 15) *0
[    0.365676] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 10 11 14 15) *0
[    0.365706] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 5 7 10 11 14 15) *0
[    0.365737] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 7 10 11 14 15) *0
[    0.365821] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.365835] vgaarb: loaded
[    0.365838] vgaarb: bridge control possible 0000:00:01.0
[    0.365974] SCSI subsystem initialized
[    0.366039] libata version 3.00 loaded.
[    0.366072] usbcore: registered new interface driver usbfs
[    0.366081] usbcore: registered new interface driver hub
[    0.366101] usbcore: registered new device driver usb
[    0.366165] PCI: Using ACPI for IRQ routing
[    0.366747] Freeing initrd memory: 13440k freed
[    0.374469] PCI: pci_cache_line_size set to 64 bytes
[    0.374567] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.374569] reserve RAM buffer: 00000000bf6d1000 - 00000000bfffffff 
[    0.374572] reserve RAM buffer: 00000000bfd1a000 - 00000000bfffffff 
[    0.374575] reserve RAM buffer: 00000000bfd74000 - 00000000bfffffff 
[    0.374578] reserve RAM buffer: 00000000bff00000 - 00000000bfffffff 
[    0.374579] reserve RAM buffer: 000000021f000000 - 000000021fffffff 
[    0.374652] NetLabel: Initializing
[    0.374655] NetLabel:  domain hash size = 128
[    0.374658] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.374670] NetLabel:  unlabeled traffic allowed by default
[    0.374708] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.374713] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.376036] Switching to clocksource hpet
[    0.379285] Switched to NOHz mode on CPU #0
[    0.379422] Switched to NOHz mode on CPU #1
[    0.380578] AppArmor: AppArmor Filesystem Enabled
[    0.380609] pnp: PnP ACPI init
[    0.380624] ACPI: bus type pnp registered
[    0.380761] pnp 00:00: [bus 00-ff]
[    0.380764] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.380766] pnp 00:00: [io  0x0000-0x03af window]
[    0.380768] pnp 00:00: [io  0x03e0-0x0cf7 window]
[    0.380769] pnp 00:00: [io  0x03b0-0x03df window]
[    0.380771] pnp 00:00: [io  0x0d00-0xffff window]
[    0.380773] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.380774] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.380776] pnp 00:00: [mem 0xc0000000-0xffffffff window]
[    0.380778] pnp 00:00: [mem 0x00000000 window]
[    0.380835] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.380861] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.380906] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.380911] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.381074] pnp 00:02: [io  0x0010-0x001f]
[    0.381076] pnp 00:02: [io  0x0022-0x003f]
[    0.381077] pnp 00:02: [io  0x0063]
[    0.381079] pnp 00:02: [io  0x0065]
[    0.381080] pnp 00:02: [io  0x0067-0x006f]
[    0.381082] pnp 00:02: [io  0x0072-0x007f]
[    0.381083] pnp 00:02: [io  0x0080]
[    0.381084] pnp 00:02: [io  0x0084-0x0086]
[    0.381088] pnp 00:02: [io  0x0088]
[    0.381089] pnp 00:02: [io  0x008c-0x008e]
[    0.381090] pnp 00:02: [io  0x0090-0x009f]
[    0.381092] pnp 00:02: [io  0x00a2-0x00bf]
[    0.381093] pnp 00:02: [io  0x00b1]
[    0.381094] pnp 00:02: [io  0x00e0-0x00ef]
[    0.381096] pnp 00:02: [io  0x04d0-0x04d1]
[    0.381097] pnp 00:02: [io  0x040b]
[    0.381098] pnp 00:02: [io  0x04d6]
[    0.381100] pnp 00:02: [io  0x0c00-0x0c01]
[    0.381101] pnp 00:02: [io  0x0c14]
[    0.381102] pnp 00:02: [io  0x0c50-0x0c51]
[    0.381104] pnp 00:02: [io  0x0c52]
[    0.381105] pnp 00:02: [io  0x0c6c]
[    0.381106] pnp 00:02: [io  0x0c6f]
[    0.381107] pnp 00:02: [io  0x0cd0-0x0cd1]
[    0.381109] pnp 00:02: [io  0x0cd2-0x0cd3]
[    0.381110] pnp 00:02: [io  0x0cd4-0x0cd5]
[    0.381112] pnp 00:02: [io  0x0cd6-0x0cd7]
[    0.381113] pnp 00:02: [io  0x0cd8-0x0cdf]
[    0.381114] pnp 00:02: [io  0x0800-0x089f]
[    0.381116] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.381118] pnp 00:02: [io  0x0000-0x000f]
[    0.381119] pnp 00:02: [io  0x0b20-0x0b3f]
[    0.381121] pnp 00:02: [io  0x0900-0x090f]
[    0.381122] pnp 00:02: [io  0x0910-0x091f]
[    0.381123] pnp 00:02: [io  0xfe00-0xfefe]
[    0.381125] pnp 00:02: [io  0x0060-0x005f disabled]
[    0.381126] pnp 00:02: [io  0x0064-0x0063 disabled]
[    0.381128] pnp 00:02: [mem 0xfec00000-0xfec00fff]
[    0.381130] pnp 00:02: [mem 0xfee00000-0xfee00fff]
[    0.381131] pnp 00:02: [mem 0xfed80000-0xfed8ffff]
[    0.381133] pnp 00:02: [mem 0xfed61000-0xfed70fff]
[    0.381134] pnp 00:02: [mem 0xfec10000-0xfec10fff]
[    0.381136] pnp 00:02: [mem 0xfed00000-0xfed00fff]
[    0.381137] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.381212] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.381216] system 00:02: [io  0x040b] has been reserved
[    0.381219] system 00:02: [io  0x04d6] has been reserved
[    0.381222] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.381225] system 00:02: [io  0x0c14] has been reserved
[    0.381228] system 00:02: [io  0x0c50-0x0c51] has been reserved
[    0.381231] system 00:02: [io  0x0c52] has been reserved
[    0.381234] system 00:02: [io  0x0c6c] has been reserved
[    0.381236] system 00:02: [io  0x0c6f] has been reserved
[    0.381239] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.381243] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.381246] system 00:02: [io  0x0cd4-0x0cd5] has been reserved
[    0.381249] system 00:02: [io  0x0cd6-0x0cd7] has been reserved
[    0.381252] system 00:02: [io  0x0cd8-0x0cdf] has been reserved
[    0.381257] system 00:02: [io  0x0800-0x089f] has been reserved
[    0.381260] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    0.381263] system 00:02: [io  0x0900-0x090f] has been reserved
[    0.381267] system 00:02: [io  0x0910-0x091f] has been reserved
[    0.381270] system 00:02: [io  0xfe00-0xfefe] has been reserved
[    0.381274] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.381277] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.381281] system 00:02: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.381285] system 00:02: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.381288] system 00:02: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.381291] system 00:02: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.381295] system 00:02: [mem 0xff000000-0xffffffff] has been reserved
[    0.381299] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.381385] pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
[    0.381387] pnp 00:03: [io  0x0300-0x031f]
[    0.381388] pnp 00:03: [io  0x0290-0x029f]
[    0.381390] pnp 00:03: [io  0x0230-0x023f]
[    0.381419] system 00:03: [io  0x0300-0x031f] has been reserved
[    0.381422] system 00:03: [io  0x0290-0x029f] has been reserved
[    0.381426] system 00:03: [io  0x0230-0x023f] has been reserved
[    0.381429] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.381440] pnp 00:04: [dma 4]
[    0.381441] pnp 00:04: [io  0x0000-0x000f]
[    0.381445] pnp 00:04: [io  0x0081-0x0083]
[    0.381446] pnp 00:04: [io  0x0087]
[    0.381447] pnp 00:04: [io  0x0089-0x008b]
[    0.381449] pnp 00:04: [io  0x008f]
[    0.381450] pnp 00:04: [io  0x00c0-0x00df]
[    0.381466] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.381473] pnp 00:05: [io  0x0070-0x0071]
[    0.381483] pnp 00:05: [irq 8]
[    0.381498] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.381503] pnp 00:06: [io  0x0061]
[    0.381520] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.381537] pnp 00:07: [io  0x0010-0x001f]
[    0.381539] pnp 00:07: [io  0x0022-0x003f]
[    0.381540] pnp 00:07: [io  0x0044-0x005f]
[    0.381541] pnp 00:07: [io  0x0072-0x007f]
[    0.381543] pnp 00:07: [io  0x0080]
[    0.381544] pnp 00:07: [io  0x0084-0x0086]
[    0.381546] pnp 00:07: [io  0x0088]
[    0.381547] pnp 00:07: [io  0x008c-0x008e]
[    0.381549] pnp 00:07: [io  0x0090-0x009f]
[    0.381550] pnp 00:07: [io  0x00a2-0x00bf]
[    0.381551] pnp 00:07: [io  0x00e0-0x00ef]
[    0.381553] pnp 00:07: [io  0x04d0-0x04d1]
[    0.381587] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.381591] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.381597] pnp 00:08: [io  0x00f0-0x00ff]
[    0.381600] pnp 00:08: [irq 13]
[    0.381616] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.381653] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.381791] pnp 00:0a: [io  0x03f8-0x03ff]
[    0.381794] pnp 00:0a: [irq 4]
[    0.381796] pnp 00:0a: [dma 0 disabled]
[    0.381838] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.382117] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.382156] pnp 00:0b: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.382161] pnp: PnP ACPI: found 12 devices
[    0.382164] ACPI: ACPI bus type pnp unregistered
[    0.387683] PCI: max bus depth: 1 pci_try_num: 2
[    0.387716] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.387721] pci 0000:00:04.0:   bridge window [io  disabled]
[    0.387726] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.387730] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    0.387736] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.387740] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
[    0.387744] pci 0000:00:05.0:   bridge window [mem disabled]
[    0.387749] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.387755] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.387757] pci 0000:00:06.0:   bridge window [io  disabled]
[    0.387762] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.387767] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.387772] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    0.387776] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
[    0.387780] pci 0000:00:07.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.387785] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    0.387790] pci 0000:00:14.4: PCI bridge to [bus 05-05]
[    0.387793] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.387798] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.387803] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.387827] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.387833] pci 0000:00:04.0: setting latency timer to 64
[    0.387841] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.387845] pci 0000:00:05.0: setting latency timer to 64
[    0.387852] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.387857] pci 0000:00:06.0: setting latency timer to 64
[    0.387863] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.387868] pci 0000:00:07.0: setting latency timer to 64
[    0.387875] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.387877] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.387879] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.387881] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.387883] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.387884] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.387886] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
[    0.387888] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.387890] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.387892] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.387894] pci_bus 0000:03: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.387896] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.387898] pci_bus 0000:04: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.387900] pci_bus 0000:05: resource 4 [io  0x0000-0x03af]
[    0.387902] pci_bus 0000:05: resource 5 [io  0x03e0-0x0cf7]
[    0.387903] pci_bus 0000:05: resource 6 [io  0x03b0-0x03df]
[    0.387905] pci_bus 0000:05: resource 7 [io  0x0d00-0xffff]
[    0.387907] pci_bus 0000:05: resource 8 [mem 0x000a0000-0x000bffff]
[    0.387909] pci_bus 0000:05: resource 9 [mem 0x000c0000-0x000dffff]
[    0.387910] pci_bus 0000:05: resource 10 [mem 0xc0000000-0xffffffff]
[    0.387942] NET: Registered protocol family 2
[    0.388145] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.389288] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.391598] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.391893] TCP: Hash tables configured (established 524288 bind 65536)
[    0.391898] TCP reno registered
[    0.391914] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.391977] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.392120] NET: Registered protocol family 1
[    0.392135] pci 0000:00:01.0: Boot video device
[    0.984152] PCI: CLS 64 bytes, default 64
[    0.984161] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.984177] Placing 64MB software IO TLB between ffff8800bb6d1000 - ffff8800bf6d1000
[    0.984190] software IO TLB at phys 0xbb6d1000 - 0xbf6d1000
[    0.984505] audit: initializing netlink socket (disabled)
[    0.984517] type=2000 audit(1325037498.980:1): initialized
[    1.016542] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.048812] VFS: Disk quotas dquot_6.5.2
[    1.048862] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.049395] fuse init (API version 7.16)
[    1.049484] msgmni has been set to 14944
[    1.050061] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.050097] io scheduler noop registered
[    1.050104] io scheduler deadline registered
[    1.050166] io scheduler cfq registered (default)
[    1.050271] pcieport 0000:00:04.0: setting latency timer to 64
[    1.050313] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    1.050367] pcieport 0000:00:05.0: setting latency timer to 64
[    1.050401] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    1.050447] pcieport 0000:00:06.0: setting latency timer to 64
[    1.050480] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    1.050525] pcieport 0000:00:07.0: setting latency timer to 64
[    1.050558] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
[    1.050625] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    1.050629] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.050634] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    1.050647] pcieport 0000:00:05.0: Signaling PME through PCIe PME interrupt
[    1.050650] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.050655] pcie_pme 0000:00:05.0:pcie01: service driver pcie_pme loaded
[    1.050667] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
[    1.050670] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.050675] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
[    1.050688] pcieport 0000:00:07.0: Signaling PME through PCIe PME interrupt
[    1.050691] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    1.050696] pcie_pme 0000:00:07.0:pcie01: service driver pcie_pme loaded
[    1.050707] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.050726] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.050833] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.050840] ACPI: Power Button [PWRB]
[    1.050869] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.050873] ACPI: Power Button [PWRF]
[    1.050898] ACPI: acpi_idle registered with cpuidle
[    1.085168] ERST: Table is not found!
[    1.085251] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.105630] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.181057] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.181414] Linux agpgart interface v0.103
[    1.182202] brd: module loaded
[    1.182526] loop: module loaded
[    1.182672] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.182708] pata_acpi 0000:00:14.1: PCI INT B disabled
[    1.182908] Fixed MDIO Bus: probed
[    1.182925] PPP generic driver version 2.4.2
[    1.182963] tun: Universal TUN/TAP device driver, 1.6
[    1.182966] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.183029] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.183043] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.183071] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.183108] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.183118] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.183143] QUIRK: Enable AMD PLL fix
[    1.183153] ehci_hcd 0000:00:12.2: debug port 1
[    1.183177] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfeb4f000
[    1.192106] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.192330] hub 1-0:1.0: USB hub found
[    1.192335] hub 1-0:1.0: 5 ports detected
[    1.192401] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.192425] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.192455] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.192464] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.192485] ehci_hcd 0000:00:13.2: debug port 1
[    1.192501] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfeb4d000
[    1.204336] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.204563] hub 2-0:1.0: USB hub found
[    1.204568] hub 2-0:1.0: 5 ports detected
[    1.204634] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.204655] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.204680] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.204711] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.204739] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfeb50000
[    1.264442] hub 3-0:1.0: USB hub found
[    1.264453] hub 3-0:1.0: 5 ports detected
[    1.264520] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.264545] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.264573] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.264594] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfeb4e000
[    1.324442] hub 4-0:1.0: USB hub found
[    1.324452] hub 4-0:1.0: 5 ports detected
[    1.324521] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.324546] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.324576] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
[    1.324595] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfeb4c000
[    1.384440] hub 5-0:1.0: USB hub found
[    1.384451] hub 5-0:1.0: 2 ports detected
[    1.384511] uhci_hcd: USB Universal Host Controller Interface driver
[    1.384572] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.385002] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.385015] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.385118] mousedev: PS/2 mouse device common for all mice
[    1.385193] rtc_cmos 00:05: RTC can wake from S4
[    1.385265] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.385285] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.385370] device-mapper: uevent: version 1.0.3
[    1.385424] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.385462] cpuidle: using governor ladder
[    1.385530] cpuidle: using governor menu
[    1.385533] EFI Variables Facility v0.08 2004-May-17
[    1.385710] TCP cubic registered
[    1.385793] NET: Registered protocol family 10
[    1.386151] NET: Registered protocol family 17
[    1.386168] Registering the dns_resolver key type
[    1.386252] PM: Hibernation image not present or could not be loaded.
[    1.386261] registered taskstats version 1
[    1.408215]   Magic number: 7:686:964
[    1.408293] rtc_cmos 00:05: setting system clock to 2011-12-28 01:58:20 UTC (1325037500)
[    1.408307] powernow-k8: Found 1 AMD A4-3400 APU with Radeon(tm) HD Graphics (2 cpu cores) (version 2.20.00)
[    1.408366] powernow-k8:    0 : pstate 0 (2700 MHz)
[    1.408369] powernow-k8:    1 : pstate 1 (2400 MHz)
[    1.408371] powernow-k8:    2 : pstate 2 (2200 MHz)
[    1.408373] powernow-k8:    3 : pstate 3 (2000 MHz)
[    1.408376] powernow-k8:    4 : pstate 4 (1800 MHz)
[    1.408378] powernow-k8:    5 : pstate 5 (1400 MHz)
[    1.408381] powernow-k8:    6 : pstate 6 (1100 MHz)
[    1.408383] powernow-k8:    7 : pstate 7 (800 MHz)
[    1.408564] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.408568] EDD information not available.
[    1.409974] Freeing unused kernel memory: 984k freed
[    1.410210] Write protecting the kernel read-only data: 10240k
[    1.410377] Freeing unused kernel memory: 16k freed
[    1.413969] Freeing unused kernel memory: 1396k freed
[    1.432766] udevd[80]: starting version 173
[    1.478362] xhci_hcd 0000:00:10.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.478389] xhci_hcd 0000:00:10.0: setting latency timer to 64
[    1.478393] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.478461] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    1.478656] xhci_hcd 0000:00:10.0: irq 18, io mem 0xfeb4a000
[    1.478712] xhci_hcd 0000:00:10.0: irq 44 for MSI/MSI-X
[    1.478716] xhci_hcd 0000:00:10.0: irq 45 for MSI/MSI-X
[    1.478720] xhci_hcd 0000:00:10.0: irq 46 for MSI/MSI-X
[    1.478846] xHCI xhci_add_endpoint called for root hub
[    1.478848] xHCI xhci_check_bandwidth called for root hub
[    1.478869] hub 6-0:1.0: USB hub found
[    1.478877] hub 6-0:1.0: 2 ports detected
[    1.478931] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.478956] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
[    1.502984] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.503010] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.503052] r8169 0000:02:00.0: setting latency timer to 64
[    1.503058] r8169 0000:02:00.0: (unregistered net_device): unknown MAC, using family default
[    1.503122] r8169 0000:02:00.0: irq 47 for MSI/MSI-X
[    1.503461] r8169 0000:02:00.0: eth0: RTL8168b/8111b at 0xffffc90000c7e000, 14:da:e9:1d:5c:ca, XID 0c900800 IRQ 47
[    1.508224] xHCI xhci_add_endpoint called for root hub
[    1.508227] xHCI xhci_check_bandwidth called for root hub
[    1.508252] hub 7-0:1.0: USB hub found
[    1.508266] hub 7-0:1.0: 2 ports detected
[    1.508343] pata_atiixp 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.511103] scsi0 : pata_atiixp
[    1.514156] scsi1 : pata_atiixp
[    1.514276] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf100 irq 14
[    1.514280] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf108 irq 15
[    1.514434] ahci 0000:00:11.0: version 3.0
[    1.514445] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.514555] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.514560] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.516820] scsi2 : ahci
[    1.518402] scsi3 : ahci
[    1.520472] scsi4 : ahci
[    1.522416] scsi5 : ahci
[    1.522643] ata3: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51100 irq 19
[    1.522649] ata4: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51180 irq 19
[    1.522654] ata5: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51200 irq 19
[    1.522658] ata6: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51280 irq 19
[    1.522710] ahci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.522774] ahci 0000:04:00.0: irq 48 for MSI/MSI-X
[    1.522802] ahci: SSS flag set, parallel bus scan disabled
[    1.522828] ahci 0000:04:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.522833] ahci 0000:04:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    1.522840] ahci 0000:04:00.0: setting latency timer to 64
[    1.523090] xhci_hcd 0000:00:10.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.523113] xhci_hcd 0000:00:10.1: setting latency timer to 64
[    1.523116] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.523181] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
[    1.523369] xhci_hcd 0000:00:10.1: irq 17, io mem 0xfeb48000
[    1.523421] xhci_hcd 0000:00:10.1: irq 49 for MSI/MSI-X
[    1.523425] xhci_hcd 0000:00:10.1: irq 50 for MSI/MSI-X
[    1.523428] xhci_hcd 0000:00:10.1: irq 51 for MSI/MSI-X
[    1.523549] xHCI xhci_add_endpoint called for root hub
[    1.523551] xHCI xhci_check_bandwidth called for root hub
[    1.523571] hub 8-0:1.0: USB hub found
[    1.523578] hub 8-0:1.0: 2 ports detected
[    1.523631] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.523654] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
[    1.526866] xHCI xhci_add_endpoint called for root hub
[    1.526868] xHCI xhci_check_bandwidth called for root hub
[    1.526886] hub 9-0:1.0: USB hub found
[    1.526896] hub 9-0:1.0: 2 ports detected
[    1.526952] xhci_hcd 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.526973] xhci_hcd 0000:03:00.0: setting latency timer to 64
[    1.526976] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.527002] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 10
[    1.534086] scsi6 : ahci
[    1.536621] xhci_hcd 0000:03:00.0: irq 18, io mem 0xfe900000
[    1.536665] xhci_hcd 0000:03:00.0: irq 52 for MSI/MSI-X
[    1.536669] xhci_hcd 0000:03:00.0: irq 53 for MSI/MSI-X
[    1.536672] xhci_hcd 0000:03:00.0: irq 54 for MSI/MSI-X
[    1.536773] xHCI xhci_add_endpoint called for root hub
[    1.536774] xHCI xhci_check_bandwidth called for root hub
[    1.536797] hub 10-0:1.0: USB hub found
[    1.536803] hub 10-0:1.0: 2 ports detected
[    1.536844] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.536871] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 11
[    1.536951] xHCI xhci_add_endpoint called for root hub
[    1.536952] xHCI xhci_check_bandwidth called for root hub
[    1.536968] hub 11-0:1.0: USB hub found
[    1.536974] hub 11-0:1.0: 2 ports detected
[    1.537113] scsi7 : ahci
[    1.537178] ata7: SATA max UDMA/133 abar m512@0xfe800000 port 0xfe800100 irq 48
[    1.537184] ata8: SATA max UDMA/133 abar m512@0xfe800000 port 0xfe800180 irq 48
[    1.684407] ata2.00: ATAPI: HL-DT-ST DVDRAM GH22LS50, TL03, max UDMA/100
[    1.684430] ata2.00: limited to UDMA/33 due to 40-wire cable
[    1.700693] ata2.00: configured for UDMA/33
[    1.711032] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22LS50  TL03 PQ: 0 ANSI: 5
[    1.712118] usb 3-2: new low speed USB device number 2 using ohci_hcd
[    1.721101] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.721122] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.721294] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.721351] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.856056] ata3: SATA link down (SStatus 0 SControl 300)
[    1.856119] ata7: SATA link down (SStatus 0 SControl 300)
[    1.856170] ata5: SATA link down (SStatus 0 SControl 300)
[    1.856219] ata6: SATA link down (SStatus 0 SControl 300)
[    1.895728] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input2
[    1.895810] generic-usb 0003:046D:C31D.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:12.0-2/input0
[    1.906568] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input3
[    1.906678] generic-usb 0003:046D:C31D.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:12.0-2/input1
[    1.906696] usbcore: registered new interface driver usbhid
[    1.906699] usbhid: USB HID core driver
[    1.984340] Refined TSC clocksource calibration: 2700.200 MHz.
[    1.984361] Switching to clocksource tsc
[    2.028347] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.028654] ata4.00: ATA-8: CRUCIAL_CT64M225, 2030, max UDMA/133
[    2.028661] ata4.00: 125045424 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.029680] ata4.00: configured for UDMA/133
[    2.030044] scsi 3:0:0:0: Direct-Access     ATA      CRUCIAL_CT64M225 2030 PQ: 0 ANSI: 5
[    2.030226] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.030324] sd 3:0:0:0: [sda] 125045424 512-byte logical blocks: (64.0 GB/59.6 GiB)
[    2.030504] sd 3:0:0:0: [sda] Write Protect is off
[    2.030510] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.030539] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.032748]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7
[    2.033145] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.208339] usb 4-2: new low speed USB device number 2 using ohci_hcd
[    2.348119] ata8: SATA link down (SStatus 0 SControl 300)
[    2.388707] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb4/4-2/4-2:1.0/input/input4
[    2.388853] generic-usb 0003:046D:C03E.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-2/input0
[    2.423602] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.590250] init: ureadahead main process (311) terminated with status 5
[    2.716070] udevd[351]: starting version 173
[    2.751494] Adding 1635324k swap on /dev/sda4.  Priority:-1 extents:1 across:1635324k SS
[    2.796433] lp: driver loaded but no devices found
[    2.863423] wmi: Mapper loaded
[    2.866215] [drm] Initialized drm 1.1.0 20060810
[    2.870394] cfg80211: Calling CRDA to update world regulatory domain
[    2.900362] [drm] radeon defaulting to kernel modesetting.
[    2.900366] [drm] radeon kernel modesetting enabled.
[    2.900430] radeon 0000:00:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.900434] radeon 0000:00:01.0: setting latency timer to 64
[    2.900808] [drm] initializing kernel modesetting (SUMO2 0x1002:0x9644 0x1043:0x84C8).
[    2.900865] [drm] register mmio base: 0xFEB00000
[    2.900867] [drm] register mmio size: 262144
[    2.900961] ATOM BIOS: General
[    2.900990] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    2.900992] radeon 0000:00:01.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[    2.901125] [drm] Detected VRAM RAM=512M, BAR=256M
[    2.901129] [drm] RAM width 32bits DDR
[    2.906935] [TTM] Zone  kernel: Available graphics memory: 3826876 kiB.
[    2.906947] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    2.906948] [TTM] Initializing pool allocator.
[    2.907055] [drm] radeon: 512M of VRAM memory ready
[    2.907057] [drm] radeon: 512M of GTT memory ready.
[    2.907072] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.907074] [drm] Driver supports precise vblank timestamp query.
[    2.908650] radeon 0000:00:01.0: irq 55 for MSI/MSI-X
[    2.908657] radeon 0000:00:01.0: radeon: using MSI.
[    2.909051] [drm] radeon: irq initialized.
[    2.909057] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.910736] [drm] Loading SUMO2 Microcode
[    2.916548] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.916572] ath9k 0000:01:00.0: setting latency timer to 64
[    2.968579] ath: EEPROM regdomain: 0x809c
[    2.968582] ath: EEPROM indicates we should expect a country code
[    2.968584] ath: doing EEPROM country->regdmn map search
[    2.968585] ath: country maps to regdmn code: 0x52
[    2.968587] ath: Country alpha2 being used: CN
[    2.968588] ath: Regpair used: 0x52
[    2.971233] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    2.971238] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971240] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    2.971242] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971244] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    2.971246] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971247] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    2.971249] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971251] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    2.971253] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971254] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    2.971256] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971258] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    2.971259] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971261] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    2.971263] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971264] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    2.971266] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971268] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    2.971270] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971271] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    2.971273] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.971275] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    2.971277] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    2.971278] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    3.025725] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.025729] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025731] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.025734] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025735] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.025737] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025739] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.025741] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025742] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.025744] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025746] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.025748] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025749] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.025751] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025753] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.025755] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025756] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.025758] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025760] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.025762] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025763] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.025765] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025767] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.025769] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025770] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    3.025772] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.025774] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    3.025776] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.086210] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    3.111994] ip_tables: (C) 2000-2006 Netfilter Core Team
[    3.127369] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    3.131117] cfg80211: Pending regulatory request, waiting for it to be processed...
[    3.132618] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    3.133692] Registered led device: ath9k-phy0
[    3.133700] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90011820000, irq=16
[    3.151534] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    3.159862] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.175849] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    3.195792] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    3.297146] asus_wmi: ASUS WMI generic driver loaded
[    3.322734] asus_wmi: Initialization: 0x0
[    3.322756] asus_wmi: BIOS WMI version: 0.9
[    3.322791] asus_wmi: SFUN value: 0x0
[    3.327582] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input5
[    3.375457] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.375462] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375464] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.375466] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375468] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.375470] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375471] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.375473] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375475] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.375477] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375478] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.375480] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375482] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.375484] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375485] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.375487] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375489] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.375490] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375492] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.375494] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375495] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.375497] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375499] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.375501] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375502] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    3.375504] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375506] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    3.375508] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.375511] cfg80211: World regulatory domain updated:
[    3.375513] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    3.375515] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.375516] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.375518] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.375520] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.375529] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.375545] cfg80211: Calling CRDA for country: CN
[    3.379363] radeon 0000:00:01.0: WB enabled
[    3.395494] [drm] ring test succeeded in 1 usecs
[    3.395587] [drm] radeon: ib pool ready.
[    3.395647] [drm] ib test succeeded in 0 usecs
[    3.395654] failed to evaluate ATIF got AE_BAD_PARAMETER
[    3.396729] [drm:radeon_dp_i2c_aux_ch] *ERROR* aux i2c too many retries, giving up
[    3.396844] [drm:radeon_dp_i2c_aux_ch] *ERROR* aux i2c too many retries, giving up
[    3.396877] [drm] Radeon Display Connectors
[    3.396878] [drm] Connector 0:
[    3.396879] [drm]   VGA
[    3.396880] [drm]   HPD2
[    3.396882] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    3.396883] [drm]   Encoders:
[    3.396884] [drm]     CRT1: INTERNAL_UNIPHY2
[    3.396885] [drm]     CRT1: NUTMEG
[    3.396886] [drm] Connector 1:
[    3.396887] [drm]   HDMI-A
[    3.396888] [drm]   HPD1
[    3.396890] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    3.396891] [drm]   Encoders:
[    3.396892] [drm]     DFP1: INTERNAL_UNIPHY2
[    3.396893] [drm] Connector 2:
[    3.396894] [drm]   DisplayPort
[    3.396895] [drm]   HPD3
[    3.396896] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[    3.396898] [drm]   Encoders:
[    3.396899] [drm]     DFP2: INTERNAL_UNIPHY
[    3.415485] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.415489] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415491] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.415493] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415495] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.415497] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415498] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.415500] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415502] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.415504] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415505] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.415507] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415509] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.415511] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415512] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.415514] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415516] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.415518] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415519] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.415521] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415523] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.415525] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415526] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.415528] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415530] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    3.415532] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.415533] cfg80211: Disabling freq 2484 MHz
[    3.415537] cfg80211: Regulatory domain changed to country: CN
[    3.415538] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    3.415540] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    3.415542] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[    3.731581] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.748669] r8169 0000:02:00.0: eth0: link down
[    3.749722] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.884037] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[    3.893934] [drm] Radeon display connector HDMI-A-1: No monitor connected or invalid EDID
[    4.148686] init: failsafe main process (698) killed by TERM signal
[    4.155914] init: alsa-restore main process (1096) terminated with status 19

```
Here's the output with the suggested work around for modprobe:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-14-generic root=UUID=0becc0a5-8e99-45a7-836a-d63a7d67791d ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6d1000 - 00000000bf94a000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf94a000 - 00000000bfb4d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfb4d000 - 00000000bfd1a000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd1a000 - 00000000bfd66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd66000 - 00000000bfd70000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfd70000 - 00000000bfd73000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd73000 - 00000000bfd74000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd74000 - 00000000bfeac000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfeac000 - 00000000bfebd000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfebd000 - 00000000bfecb000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfecb000 - 00000000bfecc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfecc000 - 00000000bfedc000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfedc000 - 00000000bfedd000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfedd000 - 00000000bfede000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfede000 - 00000000bfee4000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfee4000 - 00000000bfef7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfef7000 - 00000000bff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed61000 - 00000000fed71000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed80000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100001000 - 000000021f000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: System manufacturer System Product Name/F1A75-V EVO, BIOS 0404 06/13/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x21f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF00000000 write-back
[    0.000000]   1 base 00BFF00000 mask FFFFF00000 uncachable
[    0.000000]   2 base 00C0000000 mask FFC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000023f000000 aka 9200M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3071MB, range: 1MB, type UC
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 3071M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbff00 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcfd0] fcfd0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000bff00000
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bff00000 page 4k
[    0.000000] kernel direct mapping tables up to bff00000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000021f000000
[    0.000000]  0100000000 - 0200000000 page 1G
[    0.000000]  0200000000 - 021f000000 page 2M
[    0.000000] kernel direct mapping tables up to 21f000000 @ bfefe000-bff00000
[    0.000000] RAMDISK: 365b0000 - 372d0000
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000bfd66068 00054 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000bfd6d648 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110413/tbfadt-560)
[    0.000000] ACPI: DSDT 00000000bfd66150 074F1 (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bfedef80 00040
[    0.000000] ACPI: APIC 00000000bfd6d740 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000bfd6d7b8 0003C (v01 A M I  GMCH945. 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bfd6d7f8 00038 (v01 ALASKA    A M I 01072009 AMI  00000004)
[    0.000000] ACPI: SSDT 00000000bfd6d830 007FE (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 00000000bfd6e030 01923 (v02    AMD     ALIB 00000001 MSFT 04000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000021f000000
[    0.000000] Initmem setup node 0 0000000000000000-000000021f000000
[    0.000000]   NODE_DATA [000000021effb000 - 000000021effffff]
[    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880216e00000-ffff88021d7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0021f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf6d1
[    0.000000]     0: 0x000bfb4d -> 0x000bfd1a
[    0.000000]     0: 0x000bfd73 -> 0x000bfd74
[    0.000000]     0: 0x000bfef7 -> 0x000bff00
[    0.000000]     0: 0x00100001 -> 0x0021f000
[    0.000000] On node 0 totalpages: 1959989
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 766176 pages, LIFO batch:31
[    0.000000]   Normal zone: 16072 pages used for memmap
[    0.000000]   Normal zone: 1159479 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 3, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf6d1000 - 00000000bf94a000
[    0.000000] PM: Registered nosave memory: 00000000bf94a000 - 00000000bfb4d000
[    0.000000] PM: Registered nosave memory: 00000000bfd1a000 - 00000000bfd66000
[    0.000000] PM: Registered nosave memory: 00000000bfd66000 - 00000000bfd70000
[    0.000000] PM: Registered nosave memory: 00000000bfd70000 - 00000000bfd73000
[    0.000000] PM: Registered nosave memory: 00000000bfd74000 - 00000000bfeac000
[    0.000000] PM: Registered nosave memory: 00000000bfeac000 - 00000000bfebd000
[    0.000000] PM: Registered nosave memory: 00000000bfebd000 - 00000000bfecb000
[    0.000000] PM: Registered nosave memory: 00000000bfecb000 - 00000000bfecc000
[    0.000000] PM: Registered nosave memory: 00000000bfecc000 - 00000000bfedc000
[    0.000000] PM: Registered nosave memory: 00000000bfedc000 - 00000000bfedd000
[    0.000000] PM: Registered nosave memory: 00000000bfedd000 - 00000000bfede000
[    0.000000] PM: Registered nosave memory: 00000000bfede000 - 00000000bfee4000
[    0.000000] PM: Registered nosave memory: 00000000bfee4000 - 00000000bfef7000
[    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed01000
[    0.000000] PM: Registered nosave memory: 00000000fed01000 - 00000000fed61000
[    0.000000] PM: Registered nosave memory: 00000000fed61000 - 00000000fed71000
[    0.000000] PM: Registered nosave memory: 00000000fed71000 - 00000000fed80000
[    0.000000] PM: Registered nosave memory: 00000000fed80000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 0000000100000000 - 0000000100001000
[    0.000000] Allocating PCI resources starting at bff00000 (gap: bff00000:20100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88021ec00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1929576
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-14-generic root=UUID=0becc0a5-8e99-45a7-836a-d63a7d67791d ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7637916k/8896512k available (6109k kernel code, 1056556k absent, 202040k reserved, 4876k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 62914560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2700.075 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5400.15 BogoMIPS (lpj=10800300)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004032] Security Framework initialized
[    0.004045] AppArmor: AppArmor initialized
[    0.004048] Yama: becoming mindful.
[    0.004697] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.006765] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.008305] Mount-cache hash table entries: 256
[    0.008415] Initializing cgroup subsys cpuacct
[    0.008421] Initializing cgroup subsys memory
[    0.008429] Initializing cgroup subsys devices
[    0.008433] Initializing cgroup subsys freezer
[    0.008435] Initializing cgroup subsys net_cls
[    0.008439] Initializing cgroup subsys blkio
[    0.008445] Initializing cgroup subsys perf_event
[    0.008471] tseg: 00bff00000
[    0.008473] CPU: Physical Processor ID: 0
[    0.008475] CPU: Processor Core ID: 0
[    0.008478] mce: CPU supports 6 MCE banks
[    0.010735] ACPI: Core revision 20110413
[    0.016011] ftrace: allocating 25647 entries in 101 pages
[    0.020340] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.063644] CPU0: AMD A4-3400 APU with Radeon(tm) HD Graphics stepping 00
[    0.064003] Performance Events: AMD PMU driver.
[    0.064003] ... version:                0
[    0.064003] ... bit width:              48
[    0.064003] ... generic registers:      4
[    0.064003] ... value mask:             0000ffffffffffff
[    0.064003] ... max period:             00007fffffffffff
[    0.064003] ... fixed-purpose events:   0
[    0.064003] ... event mask:             000000000000000f
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 99000
[    0.152017] Brought up 2 CPUs
[    0.152020] Total of 2 processors activated (10800.45 BogoMIPS).
[    0.152349] devtmpfs: initialized
[    0.152349] PM: Registering ACPI NVS region at bf94a000 (2109440 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfd1a000 (311296 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfd70000 (12288 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfeac000 (69632 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfecb000 (4096 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfedc000 (4096 bytes)
[    0.152349] PM: Registering ACPI NVS region at bfede000 (24576 bytes)
[    0.153270] print_constraints: dummy: 
[    0.153290] Time: 22:44:55  Date: 12/28/11
[    0.153323] NET: Registered protocol family 16
[    0.153372] Trying to unpack rootfs image as initramfs...
[    0.153509] Extended Config Space enabled on 0 nodes
[    0.153529] ACPI: bus type pci registered
[    0.153581] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.153586] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.188078] PCI: Using configuration type 1 for base access
[    0.192080] bio: create slab <bio-0> at 0
[    0.193047] ACPI: EC: Look up EC in DSDT
[    0.193912] ACPI: Executed 1 blocks of module-level executable AML code
[    0.196134] ACPI Error: [RAMB] Namespace lookup failure, AE_NOT_FOUND (20110413/psargs-359)
[    0.196143] ACPI Exception: AE_NOT_FOUND, Could not execute arguments for [RAMW] (Region) (20110413/nsinit-349)
[    0.196516] ACPI: Interpreter enabled
[    0.196520] ACPI: (supports S0 S3 S4 S5)
[    0.196537] ACPI: Using IOAPIC for interrupt routing
[    0.314524] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    0.314692] ACPI: No dock devices found.
[    0.314695] HEST: Table not found.
[    0.314700] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.314937] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.315119] pci_root PNP0A03:00: host bridge window [io  0x0000-0x03af]
[    0.315123] pci_root PNP0A03:00: host bridge window [io  0x03e0-0x0cf7]
[    0.315127] pci_root PNP0A03:00: host bridge window [io  0x03b0-0x03df]
[    0.315130] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.315133] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.315137] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.315140] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xffffffff]
[    0.315156] pci 0000:00:00.0: [1022:1705] type 0 class 0x000600
[    0.315192] pci 0000:00:01.0: [1002:9644] type 0 class 0x000300
[    0.315201] pci 0000:00:01.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.315207] pci 0000:00:01.0: reg 14: [io  0xf000-0xf0ff]
[    0.315213] pci 0000:00:01.0: reg 18: [mem 0xfeb00000-0xfeb3ffff]
[    0.315246] pci 0000:00:01.0: supports D1 D2
[    0.315263] pci 0000:00:01.1: [1002:1714] type 0 class 0x000403
[    0.315271] pci 0000:00:01.1: reg 10: [mem 0xfeb44000-0xfeb47fff]
[    0.315312] pci 0000:00:01.1: supports D1 D2
[    0.315333] pci 0000:00:04.0: [1022:1709] type 1 class 0x000604
[    0.315375] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.315378] pci 0000:00:04.0: PME# disabled
[    0.315396] pci 0000:00:05.0: [1022:170a] type 1 class 0x000604
[    0.315436] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.315439] pci 0000:00:05.0: PME# disabled
[    0.315457] pci 0000:00:06.0: [1022:170b] type 1 class 0x000604
[    0.315498] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.315500] pci 0000:00:06.0: PME# disabled
[    0.315518] pci 0000:00:07.0: [1022:170c] type 1 class 0x000604
[    0.315559] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.315561] pci 0000:00:07.0: PME# disabled
[    0.315600] pci 0000:00:10.0: [1022:7812] type 0 class 0x000c03
[    0.315620] pci 0000:00:10.0: reg 10: [mem 0xfeb4a000-0xfeb4bfff 64bit]
[    0.315701] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
[    0.315705] pci 0000:00:10.0: PME# disabled
[    0.315740] pci 0000:00:10.1: [1022:7812] type 0 class 0x000c03
[    0.315760] pci 0000:00:10.1: reg 10: [mem 0xfeb48000-0xfeb49fff 64bit]
[    0.315841] pci 0000:00:10.1: PME# supported from D0 D3hot D3cold
[    0.315845] pci 0000:00:10.1: PME# disabled
[    0.315878] pci 0000:00:11.0: [1022:7800] type 0 class 0x000101
[    0.315894] pci 0000:00:11.0: reg 10: [io  0xf190-0xf197]
[    0.315903] pci 0000:00:11.0: reg 14: [io  0xf180-0xf183]
[    0.315912] pci 0000:00:11.0: reg 18: [io  0xf170-0xf177]
[    0.315921] pci 0000:00:11.0: reg 1c: [io  0xf160-0xf163]
[    0.315930] pci 0000:00:11.0: reg 20: [io  0xf150-0xf15f]
[    0.315939] pci 0000:00:11.0: reg 24: [mem 0xfeb51000-0xfeb517ff]
[    0.315959] pci 0000:00:11.0: set SATA to AHCI mode
[    0.315989] pci 0000:00:12.0: [1022:7807] type 0 class 0x000c03
[    0.316038] pci 0000:00:12.0: reg 10: [mem 0xfeb50000-0xfeb50fff]
[    0.316106] pci 0000:00:12.2: [1022:7808] type 0 class 0x000c03
[    0.316124] pci 0000:00:12.2: reg 10: [mem 0xfeb4f000-0xfeb4f0ff]
[    0.316191] pci 0000:00:12.2: supports D1 D2
[    0.316193] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.316196] pci 0000:00:12.2: PME# disabled
[    0.316216] pci 0000:00:13.0: [1022:7807] type 0 class 0x000c03
[    0.316229] pci 0000:00:13.0: reg 10: [mem 0xfeb4e000-0xfeb4efff]
[    0.316296] pci 0000:00:13.2: [1022:7808] type 0 class 0x000c03
[    0.316314] pci 0000:00:13.2: reg 10: [mem 0xfeb4d000-0xfeb4d0ff]
[    0.316381] pci 0000:00:13.2: supports D1 D2
[    0.316383] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.316386] pci 0000:00:13.2: PME# disabled
[    0.316406] pci 0000:00:14.0: [1022:780b] type 0 class 0x000c05
[    0.316474] pci 0000:00:14.1: [1022:780c] type 0 class 0x000101
[    0.316487] pci 0000:00:14.1: reg 10: [io  0xf140-0xf147]
[    0.316496] pci 0000:00:14.1: reg 14: [io  0xf130-0xf133]
[    0.316505] pci 0000:00:14.1: reg 18: [io  0xf120-0xf127]
[    0.316514] pci 0000:00:14.1: reg 1c: [io  0xf110-0xf113]
[    0.316523] pci 0000:00:14.1: reg 20: [io  0xf100-0xf10f]
[    0.316561] pci 0000:00:14.2: [1022:780d] type 0 class 0x000403
[    0.316581] pci 0000:00:14.2: reg 10: [mem 0xfeb40000-0xfeb43fff 64bit]
[    0.316637] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.316641] pci 0000:00:14.2: PME# disabled
[    0.316653] pci 0000:00:14.3: [1022:780e] type 0 class 0x000601
[    0.316726] pci 0000:00:14.4: [1022:780f] type 1 class 0x000604
[    0.316764] pci 0000:00:14.5: [1022:7809] type 0 class 0x000c03
[    0.316777] pci 0000:00:14.5: reg 10: [mem 0xfeb4c000-0xfeb4cfff]
[    0.316842] pci 0000:00:18.0: [1022:1700] type 0 class 0x000600
[    0.316872] pci 0000:00:18.1: [1022:1701] type 0 class 0x000600
[    0.316900] pci 0000:00:18.2: [1022:1702] type 0 class 0x000600
[    0.316929] pci 0000:00:18.3: [1022:1703] type 0 class 0x000600
[    0.316964] pci 0000:00:18.4: [1022:1704] type 0 class 0x000600
[    0.316992] pci 0000:00:18.5: [1022:1718] type 0 class 0x000600
[    0.317021] pci 0000:00:18.6: [1022:1716] type 0 class 0x000600
[    0.317048] pci 0000:00:18.7: [1022:1719] type 0 class 0x000600
[    0.317129] pci 0000:01:00.0: [168c:002b] type 0 class 0x000280
[    0.317148] pci 0000:01:00.0: reg 10: [mem 0xfea00000-0xfea0ffff 64bit]
[    0.317218] pci 0000:01:00.0: supports D1
[    0.317219] pci 0000:01:00.0: PME# supported from D0 D1 D3hot
[    0.317223] pci 0000:01:00.0: PME# disabled
[    0.324052] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.324063] pci 0000:00:04.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.324067] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.324072] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.324129] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.324145] pci 0000:02:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.324169] pci 0000:02:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.324184] pci 0000:02:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.324228] pci 0000:02:00.0: supports D1 D2
[    0.324230] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.324234] pci 0000:02:00.0: PME# disabled
[    0.332055] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.332066] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
[    0.332070] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.332075] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.332135] pci 0000:03:00.0: [1b21:1042] type 0 class 0x000c03
[    0.332158] pci 0000:03:00.0: reg 10: [mem 0xfe900000-0xfe907fff 64bit]
[    0.332247] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.332252] pci 0000:03:00.0: PME# disabled
[    0.340054] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.340065] pci 0000:00:06.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.340070] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.340074] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.340131] pci 0000:04:00.0: [1b21:0612] type 0 class 0x000106
[    0.340145] pci 0000:04:00.0: reg 10: [io  0xd050-0xd057]
[    0.340154] pci 0000:04:00.0: reg 14: [io  0xd040-0xd043]
[    0.340164] pci 0000:04:00.0: reg 18: [io  0xd030-0xd037]
[    0.340173] pci 0000:04:00.0: reg 1c: [io  0xd020-0xd023]
[    0.340182] pci 0000:04:00.0: reg 20: [io  0xd000-0xd01f]
[    0.340191] pci 0000:04:00.0: reg 24: [mem 0xfe800000-0xfe8001ff]
[    0.348057] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    0.348068] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
[    0.348072] pci 0000:00:07.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.348076] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.348141] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
[    0.348147] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.348151] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.348155] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.348157] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.348160] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.348161] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.348163] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.348165] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.348167] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.348169] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.348194] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.348388] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.348410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.348433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.348452] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.348471] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.348598]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.348744]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.352664] ACPI: PCI Interrupt Link [LN24] (IRQs *24)
[    0.352692] ACPI: PCI Interrupt Link [LN25] (IRQs *25)
[    0.352717] ACPI: PCI Interrupt Link [LN26] (IRQs *26)
[    0.352741] ACPI: PCI Interrupt Link [LN27] (IRQs *27)
[    0.352764] ACPI: PCI Interrupt Link [LN28] (IRQs *28)
[    0.352788] ACPI: PCI Interrupt Link [LN29] (IRQs *29)
[    0.352811] ACPI: PCI Interrupt Link [LN30] (IRQs *30)
[    0.352835] ACPI: PCI Interrupt Link [LN31] (IRQs *31)
[    0.352859] ACPI: PCI Interrupt Link [LN32] (IRQs *32)
[    0.352882] ACPI: PCI Interrupt Link [LN33] (IRQs *33)
[    0.352906] ACPI: PCI Interrupt Link [LN34] (IRQs *34)
[    0.352930] ACPI: PCI Interrupt Link [LN35] (IRQs *35)
[    0.352954] ACPI: PCI Interrupt Link [LN36] (IRQs *36)
[    0.352977] ACPI: PCI Interrupt Link [LN37] (IRQs *37)
[    0.353001] ACPI: PCI Interrupt Link [LN38] (IRQs *38)
[    0.353025] ACPI: PCI Interrupt Link [LN39] (IRQs *39)
[    0.353049] ACPI: PCI Interrupt Link [LN40] (IRQs *40)
[    0.353073] ACPI: PCI Interrupt Link [LN41] (IRQs *41)
[    0.353097] ACPI: PCI Interrupt Link [LN42] (IRQs *42)
[    0.353121] ACPI: PCI Interrupt Link [LN43] (IRQs *43)
[    0.353145] ACPI: PCI Interrupt Link [LN44] (IRQs *44)
[    0.353169] ACPI: PCI Interrupt Link [LN45] (IRQs *45)
[    0.353193] ACPI: PCI Interrupt Link [LN46] (IRQs *46)
[    0.353217] ACPI: PCI Interrupt Link [LN47] (IRQs *47)
[    0.353241] ACPI: PCI Interrupt Link [LN48] (IRQs *48)
[    0.353266] ACPI: PCI Interrupt Link [LN49] (IRQs *49)
[    0.353292] ACPI: PCI Interrupt Link [LN50] (IRQs *50)
[    0.353317] ACPI: PCI Interrupt Link [LN51] (IRQs *51)
[    0.353341] ACPI: PCI Interrupt Link [LN52] (IRQs *52)
[    0.353365] ACPI: PCI Interrupt Link [LN53] (IRQs *53)
[    0.353392] ACPI: PCI Interrupt Link [LN54] (IRQs *54)
[    0.353416] ACPI: PCI Interrupt Link [LN55] (IRQs *55)
[    0.353444] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 7 10 11 14 15) *0
[    0.353494] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 5 7 10 11 14 15) *0
[    0.353544] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 10 11 14 15) *0
[    0.353593] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 5 7 10 11 14 15) *0
[    0.353632] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 10 11 14 15) *0
[    0.353663] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 10 11 14 15) *0
[    0.353693] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 5 7 10 11 14 15) *0
[    0.353724] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 7 10 11 14 15) *0
[    0.353813] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.353827] vgaarb: loaded
[    0.353830] vgaarb: bridge control possible 0000:00:01.0
[    0.353967] SCSI subsystem initialized
[    0.354029] libata version 3.00 loaded.
[    0.354063] usbcore: registered new interface driver usbfs
[    0.354074] usbcore: registered new interface driver hub
[    0.354094] usbcore: registered new device driver usb
[    0.354158] PCI: Using ACPI for IRQ routing
[    0.362430] PCI: pci_cache_line_size set to 64 bytes
[    0.362527] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.362529] reserve RAM buffer: 00000000bf6d1000 - 00000000bfffffff 
[    0.362532] reserve RAM buffer: 00000000bfd1a000 - 00000000bfffffff 
[    0.362535] reserve RAM buffer: 00000000bfd74000 - 00000000bfffffff 
[    0.362538] reserve RAM buffer: 00000000bff00000 - 00000000bfffffff 
[    0.362539] reserve RAM buffer: 000000021f000000 - 000000021fffffff 
[    0.362614] NetLabel: Initializing
[    0.362617] NetLabel:  domain hash size = 128
[    0.362619] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.362629] NetLabel:  unlabeled traffic allowed by default
[    0.362667] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.362672] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.364038] Switching to clocksource hpet
[    0.367092] Freeing initrd memory: 13440k freed
[    0.367092] Switched to NOHz mode on CPU #0
[    0.367171] Switched to NOHz mode on CPU #1
[    0.368913] AppArmor: AppArmor Filesystem Enabled
[    0.368949] pnp: PnP ACPI init
[    0.368965] ACPI: bus type pnp registered
[    0.369120] pnp 00:00: [bus 00-ff]
[    0.369123] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.369125] pnp 00:00: [io  0x0000-0x03af window]
[    0.369127] pnp 00:00: [io  0x03e0-0x0cf7 window]
[    0.369129] pnp 00:00: [io  0x03b0-0x03df window]
[    0.369130] pnp 00:00: [io  0x0d00-0xffff window]
[    0.369132] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.369134] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.369136] pnp 00:00: [mem 0xc0000000-0xffffffff window]
[    0.369138] pnp 00:00: [mem 0x00000000 window]
[    0.369205] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.369233] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.369287] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.369291] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.369464] pnp 00:02: [io  0x0010-0x001f]
[    0.369466] pnp 00:02: [io  0x0022-0x003f]
[    0.369467] pnp 00:02: [io  0x0063]
[    0.369468] pnp 00:02: [io  0x0065]
[    0.369470] pnp 00:02: [io  0x0067-0x006f]
[    0.369471] pnp 00:02: [io  0x0072-0x007f]
[    0.369473] pnp 00:02: [io  0x0080]
[    0.369474] pnp 00:02: [io  0x0084-0x0086]
[    0.369476] pnp 00:02: [io  0x0088]
[    0.369477] pnp 00:02: [io  0x008c-0x008e]
[    0.369478] pnp 00:02: [io  0x0090-0x009f]
[    0.369480] pnp 00:02: [io  0x00a2-0x00bf]
[    0.369481] pnp 00:02: [io  0x00b1]
[    0.369483] pnp 00:02: [io  0x00e0-0x00ef]
[    0.369484] pnp 00:02: [io  0x04d0-0x04d1]
[    0.369486] pnp 00:02: [io  0x040b]
[    0.369490] pnp 00:02: [io  0x04d6]
[    0.369491] pnp 00:02: [io  0x0c00-0x0c01]
[    0.369493] pnp 00:02: [io  0x0c14]
[    0.369494] pnp 00:02: [io  0x0c50-0x0c51]
[    0.369495] pnp 00:02: [io  0x0c52]
[    0.369497] pnp 00:02: [io  0x0c6c]
[    0.369498] pnp 00:02: [io  0x0c6f]
[    0.369499] pnp 00:02: [io  0x0cd0-0x0cd1]
[    0.369501] pnp 00:02: [io  0x0cd2-0x0cd3]
[    0.369502] pnp 00:02: [io  0x0cd4-0x0cd5]
[    0.369504] pnp 00:02: [io  0x0cd6-0x0cd7]
[    0.369505] pnp 00:02: [io  0x0cd8-0x0cdf]
[    0.369507] pnp 00:02: [io  0x0800-0x089f]
[    0.369508] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.369510] pnp 00:02: [io  0x0000-0x000f]
[    0.369512] pnp 00:02: [io  0x0b20-0x0b3f]
[    0.369513] pnp 00:02: [io  0x0900-0x090f]
[    0.369514] pnp 00:02: [io  0x0910-0x091f]
[    0.369516] pnp 00:02: [io  0xfe00-0xfefe]
[    0.369517] pnp 00:02: [io  0x0060-0x005f disabled]
[    0.369519] pnp 00:02: [io  0x0064-0x0063 disabled]
[    0.369521] pnp 00:02: [mem 0xfec00000-0xfec00fff]
[    0.369522] pnp 00:02: [mem 0xfee00000-0xfee00fff]
[    0.369524] pnp 00:02: [mem 0xfed80000-0xfed8ffff]
[    0.369526] pnp 00:02: [mem 0xfed61000-0xfed70fff]
[    0.369527] pnp 00:02: [mem 0xfec10000-0xfec10fff]
[    0.369529] pnp 00:02: [mem 0xfed00000-0xfed00fff]
[    0.369530] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.369608] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.369612] system 00:02: [io  0x040b] has been reserved
[    0.369615] system 00:02: [io  0x04d6] has been reserved
[    0.369618] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.369621] system 00:02: [io  0x0c14] has been reserved
[    0.369624] system 00:02: [io  0x0c50-0x0c51] has been reserved
[    0.369628] system 00:02: [io  0x0c52] has been reserved
[    0.369631] system 00:02: [io  0x0c6c] has been reserved
[    0.369634] system 00:02: [io  0x0c6f] has been reserved
[    0.369637] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.369640] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.369643] system 00:02: [io  0x0cd4-0x0cd5] has been reserved
[    0.369647] system 00:02: [io  0x0cd6-0x0cd7] has been reserved
[    0.369650] system 00:02: [io  0x0cd8-0x0cdf] has been reserved
[    0.369656] system 00:02: [io  0x0800-0x089f] has been reserved
[    0.369659] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    0.369663] system 00:02: [io  0x0900-0x090f] has been reserved
[    0.369666] system 00:02: [io  0x0910-0x091f] has been reserved
[    0.369670] system 00:02: [io  0xfe00-0xfefe] has been reserved
[    0.369674] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.369678] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.369682] system 00:02: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.369685] system 00:02: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.369689] system 00:02: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.369693] system 00:02: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.369697] system 00:02: [mem 0xff000000-0xffffffff] has been reserved
[    0.369700] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.369791] pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
[    0.369793] pnp 00:03: [io  0x0300-0x031f]
[    0.369794] pnp 00:03: [io  0x0290-0x029f]
[    0.369796] pnp 00:03: [io  0x0230-0x023f]
[    0.369826] system 00:03: [io  0x0300-0x031f] has been reserved
[    0.369830] system 00:03: [io  0x0290-0x029f] has been reserved
[    0.369834] system 00:03: [io  0x0230-0x023f] has been reserved
[    0.369837] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.369848] pnp 00:04: [dma 4]
[    0.369849] pnp 00:04: [io  0x0000-0x000f]
[    0.369850] pnp 00:04: [io  0x0081-0x0083]
[    0.369852] pnp 00:04: [io  0x0087]
[    0.369853] pnp 00:04: [io  0x0089-0x008b]
[    0.369855] pnp 00:04: [io  0x008f]
[    0.369856] pnp 00:04: [io  0x00c0-0x00df]
[    0.369873] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.369880] pnp 00:05: [io  0x0070-0x0071]
[    0.369893] pnp 00:05: [irq 8]
[    0.369908] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.369914] pnp 00:06: [io  0x0061]
[    0.369931] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.369950] pnp 00:07: [io  0x0010-0x001f]
[    0.369953] pnp 00:07: [io  0x0022-0x003f]
[    0.369954] pnp 00:07: [io  0x0044-0x005f]
[    0.369955] pnp 00:07: [io  0x0072-0x007f]
[    0.369957] pnp 00:07: [io  0x0080]
[    0.369958] pnp 00:07: [io  0x0084-0x0086]
[    0.369960] pnp 00:07: [io  0x0088]
[    0.369961] pnp 00:07: [io  0x008c-0x008e]
[    0.369963] pnp 00:07: [io  0x0090-0x009f]
[    0.369964] pnp 00:07: [io  0x00a2-0x00bf]
[    0.369965] pnp 00:07: [io  0x00e0-0x00ef]
[    0.369967] pnp 00:07: [io  0x04d0-0x04d1]
[    0.370001] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.370005] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.370011] pnp 00:08: [io  0x00f0-0x00ff]
[    0.370015] pnp 00:08: [irq 13]
[    0.370031] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.370067] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.370206] pnp 00:0a: [io  0x03f8-0x03ff]
[    0.370209] pnp 00:0a: [irq 4]
[    0.370211] pnp 00:0a: [dma 0 disabled]
[    0.370252] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.370531] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.370571] pnp 00:0b: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.370576] pnp: PnP ACPI: found 12 devices
[    0.370579] ACPI: ACPI bus type pnp unregistered
[    0.376107] PCI: max bus depth: 1 pci_try_num: 2
[    0.376141] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.376146] pci 0000:00:04.0:   bridge window [io  disabled]
[    0.376152] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.376156] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    0.376162] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.376165] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
[    0.376170] pci 0000:00:05.0:   bridge window [mem disabled]
[    0.376174] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.376181] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.376183] pci 0000:00:06.0:   bridge window [io  disabled]
[    0.376188] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.376192] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.376198] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    0.376201] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
[    0.376206] pci 0000:00:07.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.376210] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    0.376216] pci 0000:00:14.4: PCI bridge to [bus 05-05]
[    0.376219] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.376225] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.376229] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.376252] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.376258] pci 0000:00:04.0: setting latency timer to 64
[    0.376266] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.376271] pci 0000:00:05.0: setting latency timer to 64
[    0.376278] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.376283] pci 0000:00:06.0: setting latency timer to 64
[    0.376290] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.376294] pci 0000:00:07.0: setting latency timer to 64
[    0.376302] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.376304] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.376305] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.376307] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.376309] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.376311] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.376313] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
[    0.376315] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.376317] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.376319] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.376321] pci_bus 0000:03: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.376323] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.376325] pci_bus 0000:04: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.376327] pci_bus 0000:05: resource 4 [io  0x0000-0x03af]
[    0.376329] pci_bus 0000:05: resource 5 [io  0x03e0-0x0cf7]
[    0.376330] pci_bus 0000:05: resource 6 [io  0x03b0-0x03df]
[    0.376332] pci_bus 0000:05: resource 7 [io  0x0d00-0xffff]
[    0.376334] pci_bus 0000:05: resource 8 [mem 0x000a0000-0x000bffff]
[    0.376336] pci_bus 0000:05: resource 9 [mem 0x000c0000-0x000dffff]
[    0.376338] pci_bus 0000:05: resource 10 [mem 0xc0000000-0xffffffff]
[    0.376369] NET: Registered protocol family 2
[    0.376560] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.377708] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.380029] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.380327] TCP: Hash tables configured (established 524288 bind 65536)
[    0.380332] TCP reno registered
[    0.380349] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.380409] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.380532] NET: Registered protocol family 1
[    0.380547] pci 0000:00:01.0: Boot video device
[    0.972150] PCI: CLS 64 bytes, default 64
[    0.972159] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.972175] Placing 64MB software IO TLB between ffff8800bb6d1000 - ffff8800bf6d1000
[    0.972188] software IO TLB at phys 0xbb6d1000 - 0xbf6d1000
[    0.972524] audit: initializing netlink socket (disabled)
[    0.972535] type=2000 audit(1325112295.968:1): initialized
[    1.004355] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.036239] VFS: Disk quotas dquot_6.5.2
[    1.036291] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.036826] fuse init (API version 7.16)
[    1.036920] msgmni has been set to 14944
[    1.037473] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.037530] io scheduler noop registered
[    1.037537] io scheduler deadline registered
[    1.037601] io scheduler cfq registered (default)
[    1.037707] pcieport 0000:00:04.0: setting latency timer to 64
[    1.037750] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    1.037803] pcieport 0000:00:05.0: setting latency timer to 64
[    1.037836] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    1.037882] pcieport 0000:00:06.0: setting latency timer to 64
[    1.037915] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    1.037962] pcieport 0000:00:07.0: setting latency timer to 64
[    1.037995] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
[    1.038059] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    1.038063] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.038068] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    1.038083] pcieport 0000:00:05.0: Signaling PME through PCIe PME interrupt
[    1.038086] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.038091] pcie_pme 0000:00:05.0:pcie01: service driver pcie_pme loaded
[    1.038103] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
[    1.038106] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.038111] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
[    1.038123] pcieport 0000:00:07.0: Signaling PME through PCIe PME interrupt
[    1.038127] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    1.038131] pcie_pme 0000:00:07.0:pcie01: service driver pcie_pme loaded
[    1.038144] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.038163] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.038264] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.038271] ACPI: Power Button [PWRB]
[    1.038302] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.038306] ACPI: Power Button [PWRF]
[    1.038330] ACPI: acpi_idle registered with cpuidle
[    1.073188] ERST: Table is not found!
[    1.073261] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.093639] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.168688] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.169085] Linux agpgart interface v0.103
[    1.169863] brd: module loaded
[    1.170189] loop: module loaded
[    1.170333] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.170369] pata_acpi 0000:00:14.1: PCI INT B disabled
[    1.170572] Fixed MDIO Bus: probed
[    1.170590] PPP generic driver version 2.4.2
[    1.170629] tun: Universal TUN/TAP device driver, 1.6
[    1.170632] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.170695] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.170708] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.170737] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.170769] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.170779] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.170805] QUIRK: Enable AMD PLL fix
[    1.170814] ehci_hcd 0000:00:12.2: debug port 1
[    1.170838] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfeb4f000
[    1.180106] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.180335] hub 1-0:1.0: USB hub found
[    1.180341] hub 1-0:1.0: 5 ports detected
[    1.180407] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.180431] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.180465] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.180474] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.180495] ehci_hcd 0000:00:13.2: debug port 1
[    1.180510] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfeb4d000
[    1.192106] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.192335] hub 2-0:1.0: USB hub found
[    1.192341] hub 2-0:1.0: 5 ports detected
[    1.192407] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.192425] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.192450] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.192479] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.192506] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfeb50000
[    1.252236] hub 3-0:1.0: USB hub found
[    1.252247] hub 3-0:1.0: 5 ports detected
[    1.252315] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.252341] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.252372] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.252390] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfeb4e000
[    1.312235] hub 4-0:1.0: USB hub found
[    1.312246] hub 4-0:1.0: 5 ports detected
[    1.312317] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.312342] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.312372] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
[    1.312390] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfeb4c000
[    1.372461] hub 5-0:1.0: USB hub found
[    1.372472] hub 5-0:1.0: 2 ports detected
[    1.372533] uhci_hcd: USB Universal Host Controller Interface driver
[    1.372592] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.372955] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.372965] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.373062] mousedev: PS/2 mouse device common for all mice
[    1.373147] rtc_cmos 00:05: RTC can wake from S4
[    1.373216] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.373236] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.373320] device-mapper: uevent: version 1.0.3
[    1.373379] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.373414] cpuidle: using governor ladder
[    1.373497] cpuidle: using governor menu
[    1.373499] EFI Variables Facility v0.08 2004-May-17
[    1.373670] TCP cubic registered
[    1.373760] NET: Registered protocol family 10
[    1.374127] NET: Registered protocol family 17
[    1.374143] Registering the dns_resolver key type
[    1.374227] PM: Hibernation image not present or could not be loaded.
[    1.374236] registered taskstats version 1
[    1.395752]   Magic number: 7:162:756
[    1.395773] tty ttyS7: hash matches
[    1.395832] rtc_cmos 00:05: setting system clock to 2011-12-28 22:44:56 UTC (1325112296)
[    1.395843] powernow-k8: Found 1 AMD A4-3400 APU with Radeon(tm) HD Graphics (2 cpu cores) (version 2.20.00)
[    1.395899] powernow-k8:    0 : pstate 0 (2700 MHz)
[    1.395902] powernow-k8:    1 : pstate 1 (2400 MHz)
[    1.395904] powernow-k8:    2 : pstate 2 (2200 MHz)
[    1.395907] powernow-k8:    3 : pstate 3 (2000 MHz)
[    1.395909] powernow-k8:    4 : pstate 4 (1800 MHz)
[    1.395911] powernow-k8:    5 : pstate 5 (1400 MHz)
[    1.395914] powernow-k8:    6 : pstate 6 (1100 MHz)
[    1.395916] powernow-k8:    7 : pstate 7 (800 MHz)
[    1.396112] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.396116] EDD information not available.
[    1.397504] Freeing unused kernel memory: 984k freed
[    1.397733] Write protecting the kernel read-only data: 10240k
[    1.397901] Freeing unused kernel memory: 16k freed
[    1.401669] Freeing unused kernel memory: 1396k freed
[    1.420314] udevd[80]: starting version 173
[    1.459457] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.459484] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.459526] r8169 0000:02:00.0: setting latency timer to 64
[    1.459533] r8169 0000:02:00.0: (unregistered net_device): unknown MAC, using family default
[    1.459596] r8169 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.459948] r8169 0000:02:00.0: eth0: RTL8168b/8111b at 0xffffc90000c78000, 14:da:e9:1d:5c:ca, XID 0c900800 IRQ 44
[    1.465306] xhci_hcd 0000:00:10.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.465333] xhci_hcd 0000:00:10.0: setting latency timer to 64
[    1.465336] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.465401] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    1.465592] xhci_hcd 0000:00:10.0: irq 18, io mem 0xfeb4a000
[    1.465647] xhci_hcd 0000:00:10.0: irq 45 for MSI/MSI-X
[    1.465651] xhci_hcd 0000:00:10.0: irq 46 for MSI/MSI-X
[    1.465654] xhci_hcd 0000:00:10.0: irq 47 for MSI/MSI-X
[    1.465774] xHCI xhci_add_endpoint called for root hub
[    1.465776] xHCI xhci_check_bandwidth called for root hub
[    1.465796] hub 6-0:1.0: USB hub found
[    1.465803] hub 6-0:1.0: 2 ports detected
[    1.465854] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.465879] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
[    1.490614] xHCI xhci_add_endpoint called for root hub
[    1.490617] xHCI xhci_check_bandwidth called for root hub
[    1.490642] hub 7-0:1.0: USB hub found
[    1.490656] hub 7-0:1.0: 2 ports detected
[    1.490721] ahci 0000:00:11.0: version 3.0
[    1.490733] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.490846] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.490851] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.493155] scsi0 : ahci
[    1.493678] scsi1 : ahci
[    1.494664] scsi2 : ahci
[    1.495789] scsi3 : ahci
[    1.496041] ata1: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51100 irq 19
[    1.496047] ata2: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51180 irq 19
[    1.496051] ata3: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51200 irq 19
[    1.496056] ata4: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51280 irq 19
[    1.496132] pata_atiixp 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.496355] ahci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.496413] ahci 0000:04:00.0: irq 48 for MSI/MSI-X
[    1.496436] ahci: SSS flag set, parallel bus scan disabled
[    1.496460] ahci 0000:04:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.496466] ahci 0000:04:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    1.496472] ahci 0000:04:00.0: setting latency timer to 64
[    1.497882] scsi4 : pata_atiixp
[    1.497947] scsi5 : ahci
[    1.498093] scsi6 : pata_atiixp
[    1.498194] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf100 irq 14
[    1.498198] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf108 irq 15
[    1.498233] scsi7 : ahci
[    1.498248] xhci_hcd 0000:00:10.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.498270] ata7: SATA max UDMA/133 abar m512@0xfe800000 port 0xfe800100 irq 48
[    1.498276] ata8: SATA max UDMA/133 abar m512@0xfe800000 port 0xfe800180 irq 48
[    1.498280] xhci_hcd 0000:00:10.1: setting latency timer to 64
[    1.498284] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.498357] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
[    1.498597] xhci_hcd 0000:00:10.1: irq 17, io mem 0xfeb48000
[    1.498659] xhci_hcd 0000:00:10.1: irq 49 for MSI/MSI-X
[    1.498663] xhci_hcd 0000:00:10.1: irq 50 for MSI/MSI-X
[    1.498666] xhci_hcd 0000:00:10.1: irq 51 for MSI/MSI-X
[    1.498791] xHCI xhci_add_endpoint called for root hub
[    1.498792] xHCI xhci_check_bandwidth called for root hub
[    1.498814] hub 8-0:1.0: USB hub found
[    1.498822] hub 8-0:1.0: 2 ports detected
[    1.499226] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.499293] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
[    1.502831] xHCI xhci_add_endpoint called for root hub
[    1.502834] xHCI xhci_check_bandwidth called for root hub
[    1.502859] hub 9-0:1.0: USB hub found
[    1.502873] hub 9-0:1.0: 2 ports detected
[    1.502941] xhci_hcd 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.502975] xhci_hcd 0000:03:00.0: setting latency timer to 64
[    1.502979] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.503014] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 10
[    1.512667] xhci_hcd 0000:03:00.0: irq 18, io mem 0xfe900000
[    1.512716] xhci_hcd 0000:03:00.0: irq 52 for MSI/MSI-X
[    1.512720] xhci_hcd 0000:03:00.0: irq 53 for MSI/MSI-X
[    1.512724] xhci_hcd 0000:03:00.0: irq 54 for MSI/MSI-X
[    1.512834] xHCI xhci_add_endpoint called for root hub
[    1.512836] xHCI xhci_check_bandwidth called for root hub
[    1.512860] hub 10-0:1.0: USB hub found
[    1.512867] hub 10-0:1.0: 2 ports detected
[    1.512922] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.512949] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 11
[    1.513010] xHCI xhci_add_endpoint called for root hub
[    1.513011] xHCI xhci_check_bandwidth called for root hub
[    1.513028] hub 11-0:1.0: USB hub found
[    1.513034] hub 11-0:1.0: 2 ports detected
[    1.668403] ata6.00: ATAPI: HL-DT-ST DVDRAM GH22LS50, TL03, max UDMA/100
[    1.668426] ata6.00: limited to UDMA/33 due to 40-wire cable
[    1.684692] ata6.00: configured for UDMA/33
[    1.716378] usb 3-1: new low speed USB device number 2 using ohci_hcd
[    1.816355] ata3: SATA link down (SStatus 0 SControl 300)
[    1.824367] ata4: SATA link down (SStatus 0 SControl 300)
[    1.824430] ata1: SATA link down (SStatus 0 SControl 300)
[    1.824491] ata7: SATA link down (SStatus 0 SControl 300)
[    1.901487] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input2
[    1.901566] generic-usb 0003:046D:C31D.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:12.0-1/input0
[    1.912349] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input3
[    1.912452] generic-usb 0003:046D:C31D.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:12.0-1/input1
[    1.912470] usbcore: registered new interface driver usbhid
[    1.912472] usbhid: USB HID core driver
[    1.972346] Refined TSC clocksource calibration: 2700.201 MHz.
[    1.972368] Switching to clocksource tsc
[    1.996341] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.996668] ata2.00: ATA-8: CRUCIAL_CT64M225, 2030, max UDMA/133
[    1.996676] ata2.00: 125045424 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.998752] ata2.00: configured for UDMA/133
[    1.999039] scsi 1:0:0:0: Direct-Access     ATA      CRUCIAL_CT64M225 2030 PQ: 0 ANSI: 5
[    1.999177] sd 1:0:0:0: [sda] 125045424 512-byte logical blocks: (64.0 GB/59.6 GiB)
[    1.999206] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.999227] sd 1:0:0:0: [sda] Write Protect is off
[    1.999233] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.999247] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.001446]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7
[    2.001801] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.002760] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22LS50  TL03 PQ: 0 ANSI: 5
[    2.013447] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.013468] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.013689] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    2.013756] sr 6:0:0:0: Attached scsi generic sg1 type 5
[    2.212341] usb 4-2: new low speed USB device number 2 using ohci_hcd
[    2.332350] ata8: SATA link down (SStatus 0 SControl 300)
[    2.388508] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb4/4-2/4-2:1.0/input/input4
[    2.388607] generic-usb 0003:046D:C03E.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-2/input0
[    2.409368] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.589134] init: ureadahead main process (312) terminated with status 5
[    2.716908] udevd[352]: starting version 173
[    2.748353] Adding 1635324k swap on /dev/sda4.  Priority:-1 extents:1 across:1635324k SS
[    2.793587] lp: driver loaded but no devices found
[    2.867825] [drm] Initialized drm 1.1.0 20060810
[    2.875214] cfg80211: Calling CRDA to update world regulatory domain
[    2.902295] [drm] radeon defaulting to kernel modesetting.
[    2.902299] [drm] radeon kernel modesetting enabled.
[    2.902348] radeon 0000:00:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.902352] radeon 0000:00:01.0: setting latency timer to 64
[    2.903137] [drm] initializing kernel modesetting (SUMO2 0x1002:0x9644 0x1043:0x84C8).
[    2.903201] [drm] register mmio base: 0xFEB00000
[    2.903202] [drm] register mmio size: 262144
[    2.903304] ATOM BIOS: General
[    2.903329] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    2.903331] radeon 0000:00:01.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[    2.906870] wmi: Mapper loaded
[    2.908816] [drm] Detected VRAM RAM=512M, BAR=256M
[    2.908820] [drm] RAM width 32bits DDR
[    2.911948] [TTM] Zone  kernel: Available graphics memory: 3826876 kiB.
[    2.911952] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    2.911954] [TTM] Initializing pool allocator.
[    2.911977] [drm] radeon: 512M of VRAM memory ready
[    2.911979] [drm] radeon: 512M of GTT memory ready.
[    2.911993] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.911994] [drm] Driver supports precise vblank timestamp query.
[    2.912049] radeon 0000:00:01.0: irq 55 for MSI/MSI-X
[    2.912057] radeon 0000:00:01.0: radeon: using MSI.
[    2.912148] [drm] radeon: irq initialized.
[    2.912153] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.913544] ip_tables: (C) 2000-2006 Netfilter Core Team
[    2.913828] [drm] Loading SUMO2 Microcode
[    2.918049] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.918059] ath9k 0000:01:00.0: setting latency timer to 64
[    2.966631] ath: EEPROM regdomain: 0x809c
[    2.966633] ath: EEPROM indicates we should expect a country code
[    2.966634] ath: doing EEPROM country->regdmn map search
[    2.966636] ath: country maps to regdmn code: 0x52
[    2.966637] ath: Country alpha2 being used: CN
[    2.966639] ath: Regpair used: 0x52
[    2.966641] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    2.966643] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966645] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    2.966647] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966649] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    2.966651] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966652] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    2.966655] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966656] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    2.966658] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966660] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    2.966662] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966664] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    2.966666] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966667] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    2.966669] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966671] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    2.966673] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966675] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    2.966677] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966678] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    2.966680] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    2.966682] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    2.966683] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    2.966685] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    2.968122] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    2.968125] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968127] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    2.968129] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968130] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    2.968132] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968134] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    2.968136] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968138] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    2.968140] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968141] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    2.968143] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968145] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    2.968147] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968148] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    2.968150] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968152] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    2.968154] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968156] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    2.968158] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968159] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    2.968161] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968163] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    2.968165] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968167] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    2.968169] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[    2.968170] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    2.968172] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[    3.046994] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    3.058943] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    3.068509] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    3.069009] cfg80211: Pending regulatory request, waiting for it to be processed...
[    3.069066] Registered led device: ath9k-phy0
[    3.069070] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90011820000, irq=16
[    3.083861] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    3.107959] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.123910] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    3.148408] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    3.358715] init: failsafe main process (772) killed by TERM signal
[    3.447160] asus_wmi: ASUS WMI generic driver loaded
[    3.449752] asus_wmi: Initialization: 0x0
[    3.449772] asus_wmi: BIOS WMI version: 0.9
[    3.449805] asus_wmi: SFUN value: 0x0
[    3.453422] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input5
[    3.514505] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.514509] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514511] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.514514] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514515] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.514517] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514523] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.514525] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514526] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.514528] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514530] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.514532] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514533] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.514535] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514537] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.514539] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514540] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.514542] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514544] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.514546] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514547] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.514549] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514551] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.514553] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514554] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    3.514556] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514558] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    3.514560] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[    3.514563] cfg80211: World regulatory domain updated:
[    3.514564] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    3.514567] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.514568] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.514570] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.514572] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.514574] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.515718] cfg80211: Calling CRDA for country: CN
[    3.526144] radeon 0000:00:01.0: WB enabled
[    3.542615] [drm] ring test succeeded in 1 usecs
[    3.542748] [drm] radeon: ib pool ready.
[    3.542843] [drm] ib test succeeded in 0 usecs
[    3.542849] failed to evaluate ATIF got AE_BAD_PARAMETER
[    3.543016] Radeon i2c bit bus 0x90: Test OK
[    3.543076] Radeon i2c bit bus 0x91: bus seems to be busy
[    3.553241] [drm:radeon_i2c_create] *ERROR* Failed to register bit i2c 0x91
[    3.553269] Radeon i2c bit bus 0x92: bus seems to be busy
[    3.554759] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.554763] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554765] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.554767] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554769] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.554771] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554773] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.554774] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554776] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.554778] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554780] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.554782] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554783] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.554785] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554787] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.554789] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554790] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.554792] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554794] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.554796] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554797] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.554799] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554801] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.554803] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554804] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    3.554806] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.554808] cfg80211: Disabling freq 2484 MHz
[    3.554811] cfg80211: Regulatory domain changed to country: CN
[    3.554812] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    3.554814] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    3.554816] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[    3.564022] [drm:radeon_i2c_create] *ERROR* Failed to register bit i2c 0x92
[    3.564070] Radeon i2c bit bus 0x93: SDA stuck low!
[    3.564109] [drm:radeon_i2c_create] *ERROR* Failed to register bit i2c 0x93
[    3.564144] Radeon i2c bit bus 0x94: SDA stuck low!
[    3.564183] [drm:radeon_i2c_create] *ERROR* Failed to register bit i2c 0x94
[    3.564217] Radeon i2c bit bus 0x95: SDA stuck low!
[    3.564256] [drm:radeon_i2c_create] *ERROR* Failed to register bit i2c 0x95
[    3.564267] Radeon i2c bit bus 0x96: bus seems to be busy
[    3.578007] [drm:radeon_i2c_create] *ERROR* Failed to register bit i2c 0x96
[    3.578026] Radeon i2c bit bus 0x97: bus seems to be busy
[    3.589869] [drm:radeon_i2c_create] *ERROR* Failed to register bit i2c 0x97
[    3.591282] [drm:radeon_add_atom_connector] *ERROR* DP: Failed to assign ddc bus! Check dmesg for i2c errors.
[    3.595223] [drm:radeon_dp_i2c_aux_ch] *ERROR* aux i2c too many retries, giving up
[    3.595361] [drm:radeon_dp_i2c_aux_ch] *ERROR* aux i2c too many retries, giving up
[    3.595857] [drm:radeon_add_atom_connector] *ERROR* DP: Failed to assign ddc bus! Check dmesg for i2c errors.
[    3.596017] [drm] Radeon Display Connectors
[    3.596018] [drm] Connector 0:
[    3.596020] [drm]   VGA
[    3.596021] [drm]   HPD2
[    3.596022] [drm]   DDC: no ddc bus - possible BIOS bug - please report to xorg-driver-ati@lists.x.org
[    3.596023] [drm]   Encoders:
[    3.596025] [drm]     CRT1: INTERNAL_UNIPHY2
[    3.596026] [drm]     CRT1: NUTMEG
[    3.596027] [drm] Connector 1:
[    3.596028] [drm]   HDMI-A
[    3.596029] [drm]   HPD1
[    3.596030] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    3.596032] [drm]   Encoders:
[    3.596033] [drm]     DFP1: INTERNAL_UNIPHY2
[    3.596034] [drm] Connector 2:
[    3.596035] [drm]   DisplayPort
[    3.596036] [drm]   HPD3
[    3.596037] [drm]   Encoders:
[    3.596038] [drm]     DFP2: INTERNAL_UNIPHY
[    3.623541] [drm] Radeon display connector HDMI-A-1: No monitor connected or invalid EDID
[    3.628722] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.641485] [drm] Internal thermal controller without fan control
[    3.642030] [drm] radeon: power management initialized
[    3.656891] r8169 0000:02:00.0: eth0: link down
[    3.657715] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.684310] No connectors reported connected with modes
[    3.684315] [drm] Cannot find any crtc or sizes - going 1024x768
[    3.685788] [drm] fb mappable at 0xC0141000
[    3.685790] [drm] vram apper at 0xC0000000
[    3.685791] [drm] size 3145728
[    3.685792] [drm] fb depth is 24
[    3.685793] [drm]    pitch is 4096
[    3.685876] fbcon: radeondrmfb (fb0) is primary device
[    3.685946] Console: switching to colour frame buffer device 128x48
[    3.688181] fb0: radeondrmfb frame buffer device
[    3.688183] drm: registered panic notifier
[    3.688190] [drm] Initialized radeon 2.10.0 20080528 for 0000:00:01.0 on minor 0
[    3.688489] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    3.688617] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.688681] HDA Intel 0000:00:01.1: irq 56 for MSI/MSI-X
[    3.688704] HDA Intel 0000:00:01.1: setting latency timer to 64
[    3.709554] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[    3.709660] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input6
[    3.709825] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.759211] hda_codec: ALC892: BIOS auto-probing.
[    3.767696] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
[    3.928582] ppdev: user-space parallel port driver

```
Output from lspci:
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
    Subsystem: ASUSTeK Computer Inc. Device 84c8
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9644 (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 84c8
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel modules: radeon

00:01.1 Audio device: ATI Technologies Inc Device 1714
    Subsystem: ASUSTeK Computer Inc. Device 84c8
    Flags: bus master, fast devsel, latency 0, IRQ 55
    Memory at feb44000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: fea00000-feafffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fe900000-fe9fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe800000-fe8fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:10.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at feb4a000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [50] Power Management version 3
    Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [a0] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] #18
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

00:10.1 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at feb48000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [50] Power Management version 3
    Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [a0] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [IDE mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at f190 [size=8]
    I/O ports at f180 [size=4]
    I/O ports at f170 [size=8]
    I/O ports at f160 [size=4]
    I/O ports at f150 [size=16]
    Memory at feb51000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [70] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb50000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb4f000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb4d000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f100 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 841b
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=64

00:14.5 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84c7
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
    Flags: fast devsel

01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Atheros Communications Inc. Device 30a1
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fea00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
    Capabilities: [170] Power Budgeting <?>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards
    Flags: bus master, fast devsel, latency 0, IRQ 47
    I/O ports at e000 [size=256]
    Memory at d0004000 (64-bit, prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 USB Controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8488
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fe900000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [68] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

04:00.0 SATA controller: ASMedia Technology Inc. Device 0612 (rev 01) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 84b7
    Flags: bus master, fast devsel, latency 0, IRQ 51
    I/O ports at d050 [size=8]
    I/O ports at d040 [size=4]
    I/O ports at d030 [size=8]
    I/O ports at d020 [size=4]
    I/O ports at d000 [size=32]
    Memory at fe800000 (32-bit, non-prefetchable) [size=512]
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: ahci
    Kernel modules: ahci

```

Any suggestions would be extremely welcome!

---

### Post by cfr42 on 2011-12-28
In my case, the latest version of AMD's proprietary driver works around this issue (sort of). The quality isn't great - I'm seeing lots of corruption when redrawing the screen but it is better than having to disable KMS all the time.

An interim solution - and one I'd have preferred to avoid in any case - at best...

---

### Post by cfr42 on 2012-01-03
> **cfr42 said:**
> In my case, the latest version of AMD's proprietary driver works around this issue (sort of). The quality isn't great - I'm seeing lots of corruption when redrawing the screen but it is better than having to disable KMS all the time.

An interim solution - and one I'd have preferred to avoid in any case - at best...

Spoke too soon. It does fix that issue but gnome-shell continually seg-faults...

---

### Post by kullerhamPster on 2012-01-23
Same here, tons of these error messages in the kernel log.

The errors alone wouldn't bother me, yet, they seem to cause short periodic freezes of the mouse and keyboard input.

Using nomodeset makes the errors disappear, but Gnome Shell is no longer working in that case.

There are no such errors when using fglrx instead of radeon, but the official driver shows a worse performance and has some other issues which are at least as annoying as this mouse lag.

---


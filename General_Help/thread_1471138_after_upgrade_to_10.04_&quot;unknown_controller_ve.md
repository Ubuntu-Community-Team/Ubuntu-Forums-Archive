---
title: "after upgrade to 10.04 &quot;unknown controller version you may experience problems&quot;"
date: 2010-05-03
forum: General Help
---

### Post by DrScum on 2010-05-03
Updated from 9.10 to 10.04 and experienced some problems with grub (thread #1470653). 

With the forum help I could fix that but a new problem popped up. I don't know if it existed before or if it came with the fix.

After the boot menue there is an extended black screen with only cursor blinking at the upper left (approx. 15 seconds) then there is an error message saying  something like "unknown controller version you may experience problems" for a very short time, a screen flicker and then the login window appears.

The reason for the extended black period might be some search process resulting in the error message. How do I diagnose something like this and how can I fix it.

---

### Post by isomorph on 2010-05-04
Exactly the same problem here. Same message, same blinking.

And during working on the PC the mouse pointer sometimes just jumps and takes some time until it is under control again.

cheers

Iso

---

### Post by lotharmat on 2010-05-04
I also get this..

I haven't managed to find anything in the logs as yet.

---

### Post by DrScum on 2010-05-04
Obviously I had the Problem before upgrading since you guys are using 9.04 and 9.10 respectively.

What hardware are you guys running? I am running a Dell Vostro 1520 and in the meantime found the following entry in the dmesg output:

[16.804351] mmc0: unknown controller version (2). You may experience problems.

The device mmc0 points to a card reader if I interpret correctly what I find on the internet. 

Question to the expert: is there a connection between the extended blinking (which means waiting) and the error message or am I barking up the wrong tree here?

---

### Post by lotharmat on 2010-05-04
I'm fairly sure that's the exact (ish) message I got

Fujitsu Siemens Lifebook
x64
With SD card reader on the front - which works perfectly well

I'll try and did out the dmesg!

---

### Post by lotharmat on 2010-05-04
Found it!

```
[   12.765348] sdhci-pci 0000:08:03.2: SDHCI controller found [1217:7120] (rev 0)
[   12.765376] sdhci-pci 0000:08:03.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.765414] mmc0: Unknown controller version (16). You may experience problems.
[   12.765533] Registered led device: mmc0::
[   12.765581] mmc0: SDHCI controller on PCI [0000:08:03.2] using PIO
```

---

### Post by isomorph on 2010-05-05
I am using ubuntu 10.04 on a Dell Vostro 1520.

dmsg goes like:
6
[   17.647258] mmc0: Unknown controller version (2). You may experience problems

cheers

Iso

---

### Post by lotharmat on 2010-05-05
Interestingly; either I missed the message after I booted with the SD card out or there was no message.

Is this anyone else's experience?

---

### Post by al.adab on 2010-05-05
just read your posts after posting mine [http://ubuntuforums.org/showthread.php?p=9240841#post9240841](http://ubuntuforums.org/showthread.php?p=9240841#post9240841)

I'm wondering if this would might work for you. Also if you know how to pause that screen I see during the booting process (there seems to be a couple of warning messages in it). 

thanks.

---

### Post by lotharmat on 2010-05-05
> **al.adab said:**
> just read your posts after posting mine [http://ubuntuforums.org/showthread.php?p=9240841#post9240841](http://ubuntuforums.org/showthread.php?p=9240841#post9240841)

I'm wondering if this would might work for you. Also if you know how to pause that screen I see during the booting process (there seems to be a couple of warning messages in it). 

thanks.

I've just tried that and it stopped my SD card from being seen - Which I should have expected really!;)

---

### Post by al.adab on 2010-05-05
oops :) sorry :) 
in the end I reinstalled ubuntu 10.04. The problem seems to be gone now...but will check again and get back to this thread on this.

---

### Post by dino99 on 2010-05-05
[http://manpages.ubuntu.com/manpages/lucid/man4/sdhci.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/sdhci.4freebsd.html)

you may want to try with other kernel too:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by al.adab on 2010-05-05
sorry...how do you edit the kernel configuration file in ubuntu 10.04? I tried *sudo gedit /boot/grub/menu.lst* but the file is empty...

also is it completely safe to compile the file according to 
[http://manpages.ubuntu.com/manpages/lucid/man4/sdhci.4freebsd.html?](http://manpages.ubuntu.com/manpages/lucid/man4/sdhci.4freebsd.html?)

---

### Post by al.adab on 2010-05-05
...er...anyone?

---

### Post by isomorph on 2010-05-31
nowhere any answer neither here: [https://bugs.launchpad.net/ubuntu/+bug/323159](https://bugs.launchpad.net/ubuntu/+bug/323159)

nor here. i have all the updates but problem is not solved yet.

Strange

cheers


Iso

---

### Post by bjordan1979 on 2010-06-01
I have the same issue running 10.04. However my install was a clean install not an upgrade.

Kernel version:

Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3  (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed 

On boot I see a blinking cursor for a while the error blips up on the  screen then the boot splash screen starts. My kern.log has:

------------------------------------------
Jun  1 19:40:59 Workstation20 kernel: [   14.158573] sdhci: Secure  Digital Host Controller Interface driver
Jun  1 19:40:59 Workstation20 kernel: [   14.158577] sdhci: Copyright(c)  Pierre Ossman
Jun  1 19:40:59 Workstation20 kernel: [   14.160559] sdhci-pci  0000:03:05.2: SDHCI controller found [1217:7120] (rev 1)
Jun  1 19:40:59 Workstation20 kernel: [   14.160583] sdhci-pci  0000:03:05.2: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) ->  IRQ 19
**Jun  1 19:40:59 Workstation20 kernel: [   14.160617] mmc0: Unknown  controller version (16). You may experience problems.**
Jun  1 19:40:59 Workstation20 kernel: [   14.160723] Registered led  device: mmc0::
Jun  1 19:40:59 Workstation20 kernel: [   14.160778] mmc0: SDHCI  controller on PCI [0000:03:05.2] using PIO
------------------------------------------

My card reader still works correctly. I recently copied images from an  SD card.

I'm on an Averatec 2300 series notebook.

I'd love to resolve the issue. More importantly find a way to speed up  my boot times. It probably sits on the blinking cursor for about 15  seconds (maybe more). Which is really annoying on boot.

---

### Post by sf_basilix on 2010-06-23
same problem here.

Ubuntu 10.04 (lucid) fresh install
Dell Latitude E6510 w/Intel Core i5 and Intel integrated graphics


$ dmesg | grep -i mmc
[    0.786323] PCI: Using MMCONFIG at f8000000 - fbffffff
[   10.473322] mmc0: Unknown controller version (2). You may experience problems.
[   10.473437] Registered led device: mmc0::
[   10.473475] mmc0: SDHCI controller on PCI [0000:03:00.1] using ADMA



$ lspci | grep SD
03:00.1 SD Host controller: Ricoh Co Ltd Device e822 (rev 03)

---

### Post by .K. on 2010-06-25
I have the same problem, any solution yet?

---

### Post by bach on 2010-06-28
Same here, DELL D6510. Any solution?

---

### Post by bach on 2010-07-01
Ubuntu 10.04 64 bits on DELL Latitude E6510 with Intel integrated graphics; bios is A03. I can only boot using the kernel option "i915.modeset=0". The problem is that it boots in low-graphics mode. The X log file has 

(EE) intel(0): No kernel modesetting driver detected 

I have the latest xserver-xorg-video-intel installed (from ppa). I have already tried more recent kernels, but to no success. 

Tips are extremely welcome. I am going nuts over this... Thanks.

---

### Post by klossner on 2010-07-01
I also am trying to run Ubuntu on a Latitude E6510.  I just yesterday found a patch that lets me run the KMS Intel video driver:
[http://bugs.freedesktop.org/show_bug.cgi?id=28070](http://bugs.freedesktop.org/show_bug.cgi?id=28070)
Suspend/resume still doesn't work: the rest of the system resumes but the screen remains blank.  That's being tracked here:
[http://bugs.freedesktop.org/show_bug.cgi?id=28739](http://bugs.freedesktop.org/show_bug.cgi?id=28739)

(I know, this is not on topic for this thread.  I tried to send it as a private message but ubuntuforums.org says I can't do that until I have 75 posts.)

---

### Post by bach on 2010-07-02
Klossner, could you please give us more details? Which packages have you installed/upgraded? Which kernel options are you using? Are you using "i915.modeset=0" as a kernel option? Thanks a lot in advance.

---

### Post by klossner on 2010-07-02
I'm running standard 10.04, with the exception of the kernel, which I built by taking the upstream 2.6.34 kernel and applying that patch.  I'm running with no kernel command-line options which means I'm using the default i915.modeset=1.  I get full graphics support, including compiz effects.

Now I'm chasing several other kernel problems on my E6510, but I don't want to take this thread off topic.  You can email me directly by building an email address of the form my-first-name at-sign my-last-name dot org.

Andrew Klossner

---

### Post by johnathanamber on 2010-07-10
Hey everyone,

I am also having the same boot lag problem.

When I boot up, the system lags a good ~15 seconds.

I've added several performance tweaks found here:
[http://linux.aldeby.org/speed-up-your-ubuntu-linux-boot.html](http://linux.aldeby.org/speed-up-your-ubuntu-linux-boot.html)

Also here are the logs, pretty much the same as some others:
dmesg:
------------------------------------------------
[   22.952020] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   22.953223] dell-laptop: Blacklisted hardware detected - not loading
[   22.954669] sdhci: Secure Digital Host Controller Interface driver
[   22.954671] sdhci: Copyright(c) Pierre Ossman
[   22.955961] sdhci-pci 0000:1a:00.1: SDHCI controller found [1217:8120] (rev 1)
[   22.956003] sdhci-pci 0000:1a:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.956030] mmc0: Unknown controller version (2). You may experience problems.
[   22.956207] sdhci-pci 0000:1a:00.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   22.956222] sdhci-pci 0000:1a:00.1: setting latency timer to 64
[   22.956264] Registered led device: mmc0::
[   22.956306] mmc0: SDHCI controller on PCI [0000:1a:00.1] using DMA
------------------------------------------------

Any insight into this, diagnosis suggestions or other help would be greatly appreciated.

Attached is my last bootchart image.

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2010-07-14
Any ideas or assistance would be greatly appreciated.

---

### Post by johnathanamber on 2010-07-16
Found this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159?comments=all)

And this:
[https://answers.launchpad.net/ubuntu/+question/2535](https://answers.launchpad.net/ubuntu/+question/2535)

The 2nd looks promising however there is a broken link.

Any help would be appreciated.

I wonder if the Ubuntu team would mind including this driver in an update or the next revision to resolve this issue from now on?

Thank you and God bless,
Johnthan

---

### Post by johnathanamber on 2010-07-16
OK, went ahead and did the update, and for me it didn't work.

Here is what I have thus far:
```

#!/bin/sh
# Fix the mmc "unknown controller" issue in Ubuntu with O2Micro MMC Readers
# See: http://www.denraf.be/content/o2micro-cardreader-dell-acer
# See: http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-11/msg08170.html

# Install libhal-dev for PCSCLITE
sudo apt-get -y install libhal-dev

# Get PCSCLITE from http://pcsclite.alioth.debian.org/
wget https://alioth.debian.org/frs/download.php/3298/pcsc-lite-1.6.1.tar.bz2

# Install pcsclite
tar jxvf pcsc-lite-1.6.1.tar.bz2
cd pcsc-lite-1.6.1
sudo ./configure
sudo make
sudo make install
cd ..

# Get the source code to convert, Check out: http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-11/msg08170.html
wget http://pieleric.free.fr/o2scr/O2Micro_PCMCIA_SCR_203_Linux_Kernel26_OpenSource.tar.gz

# Unpack
tar zxvf O2Micro_PCMCIA_SCR_203_Linux_Kernel26_OpenSource.tar.gz
cd OZSCR_2.0.3_Kern_2.6

# Perform the install
sudo ./configure-release
sudo modprobe ozsrclx

```

Also, I've emailed O2Micro. They informed that they will not develop a Linux driver since the Linux community already has.

So we have to figure this out on our own.

Any help would be greatly appreciated.

God bless,
Johnathan

---

### Post by al.adab on 2010-08-11
solved by re-installing Ubuntu :)

---


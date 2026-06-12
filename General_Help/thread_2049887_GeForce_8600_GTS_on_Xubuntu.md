---
title: "GeForce 8600 GTS on Xubuntu"
date: 2012-08-29
forum: General Help
---

### Post by Elvis99 on 2012-08-29
Hi all,

I recently installed 12.04 and switched because of unity to xcfe/xubuntu and now I'm trying to get my graphics card to work. I installed the recommended addittional drivers but I had no luck with running the monitor from the graphics card. It currently runs on the built in graphics. 

I did a lspci -vvv and it says

```

02:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GTS] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device 0891
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    Region 5: I/O ports at d800 [size=128]
    Expansion ROM at feae0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nvidia_current_updates, nvidia_173, nvidia_173_updates, nouveau, nvidiafb


```

but still, when I run the "Nvidia X Server Settings" I only get this message "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." and it does not show the Geforce card. It's quite annoying since the card worked flawlessly with 10.4 :( 

Any help would be greatly appreciated!

---

### Post by oldfred on 2012-08-29
Are you sure it is not running?

nVidia driver activated and apparently being used but reported as not being used by jockey-gtk 
[https://bugs.launchpad.net/jockey/+bug/771788](https://bugs.launchpad.net/jockey/+bug/771788)

---

### Post by Elvis99 on 2012-08-29
> **oldfred said:**
> Are you sure it is not running?


Hi and thanks for reply.
When I plug my monitor into the graphics card, the screen stays black so I guess the answer is yes.

> **oldfred said:**
> 
nVidia driver activated and apparently being used but reported as not being used by jockey-gtk 
[https://bugs.launchpad.net/jockey/+bug/771788](https://bugs.launchpad.net/jockey/+bug/771788)


I did a  sudo lshw -C display

```

  *-display               
       description: VGA compatible controller
       product: RS780L [Radeon HD 3000]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:c0000000-cfffffff ioport:c000(size=256) memory:f9ff0000-f9ffffff memory:f9e00000-f9efffff
  *-display
       description: VGA compatible controller
       product: G84 [GeForce 8600 GTS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:d800(size=128) memory:feae0000-feafffff

```

The Radeon HD 3000 is the on board one. So I guess Xubuntu recognizes the card, but it somehow can't use it for output :confused:

---

### Post by oldfred on 2012-08-29
Since you have the Radeon on board it really is not this, but is it some of the same issues?
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

Are you able to turn off the internal video in BIOS?

---

### Post by Elvis99 on 2012-08-29
> **oldfred said:**
> 
Are you able to turn off the internal video in BIOS?

Unfortunately I can't turn off the other card in BIOS.

But I followed this guide (pasting it for reference to others) , and - at least - now I get a signal from the GeForce, displaying the xcfe background, but I can't see anything on that screen.

[LIST=1]
[*]**From a shell, make a directory**
I did this: Code: 	$ mkdir nvidia 
[*]**Download the latest drivers from nvidia**

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

in my case it was: "NVIDIA-Linux-x86-304.43.run"
[*]**Set up file permissions**:

 	Code:
 	$ chmod 777 NVIDIA-Linux-x86-304.43.run 
you will need to put the name of the file you download here, if it isn't the same.
[*]***Optional*:  open a non-Gui Terminal**

If you are running your shell so far from the gui X interface, then Open up a non-Gui Terminal:

[Control]+[Alt]+[F2] (or [F3] etc ...)
[*]***Optional*: Login to your non-Gui Terminal**

 -- you don't need to do this if you're not running x.
[*]**Clean up all the old apt based packages**:

 	Code:
 	$ sudo apt-get remove 'nvidia*' 
[*]***Optional*: Turn off the X server**

-- don't worry about this if you're not running x.

 	Code:
 	$ sudo /etc/init.d/lightdm stop 
[*]**Install the nvidia driver**

-- this will start a text-based colorful interface that should walk you through the install process, and then offer to rebuild your xorg.conf file, I suggest letting the installer handler this.

 	Code:
 	$ sudo sh NVIDIA-Linux-x86-304.43.run 
* Note you will use the name of your downloaded package here

-- If you have any errors, fix them then run this command again.  

(I had a few problems in this step, until I cleaned everything out with step 6 above)

When everything is ok the last message should be something like:

 	Code:
 	Your X configuration file has been successfully updated.  Installation of
   the NVIDIA Accelerated Graphics Driver for Linux-x86 (version: 185.18.14) is
   now complete. 
Though obviously with the version that you used.
[*]**Restart your X server**

 	Code:
 	$ sudo /etc/init.d/lightdm start 
[/LIST]

Now, the Nvidia X Server Settings still tells me, that I do not appear to be using the NVIDIA X driver and adwises me to run nvidia-xconfig and and restart the X server. :(

---


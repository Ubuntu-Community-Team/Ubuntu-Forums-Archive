---
title: "Limited resolutions with Sandybridge graphics"
date: 2012-09-14
forum: General Help
---

### Post by robertj20112 on 2012-09-14
After finally getting Precise Pangolin installed on wife's Dell Inspiron All-in-one (Intel Sandybridge graphics) by using nomodeset in grub, I find that the monitor is unrecognized (i.e., "default") and screen resolutions are severely limited, with no 16:9 resolutions available.  Resulting screen distortion is not acceptable to her, so she won't use Ubuntu, which she otherwise loves.  Have done numerous searches on forum, tried several suggestions with no success.  Any help will be much appreciated.  I've got to get her away from Windows!!

---

### Post by oldfred on 2012-09-15
What version Intel chip?


#To see video:
sudo lshw | grep -A 11 display
#Resolution:
xwininfo -root


If it is the 500:
Guide to Get the Best Performace from the GMA 500 
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
Intel GMA500 "Poulsbo" video hardware
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
With Startup Disk creator syslinux.cfg includes menu.cfg which includes txt.cfg where settings really are.
[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)

---

### Post by robertj20112 on 2012-09-15
> **oldfred said:**
> What version Intel chip?


#To see video:
sudo lshw | grep -A 11 display
#Resolution:
xwininfo -root


If it is the 500:
Guide to Get the Best Performace from the GMA 500 
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
Intel GMA500 "Poulsbo" video hardware
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
With Startup Disk creator syslinux.cfg includes menu.cfg which includes txt.cfg where settings really are.
[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)

Here are the ouputs from the two commands:

mary@mary-Inspiron-One-2320:~$ sudo lshw | grep -A 11 display 
[sudo] password for mary: 
        *-display UNCLAIMED 
             description: VGA compatible controller 
             product: 2nd Generation Core Processor Family Integrated Graphics Controller 
             vendor: Intel Corporation 
             physical id: 2 
             bus info: pci@0000:00:02.0 
             version: 09 
             width: 64 bits 
             clock: 33MHz 
             capabilities: msi pm vga_controller bus_master cap_list 
             configuration: latency=0 
             resources: memory:fe000000-fe3fffff memory:d0000000-dfffffff ioport:f000(size=64) 
mary@mary-Inspiron-One-2320:~$ xwininfo -root 

xwininfo: Window id: 0x131 (the root window) (has no name) 

  Absolute upper-left X:  0 
  Absolute upper-left Y:  0 
  Relative upper-left X:  0 
  Relative upper-left Y:  0 
  Width: 1280 
  Height: 1024 
  Depth: 24 
  Visual: 0x21 
  Visual Class: TrueColor 
  Border width: 0 
  Class: InputOutput 
  Colormap: 0x20 (installed) 
  Bit Gravity State: NorthWestGravity 
  Window Gravity State: NorthWestGravity 
  Backing Store State: NotUseful 
  Save Under State: no 
  Map State: IsViewable 
  Override Redirect State: no 
  Corners:  +0+0  -0+0  -0-0  +0-0 
  -geometry 1280x1024+0+0 

mary@mary-Inspiron-One-2320:~$

In Windows 7, the display is capable of 1920x1080 resolution.

---

### Post by oldfred on 2012-09-15
Are you sure this is not an Optimus system?

lspci | grep VGA

[http://askubuntu.com/questions/164624/having-trouble-updating-nvidia-drivers](http://askubuntu.com/questions/164624/having-trouble-updating-nvidia-drivers)

Or you can experiment with ppas, but as mentioned that can break things.

[http://askubuntu.com/questions/54464/how-to-install-intel-corporation-2nd-generation-core-processor-family-integrated](http://askubuntu.com/questions/54464/how-to-install-intel-corporation-2nd-generation-core-processor-family-integrated)

---

### Post by robertj20112 on 2012-09-15
> **oldfred said:**
> Are you sure this is not an Optimus system?

lspci | grep VGA

[http://askubuntu.com/questions/164624/having-trouble-updating-nvidia-drivers](http://askubuntu.com/questions/164624/having-trouble-updating-nvidia-drivers)

Or you can experiment with ppas, but as mentioned that can break things.

[http://askubuntu.com/questions/54464/how-to-install-intel-corporation-2nd-generation-core-processor-family-integrated](http://askubuntu.com/questions/54464/how-to-install-intel-corporation-2nd-generation-core-processor-family-integrated)


Don't know what an Optimus system is.  Here is the result of lspci:

mary@mary-Inspiron-One-2320:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
mary@mary-Inspiron-One-2320:~$

I think the root problem is that the nomodeset is preventing the loading of intel drivers and forcing VESA mode, which has limited number of resolutions available, none of which are 16:9.  What I cannot figure out is how to get the intel drivers in play.

---

### Post by bogan on 2012-09-15
Hi!,** robertj20112,**

Please post:```
 lspci -nnk | grep -iA3 VGA
```This will how which driver & modules are in use.

'nomodset' is for nvidia drivers, for Intel it is different, the form is:> Vide MAFoElffen: **Intel i915GM**
There is a known bug with this chipset ....  Some of the  workarounds include using "i915modeset=0" and some "i815modeset=1" in  the kernel boot line But as your Post suggests the Intel driver is not being used, it may not make any difference.

Chao!, **bogan**.

---

### Post by oldfred on 2012-09-15
Someone that actually has a Sandybridge system should comment.

I have not messed with video for ages, as once I install my nVidia driver my desktop works & my laptop with older Intel just works. 

I used to have to edit this, post yours:

cat /etc/X11/xorg.conf

It may just have written a vesa version and we need to undo it?
 This is normally used to use vesa as default?
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

I think some with the newer Sandybridge systems had other boot parameters also?

---

### Post by robertj20112 on 2012-09-15
> **bogan said:**
> Hi!,** robertj20112,**

Please post:```
 lspci -nnk | grep -iA3 VGA
```This will how which driver & modules are in use.

'nomodset' is for nvidia drivers, for Intel it is different, the form is:But as your Post suggests the Intel driver is not being used, it may not make any difference.

Chao!, **bogan**.

Here is the result:

mary@mary-Inspiron-One-2320:~$ lspci -nnk | grep -iA3 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)
	Subsystem: Dell Device [1028:0511]
	Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
mary@mary-Inspiron-One-2320:~$

---

### Post by robertj20112 on 2012-09-15
> **oldfred said:**
> Someone that actually has a Sandybridge system should comment.

I have not messed with video for ages, as once I install my nVidia driver my desktop works & my laptop with older Intel just works. 

I used to have to edit this, post yours:

cat /etc/X11/xorg.conf

It may just have written a vesa version and we need to undo it?
 This is normally used to use vesa as default?
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

I think some with the newer Sandybridge systems had other boot parameters also?

Here are the contents of /etc/X11/xorg.conf:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "record"
    Load  "dbe"
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync 30.0 - 83.0
    VertRefresh 56.0 - 76.0
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync 30.0 - 83.0
    VertRefresh 56.0 - 76.0
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync 30.0 - 83.0
    VertRefresh 56.0 - 76.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card2"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

---

### Post by oldfred on 2012-09-15
Added code tags to your xorg list to make it easier to read.

bogan has been helpful in other threads on video issues, so he is more knowledgeable of the latest issues and how to solve.

In Device I see three versions  Intel, fbdev & vesa. I would think it should use Intel  first and then the other as default. 

If you boot without nomodeset or with the i915modeset=0 option what happens?

---

### Post by robertj20112 on 2012-09-15
> **oldfred said:**
> Added code tags to your xorg list to make it easier to read.

bogan has been helpful in other threads on video issues, so he is more knowledgeable of the latest issues and how to solve.

In Device I see three versions  Intel, fbdev & vesa. I would think it should use Intel  first and then the other as default. 

If you boot without nomodeset or with the i915modeset=0 option what happens?

When I boot without nomodeset, or with i915modeset=0, halfway through the boot process the display goes dark and stays that way.

Since the intel drivers provide many, many more resolutions in Windows 7, and I have only four choices available to me in 12.04, my guess is that the intel driver is not being used in Ubuntu.  Could there be some connection between that and the presence of three monitors listed in xorg.conf?

---

### Post by robertj20112 on 2012-09-15
> **bogan said:**
> Hi!,** robertj20112,**

Please post:```
 lspci -nnk | grep -iA3 VGA
```This will how which driver & modules are in use.

'nomodset' is for nvidia drivers, for Intel it is different, the form is:But as your Post suggests the Intel driver is not being used, it may not make any difference.

Chao!, **bogan**.



My apologies!  When I posted my response to you, I didn't realize it was from a new replier.  Thanks for responding, Bogan.  I hope the output helped

---

### Post by oldfred on 2012-09-15
That may be some other issue? Remove quiet splash and see if you can tell if something is reporting errors or look in log files.

You can use Log File Viewer to review log files. I look in dmesg for boot issues. Not sure if there is a separate one for video issues.

---

### Post by bogan on 2012-09-15
Hi!, **robertj20112**,

The lspci data shows the Id of your GPU Graphics Controller to be: [8086:1c3a] which is the Intel 2000, for which the i915 driver is correct. & is built-in to 12.04.

I agree with **oldfred** that it is worth trying ' i915modeset=0' in the boot line.[Whoops! I see you have just tried that.]

Is your wife really using three screens with an all-in-one box??

If not, and with all those duplicated entries in the X11/xorg.conf file I would be inclined to 'rm' that file, reboot EDit2: Ignore this next bit, I was mixing up with another thread.[COLOR=SandyBrown]and run ```
sudo nvidia-config # and 
gksu nvidia-settings 
```and reboot again.
[/COLOR] 
{ That assumes you tried **oldfred**'s code creating a backup and trying with the sailsafe file, and that produced the file you posted.] Edit2: I do not know if the Intel Controller will work without an xorg.conf file, or of any equivalent Intel config program; perhaps you have to rely on System Settings>Displays.

I cannot claim the expertize **oldfred** credited me with, but I do run a 7650 GS video card sucessfully, as well as a GT520 on the computer I am using at the moment, though I do not have a Sandy Bridge CPU/GPU.

+1 to "Someone that actually has a Sandybridge system should comment."

Edit: [COLOR=Blue]Just read oldfred's latest Post:  Checkout the .xsession-errors file in /home/user[Crtl+h to show hidden files][/COLOR]

Chao!, **bogan..**

---

### Post by robertj20112 on 2012-09-15
> **oldfred said:**
> That may be some other issue? Remove quiet splash and see if you can tell if something is reporting errors or look in log files.

You can use Log File Viewer to review log files. I look in dmesg for boot issues. Not sure if there is a separate one for video issues.

Thanks, I'll try that.  Not sure if I can spot a problem, so I may post the log online if it's not too long.

Here's dmesg:  (Down near the end is reference to vesa)

```
[    0.588015] pci 0000:00:1d.0: PCI INT A disabled
[    0.588036] PCI: CLS 64 bytes, default 64
[    0.588038] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.588040] Placing 64MB software IO TLB between ffff8800b6c0d000 - ffff8800bac0d000
[    0.588041] software IO TLB at phys 0xb6c0d000 - 0xbac0d000
[    0.588330] audit: initializing netlink socket (disabled)
[    0.588342] type=2000 audit(1347727960.460:1): initialized
[    0.607544] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.608959] VFS: Disk quotas dquot_6.5.2
[    0.608996] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.609313] fuse init (API version 7.17)
[    0.609371] msgmni has been set to 7686
[    0.609566] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.609584] io scheduler noop registered
[    0.609585] io scheduler deadline registered
[    0.609607] io scheduler cfq registered (default)
[    0.609686] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.609733] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.609799] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.609838] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.609899] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.609937] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.610000] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.610038] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.610117] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.610122] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.610137] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.610139] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.610143] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.610159] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.610163] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.610178] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.610180] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.610184] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    0.610194] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.610211] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.610246] intel_idle: MWAIT substates: 0x1120
[    0.610247] intel_idle: v0.4 model 0x2A
[    0.610248] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.610313] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.610317] ACPI: Power Button [PWRB]
[    0.610349] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.610351] ACPI: Power Button [PWRF]
[    0.611246] ERST: Table is not found!
[    0.611248] GHES: HEST is not enabled!
[    0.611294] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.632278] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.699655] Freeing initrd memory: 13864k freed
[    0.796995] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.812166] Linux agpgart interface v0.103
[    0.812219] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    0.812340] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.813287] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    0.813385] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.814341] brd: module loaded
[    0.814832] loop: module loaded
[    0.814921] ahci 0000:00:1f.2: version 3.0
[    0.814932] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.814970] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    0.815010] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    0.815013] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    0.815018] ahci 0000:00:1f.2: setting latency timer to 64
[    0.820198] scsi0 : ahci
[    0.820267] scsi1 : ahci
[    0.820323] scsi2 : ahci
[    0.820376] scsi3 : ahci
[    0.820456] ata1: SATA max UDMA/133 abar m2048@0xfe505000 port 0xfe505100 irq 44
[    0.820459] ata2: SATA max UDMA/133 abar m2048@0xfe505000 port 0xfe505180 irq 44
[    0.820460] ata3: DUMMY
[    0.820461] ata4: DUMMY
[    0.820697] Fixed MDIO Bus: probed
[    0.820710] tun: Universal TUN/TAP device driver, 1.6
[    0.820711] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.820754] PPP generic driver version 2.4.2
[    0.820823] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.820837] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.820851] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.820854] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.820889] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.820911] ehci_hcd 0000:00:1a.0: debug port 2
[    0.824792] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.824805] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfe507000
[    0.839920] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.840042] hub 1-0:1.0: USB hub found
[    0.840046] hub 1-0:1.0: 2 ports detected
[    0.840093] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.840104] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.840107] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.840139] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.840158] ehci_hcd 0000:00:1d.0: debug port 2
[    0.844042] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.844053] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe506000
[    0.859913] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.860021] hub 2-0:1.0: USB hub found
[    0.860024] hub 2-0:1.0: 2 ports detected
[    0.860063] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.860072] uhci_hcd: USB Universal Host Controller Interface driver
[    0.860103] usbcore: registered new interface driver libusual
[    0.860128] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.864657] i8042: Detected active multiplexing controller, rev 1.1
[    0.866249] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.866254] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.866274] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.866289] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.866305] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.866383] mousedev: PS/2 mouse device common for all mice
[    0.866487] rtc_cmos 00:04: RTC can wake from S4
[    0.866621] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.866657] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.866710] device-mapper: uevent: version 1.0.3
[    0.866760] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.866800] cpuidle: using governor ladder
[    0.866854] cpuidle: using governor menu
[    0.866855] EFI Variables Facility v0.08 2004-May-17
[    0.866991] TCP cubic registered
[    0.867057] NET: Registered protocol family 10
[    0.867337] NET: Registered protocol family 17
[    0.867340] Registering the dns_resolver key type
[    0.867514] PM: Hibernation image not present or could not be loaded.
[    0.867524] registered taskstats version 1
[    0.872435]   Magic number: 12:182:894
[    0.872532] rtc_cmos 00:04: setting system clock to 2012-09-15 16:52:41 UTC (1347727961)
[    0.872842] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.872844] EDD information not available.
[    0.992786] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.011267] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[    1.011272] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[    1.139867] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.139902] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.141110] ata1.00: ATA-8: ST3500413AS, JC49, max UDMA/133
[    1.141115] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.142602] ata1.00: configured for UDMA/133
[    1.142853] scsi 0:0:0:0: Direct-Access     ATA      ST3500413AS      JC49 PQ: 0 ANSI: 5
[    1.142954] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.142987] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.143166] sd 0:0:0:0: [sda] Write Protect is off
[    1.143170] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.143271] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.143756] ata2.00: ATAPI: TSSTcorp DVD+/-RW SN-208BB, D100, max UDMA/100
[    1.149978] ata2.00: configured for UDMA/100
[    1.151865] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.158426] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW SN-208BB D100 PQ: 0 ANSI: 5
[    1.172316] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.172322] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.172511] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.172625] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.196109]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.197166] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.198387] Freeing unused kernel memory: 920k freed
[    1.198500] Write protecting the kernel read-only data: 12288k
[    1.202460] Freeing unused kernel memory: 1616k freed
[    1.205557] Freeing unused kernel memory: 1200k freed
[    1.211177] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[    1.211180] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[    1.217496] udevd[93]: starting version 175
[    1.251184] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.251207] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.251247] r8169 0000:04:00.0: setting latency timer to 64
[    1.251330] r8169 0000:04:00.0: irq 45 for MSI/MSI-X
[    1.251635] r8169 0000:04:00.0: eth0: RTL8168evl/8111evl at 0xffffc9000064e000, 00:21:70:66:72:bb, XID 0c900800 IRQ 45
[    1.251638] r8169 0000:04:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.284233] hub 1-1:1.0: USB hub found
[    1.284330] hub 1-1:1.0: 4 ports detected
[    1.395772] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.409852] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[    1.409857] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[    1.528402] hub 2-1:1.0: USB hub found
[    1.528499] hub 2-1:1.0: 6 ports detected
[    1.599744] usb 1-1.2: new high-speed USB device number 3 using ehci_hcd
[    1.603688] Refined TSC clocksource calibration: 2693.880 MHz.
[    1.603694] Switching to clocksource tsc
[    1.613173] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[    1.613178] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[    1.665094] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    1.767866] usb 1-1.3: new full-speed USB device number 4 using ehci_hcd
[    1.813162] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[    1.813167] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[    1.931634] usb 1-1.4: new high-speed USB device number 5 using ehci_hcd
[    2.012926] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[    2.012931] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[    2.395603] usb 2-1.4: new high-speed USB device number 3 using ehci_hcd
[    2.695513] usb 2-1.6: new full-speed USB device number 4 using ehci_hcd
[    9.105569] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.662216] udevd[450]: starting version 175
[    9.682999] Adding 7812092k swap on /dev/sda6.  Priority:-1 extents:1 across:7812092k 
[    9.702046] mei: module is from the staging directory, the quality is unknown, you have been warned.
[    9.703214] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.703220] mei 0000:00:16.0: setting latency timer to 64
[    9.703277] mei 0000:00:16.0: irq 46 for MSI/MSI-X
[    9.703961] lp: driver loaded but no devices found
[    9.707152] [drm] Initialized drm 1.1.0 20060810
[    9.711782] cfg80211: Calling CRDA to update world regulatory domain
[    9.717800] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[    9.717803] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[    9.724009] ath9k 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.724022] ath9k 0000:02:00.0: setting latency timer to 64
[    9.731653] wmi: Mapper loaded
[    9.732648] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.732651] pci 0000:00:02.0: setting latency timer to 64
[    9.773121] ath: EEPROM regdomain: 0x60
[    9.773123] ath: EEPROM indicates we should expect a direct regpair map
[    9.773126] ath: Country alpha2 being used: 00
[    9.773127] ath: Regpair used: 0x60
[    9.773129] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    9.773131] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773133] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    9.773135] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773136] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    9.773138] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773140] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    9.773141] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773143] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    9.773145] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773146] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    9.773148] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773150] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    9.773151] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773153] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    9.773155] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773156] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    9.773158] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773160] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    9.773162] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773163] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    9.773165] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773166] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    9.773168] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773170] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    9.773172] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.773173] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    9.773175] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    9.774717] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    9.780989] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    9.781354] Registered led device: ath9k-phy0
[    9.781360] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90000660000, irq=18
[    9.805355] pci 0000:00:02.0: irq 47 for MSI/MSI-X
[    9.805359] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.805360] [drm] No driver support for vblank timestamp query.
[    9.805470] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    9.805604] acpi device:33: registered as cooling_device2
[    9.805663] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input3
[    9.805725] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.805764] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.829276] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    9.859545] Bluetooth: Core ver 2.16
[    9.859563] NET: Registered protocol family 31
[    9.859564] Bluetooth: HCI device and connection manager initialized
[    9.859566] Bluetooth: HCI socket layer initialized
[    9.859568] Bluetooth: L2CAP socket layer initialized
[    9.859571] Bluetooth: SCO socket layer initialized
[    9.859835] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    9.863148] usbcore: registered new interface driver btusb
[    9.876794] Linux video capture interface: v2.00
[    9.880525] input: Dell Dell KM632 Wireless Keyboard and Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input4
[    9.880651] generic-usb 0003:413C:2501.0001: input,hidraw0: USB HID v1.11 Keyboard [Dell Dell KM632 Wireless Keyboard and Mouse] on usb-0000:00:1d.0-1.6/input0
[    9.883881] input: Dell Dell KM632 Wireless Keyboard and Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/input/input5
[    9.884054] generic-usb 0003:413C:2501.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Dell Dell KM632 Wireless Keyboard and Mouse] on usb-0000:00:1d.0-1.6/input1
[    9.885653] input: Dell Dell KM632 Wireless Keyboard and Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/input/input6
[    9.885776] generic-usb 0003:413C:2501.0003: input,hidraw2: USB HID v1.11 Mouse [Dell Dell KM632 Wireless Keyboard and Mouse] on usb-0000:00:1d.0-1.6/input2
[    9.885805] usbcore: registered new interface driver usbhid
[    9.885807] usbhid: USB HID core driver
[    9.896236] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (04f2:b2a8)
[    9.908233] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.914535] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[    9.914538] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[    9.917802] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[    9.918331] Initializing rts5139 USB card reader driver...
[    9.932786] scsi4 : SCSI emulation for RTS5139 USB card reader
[    9.938543] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    9.938895] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    9.939903] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    9.940768] usbcore: registered new interface driver rts5139
[    9.940770] Realtek rts5139 USB card reader support registered.
[    9.946013] input: Dell AIO WMI hotkeys as /devices/virtual/input/input7
[    9.949110] type=1400 audit(1347742370.578:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=666 comm="apparmor_parser"
[    9.949118] type=1400 audit(1347742370.578:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=642 comm="apparmor_parser"
[    9.949406] type=1400 audit(1347742370.578:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=666 comm="apparmor_parser"
[    9.949412] type=1400 audit(1347742370.578:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=642 comm="apparmor_parser"
[    9.949571] type=1400 audit(1347742370.578:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=666 comm="apparmor_parser"
[    9.949578] type=1400 audit(1347742370.578:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=642 comm="apparmor_parser"
[    9.996917] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    9.996920] cfg80211: World regulatory domain updated:
[    9.996921] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.996923] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.996925] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.996927] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.996929] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.996930] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.009643] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.009690] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   10.009712] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   10.022976] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input8
[   10.023031] usbcore: registered new interface driver uvcvideo
[   10.023032] USB Video Class driver (1.1.1)
[   10.031667] init: failsafe main process (778) killed by TERM signal
[   10.056667] hda_codec: ALC269: SKU not ready 0x598301f0
[   10.060361] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   10.060457] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.060537] input: HDA Intel PCH Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.061946] ppdev: user-space parallel port driver
[   10.114431] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[   10.114434] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[   10.173604] type=1400 audit(1347742370.802:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=878 comm="apparmor_parser"
[   10.173948] type=1400 audit(1347742370.802:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=878 comm="apparmor_parser"
[   10.176179] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.176181] Bluetooth: BNEP filters: protocol multicast
[   10.199480] type=1400 audit(1347742370.826:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=916 comm="apparmor_parser"
[   10.204898] type=1400 audit(1347742370.830:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=915 comm="apparmor_parser"
[   10.208880] Bluetooth: RFCOMM TTY layer initialized
[   10.208884] Bluetooth: RFCOMM socket layer initialized
[   10.208885] Bluetooth: RFCOMM ver 1.11
[   10.241055] usb 2-1.4: reset high-speed USB device number 3 using ehci_hcd
[   10.372941] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.373740] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.509960] r8169 0000:04:00.0: eth0: link down
[   10.510234] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.510471] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.674989] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.674992] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.674994] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.674996] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.674998] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.675000] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.675001] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.675003] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.675004] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.675006] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.675008] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.675010] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.675011] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.675013] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.675015] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.675016] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.675018] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.675020] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.675021] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.675023] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.675025] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.675026] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.675028] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.675030] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.675031] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.675033] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.675035] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.675037] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.675112] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[   10.675463] Registered led device: rt73usb-phy1::radio
[   10.675475] Registered led device: rt73usb-phy1::assoc
[   10.675488] Registered led device: rt73usb-phy1::quality
[   10.675933] usbcore: registered new interface driver rt73usb
[   11.027586] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   11.027800] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   11.068551] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   11.068554] vesafb: scrolling: redraw
[   11.068556] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   11.069723] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90015b00000, using 5120k, total 5120k
[   11.069846] Console: switching to colour frame buffer device 160x64
[   11.069867] fb0: VESA VGA frame buffer device
[   11.084565] init: plymouth-splash main process (1208) terminated with status 1
[   13.380574] wlan0: authenticate with 00:e0:98:d3:00:11 (try 1)
[   13.384734] wlan0: authenticated
[   13.384933] wlan0: associate with 00:e0:98:d3:00:11 (try 1)
[   13.390117] wlan0: RX AssocResp from 00:e0:98:d3:00:11 (capab=0x431 status=0 aid=1)
[   13.390121] wlan0: associated
[   13.390518] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   14.393213] wlan1: authenticate with 00:e0:98:d3:00:11 (try 1)
[   14.394466] wlan1: authenticated
[   14.451060] wlan1: associate with 00:e0:98:d3:00:11 (try 1)
[   14.454084] wlan1: RX AssocResp from 00:e0:98:d3:00:11 (capab=0x431 status=0 aid=2)
[   14.454087] wlan1: associated
[   14.466751] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   23.588681] wlan0: no IPv6 routers present
[   25.899189] wlan1: no IPv6 routers present
```
mary@mary-Inspiron-One-2320:~$

---

### Post by oldfred on 2012-09-15
I found these older threads. Not sure if anything useful. Something like the pci=noacpi may be worth testing.

With 11.04:SandyBridge
[http://ubuntuforums.org/showthread.php?t=1817374](http://ubuntuforums.org/showthread.php?t=1817374)
acpi_osi=linux pci=noacpi
[http://ubuntuforums.org/showthread.php?t=1900897](http://ubuntuforums.org/showthread.php?t=1900897)
Testing of 12.04
[http://ubuntuforums.org/showthread.php?t=1927965](http://ubuntuforums.org/showthread.php?t=1927965)

---

### Post by bogan on 2012-09-15
Sorry for my error in Post #13 referring to nvidia-config, I was not thinking straight.

But it is worth trying to boot without any X11/xorg.conf file as recent drivers do not all require one.

Chao!, **bogan**.

---

### Post by robertj20112 on 2012-09-15
[QUOTE=bogan;12240977]Hi!, **robertj20112**,

The lspci data shows the Id of your GPU Graphics Controller to be: [8086:1c3a] which is the Intel 2000, for which the i915 driver is correct. & is built-in to 12.04.

I agree with **oldfred** that it is worth trying ' i915modeset=0' in the boot line.[Whoops! I see you have just tried that.]

Is your wife really using three screens with an all-in-one box??

If not, and with all those duplicated entries in the X11/xorg.conf file I would be inclined to 'rm' that file, reboot EDit2: Ignore this next bit, I was mixing up with another thread.[COLOR=SandyBrown]and run ```
sudo nvidia-config # and 
gksu nvidia-settings 
```and reboot again.
[/COLOR] 
{ That assumes you tried **oldfred**'s code creating a backup and trying with the sailsafe file, and that produced the file you posted.] Edit2: I do not know if the Intel Controller will work without an xorg.conf file, or of any equivalent Intel config program; perhaps you have to rely on System Settings>Displays.

I cannot claim the expertize **oldfred** credited me with, but I do run a 7650 GS video card sucessfully, as well as a GT520 on the computer I am using at the moment, though I do not have a Sandy Bridge CPU/GPU.

+1 to "Someone that actually has a Sandybridge system should comment."

Edit: [COLOR=Blue]Just read oldfred's latest Post:  Checkout the .xsession-errors file in /home/user[Crtl+h to show hidden files][/COLOR]

Chao!, **bogan..**[/QUOTE

Thanks, Bogan.  Only one screen in use -- the all-in-one screen.  That's why I was struck by the three entries.  The following entries in the .xsession-errors file grabbed my attention:

(gnome-settings-daemon:1366): color-plugin-WARNING **: failed to get edid: unable to get EDID for output

(gnome-settings-daemon:1366): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

(gnome-settings-daemon:1366): color-plugin-WARNING **: failed to reset xrandr-default gamma tables: gamma size is zero

Any significance there?

---

### Post by oldfred on 2012-09-15
The EDID errors may just because VESA cannot parse that.

Please use code tags (# in edit panel) when posting code or long outputs to make it easier to read. Also preserves formating.

Try removing/renaming the current xorg. It should just create a new default.

And try some of the other settings from older SandyBridge systems. 

Not sure what else to try??

---

### Post by robertj20112 on 2012-09-15
> **oldfred said:**
> The EDID errors may just because VESA cannot parse that.

Please use code tags (# in edit panel) when posting code or long outputs to make it easier to read. Also preserves formating.

Try removing/renaming the current xorg. It should just create a new default.

And try some of the other settings from older SandyBridge systems. 

Not sure what else to try??

Didn't know about the #; thanks for telling me.  Renamed current xorg to xorg.conf.old.  No new xorg.conf file created upon reboot.  Perhaps o/s used the failsafe one?

I'm stumped (which isn't that hard to do!)

---

### Post by oldfred on 2012-09-15
Did you try any of the settings suggested in ost #16 links.

acpi_osi=linux pci=noacpi

Sometimes a setting that does not seem related solves issues, but that also is a stretch. But I am out of ideas.

---

### Post by robertj20112 on 2012-09-16
> **oldfred said:**
> Did you try any of the settings suggested in ost #16 links.

acpi_osi=linux pci=noacpi

Sometimes a setting that does not seem related solves issues, but that also is a stretch. But I am out of ideas.

Yes, anything that looked at all promising.  Especially the one cited in your post.  I really thought the backlight=vendor might do the trick.  To date, every variation I have tried -- except nomodeset -- has led to the same result: a blank screen in the middle of the boot process, which never goes away.  I'm sorely tempted to try Linux Mint 13, but if this problem is rooted in the kernel, I doubt that will do any good.  However, if the problem is in Unity, maybe it would.  What do you think?

---

### Post by cwsnyder on 2012-09-16
I doubt if using LM13 will be any better, because it uses the same basic drivers & setup as Ubuntu, unless, as you said, it has to do with Unity.

It looks to me from your log file that the system is defaulting to a frame buffer VGA mode, which will definitely limit your graphics resolutions.

Have you tried the **xrandr** terminal command? or any of the 'fixes' from [https://wiki.ubuntu.com/X/Config/Resolution/](https://wiki.ubuntu.com/X/Config/Resolution/) ?  Those methods don't seem to have been listed in any of the posts.

---

### Post by robertj20112 on 2012-09-16
> **cwsnyder said:**
> I doubt if using LM13 will be any better, because it uses the same basic drivers & setup as Ubuntu, unless, as you said, it has to do with Unity.

It looks to me from your log file that the system is defaulting to a frame buffer VGA mode, which will definitely limit your graphics resolutions.

Have you tried the **xrandr** terminal command? or any of the 'fixes' from [https://wiki.ubuntu.com/X/Config/Resolution/](https://wiki.ubuntu.com/X/Config/Resolution/) ?  Those methods don't seem to have been listed in any of the posts.

Thanks for responding, Cwsnyder.

Well, I tried installing LM13, got the same blank screen problem during the install, so it must be in the kernel.
The xrandr command returns:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      76.0* 
   1024x768       76.0  
   800x600        73.0  
   640x480        73.0  

Here's the result of trying to add 1920x1080 (resolution of screen in Windows 7):


```
mary@mary-Inspiron-One-2320:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
mary@mary-Inspiron-One-2320:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr: Failed to get size of gamma for output default
mary@mary-Inspiron-One-2320:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      76.0* 
   1024x768       76.0  
   800x600        73.0  
   640x480        73.0  
  1920x1080_76.00 (0x142)  224.0MHz
        h: width  1920 start 2064 end 2264 total 2608 skew    0 clock   85.9KHz
        v: height 1080 start 1083 end 1088 total 1131           clock   75.9Hz
  1920x1080_60.00 (0x145)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz
mary@mary-Inspiron-One-2320:~$ xrandr --addmode default 1920X1080
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1920X1080"
mary@mary-Inspiron-One-2320:~$ xrandr --addmode default 1920x1080
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1920x1080"
mary@mary-Inspiron-One-2320:~$
``` 



What have I done wrong?

---

### Post by Wim Sturkenboom on 2012-09-16
> 
```

mary@mary-Inspiron-One-2320:~$ cvt 1920 1080 76
# 1920x1080 75.94 Hz (CVT) hsync: 85.89 kHz; pclk: 224.00 MHz
Modeline "1920x1080_76.00" 224.00 1920 2064 2264 2608 1080 1083 1088 1131 -hsync +vsync

```

Are you sure you can do that resolution at 76Hz? I would carefully start with 60Hz.

> 
```

mary@mary-Inspiron-One-2320:~$ xrandr --newmode "1920x1080_76.00" 224.00 1920 2064 2264 2608 1080 1083 1088 1131 -hsync +vsync
xrandr: Failed to get size of gamma for output default
mary@mary-Inspiron-One-2320:~$ xrandr --addmode default 1920X1080
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1920X1080"

```

The last command should probably be 
```

xrandr --addmode default 1920X1080[COLOR="Blue"]**_76**[/COLOR]

```
as that is the name of the new mode that you specified

I have a Intel HD2000 based processor (I3-2120) and had hassles as well to get 1920x1200@60Hz (16:10) going in Ubuntu while Win7 did not have any problems; for me, the issue was solved when I switched the VGA cable (still unknown why). The only way (with the 1st cable) to get the resolution was by using a modeline for 50Hz instead of 60Hz; the monitor was not conviced (stated 1600x1200) but it was 1920x1200. After swapping tjhe video cable the issue was solved, but I guess that that is not an option for you ;)

PS
With regards to posting code
Use *[noparse]```
your text here
```[/noparse]*; that is what the # symbol in the advanced reply-screen does. You're not supposed to simply type a # :D

---

### Post by robertj20112 on 2012-09-16
> **Wim Sturkenboom said:**
> Are you sure you can do that resolution at 76Hz? I would carefully start with 60Hz.


The last command should probably be 
```

xrandr --addmode default 1920X1080[COLOR="Blue"]**_76**[/COLOR]

```
as that is the name of the new mode that you specified

I have a Intel HD2000 based processor (I3-2120) and had hassles as well to get 1920x1200@60Hz (16:10) going in Ubuntu while Win7 did not have any problems; for me, the issue was solved when I switched the VGA cable (still unknown why). The only way (with the 1st cable) to get the resolution was by using a modeline for 50Hz instead of 60Hz; the monitor was not conviced (stated 1600x1200) but it was 1920x1200. After swapping tjhe video cable the issue was solved, but I guess that that is not an option for you ;)

PS
With regards to posting code
Use *[noparse]```
your text here
```[/noparse]*; that is what the # symbol in the advanced reply-screen does. You're not supposed to simply type a # :D

I added some info to that post after you drafted your reply.  I did try the 60 Hz resolution with the same negative results.  When I tried using the 1920x1080_60 name instead of 1920x1080, I got a syntax error for xrandr.  The mode does now exist, according to xrandr, but applying it to "default" is what is failing.  I wonder if that is because 1920x1080 is not an available mode for VESA?

---

### Post by cwsnyder on 2012-09-16
I have had problems before when the display is not recognized (name for display is only default) when using xrandr.  Default as a name doesn't seem to work for setting up new display resolutions which are more than the Screen 0 maximum.  Something about not being able to correctly interpret the EDID causes it to fail.

---

### Post by robertj20112 on 2012-09-16
> **cwsnyder said:**
> I have had problems before when the display is not recognized (name for display is only default) when using xrandr.  Default as a name doesn't seem to work for setting up new display resolutions which are more than the Screen 0 maximum.  Something about not being able to correctly interpret the EDID causes it to fail.

Is there any success to be had in modifying the contents of xorg.conf via gedit, or would that just scramble everything?  I actually renamed xorg.conf to xorg.conf.old and rebooted, but that had no apparent effect at all.  Linux did not create a new xorg.conf.

---

### Post by bogan on 2012-09-16
Hi!, **robertj20112**,

The command to create a new xorg.conf file is: ```
sudo Xorg -configure # you then need to move iot to X11
sudo mv xorg.conf /etc/X11/xorg.conf
``` Caveat!! I have never used this command as nvidia has it own conf creator app. [ Though, presumably, if you opened a Terminal in the /etc/X11/ folder, it would be created there, without the need to move it.]

Also there is a recent thread in which a Poster with a similar problem used this command, and it produced an xorg,conf identical to the one you Posted, complete with three Monitors, each with a different drivers, and multiple entries besides.

Presumably this is because, in both cases, the EIID is not being correctly found; so I do not hold out much hope of any success this way - rather clutching at straws.

Chao!, bogan.

---

### Post by Wim Sturkenboom on 2012-09-16
> 
```

mary@mary-Inspiron-One-2320:~$ xrandr --addmode default 1920x1080
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1920x1080"

```

Your mode is not called 1920x1080, it's called 1920x1080**[COLOR="Blue"]_60[/COLOR]** as I already indicated in my earlier post. So try to use that.

```

xrandr --addmode default 1920x1080[COLOR="Blue"]**_60**[/COLOR]

```

---

### Post by robertj20112 on 2012-09-16
> **Wim Sturkenboom said:**
> Your mode is not called 1920x1080, it's called 1920x1080**[COLOR="Blue"]_60[/COLOR]** as I already indicated in my earlier post. So try to use that.

```

xrandr --addmode default 1920x1080[COLOR="Blue"]**_60**[/COLOR]

```

Thanks for your response.  I had tried 1920x1080_60 and it failed, but in looking over the terminal output, I realized the true name was 1920x1080_60.00.  I had to go through the mode adding process (for some reason, the modes I had added in a previous session were now gone, as were 3 of the four previously-existing VESA modes.)  This time, the addmode worked.  However, when I tried to select that mode from the drop-down list in the Displays GUI, I got an error notice that the chosen mode exceeded the allowable resolution, which was    Minimum  1280x1024, Maximum  1280x1024.

You can see this range limitation in the xrandr output buried in this terminal listing:
```

mary@mary-Inspiron-One-2320:~$ [COLOR="Red"]xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      77.0* [/COLOR]
mary@mary-Inspiron-One-2320:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      77.0* 
mary@mary-Inspiron-One-2320:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
mary@mary-Inspiron-One-2320:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr: Failed to get size of gamma for output default
mary@mary-Inspiron-One-2320:~$[COLOR="Red"] xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      77.0* 
  1920x1080_60.00 (0x14d)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz[/COLOR]
mary@mary-Inspiron-One-2320:~$ xrandr --addmode default 1920x1080_60.00
xrandr: Failed to get size of gamma for output default
mary@mary-Inspiron-One-2320:~$ 
```

So now the question is, how to change these minimum/maximum limits?

---

### Post by Epodx64 on 2012-09-17
You should amend "video=1280x1024-24@75" to Grub (the Linux Boot line)

obviously change 1280x1024 with your native resolution KMS Auto detection is failing when it boots because you either have a rare EDID or it's giving it the wrong EDID.

---

### Post by robertj20112 on 2012-09-17
> **Epodx64 said:**
> You should amend "video=1280x1024-24@75" to Grub (the Linux Boot line)

obviously change 1280x1024 with your native resolution KMS Auto detection is failing when it boots because you either have a rare EDID or it's giving it the wrong EDID.

Thanks so much for your response, Epodx64.

Here is what the line now says (after ro)

```
 ....... quiet splash nomodeset video=1920x1080-24@60 $vt_handoff
```

Is this the right syntax?

After booting, xrandr still shows maximum resolution 1280 x 1024, and 1920x1080 is not in the list of selectable resolutions in Displays GUI
.  (Display native resolution in Win7 is 1920x1080)

---

### Post by Epodx64 on 2012-09-28
> **robertj20112 said:**
> Thanks so much for your response, Epodx64.

Here is what the line now says (after ro)

```
 ....... quiet splash nomodeset video=1920x1080-24@60 $vt_handoff
```Is this the right syntax?

After booting, xrandr still shows maximum resolution 1280 x 1024, and 1920x1080 is not in the list of selectable resolutions in Displays GUI
.  (Display native resolution in Win7 is 1920x1080)

get rid of the nomodeset thats probably forcing vesa to load and the intel graphics driver works fine

---

### Post by robertj20112 on 2012-09-29
> **Epodx64 said:**
> get rid of the nomodeset thats probably forcing vesa to load and the intel graphics driver works fine

Thanks for your suggestion, Epodx64. I have now tried it. When I removed nomodeset, the result was a blank (i.e., dark) screen for both the login screen and (once I typed the password blindly) the desktop.  There must be a way to get the intel graphics driver working, but I haven't found it.  FYI, while I got 10.04LTS to load on this hardware and the display to work without nomodeset, only the same reduced-resolution set of display parameters was available as in 12.04LTS with nomodeset.  Then, when I tried to upgrade to 12.04 (rather than a direct installation of 12.04), the graphics continued working throughout the upgrade until the reboot after installation of changes.  Then I got the blank/dark screen again.  Right now, I am working with a fresh, direct installation of 12.04 again, and that is what I tested your suggestion against.

---

### Post by robertj20112 on 2012-10-22
Problem has been solved in the 3.5 kernel of 12.10.  All resolutions are available, no need to use nomodeset in the boot.  Unfortunately, I cannot benefit from the Long Term Support of 12.04 but must install each successive new version.  Oh, well, maybe the next LTS will work properly out-of-the-(electronic)box!  Thanks to all who tried to help.

---


---
title: "A740GM Built in Video problem"
date: 2011-02-10
forum: General Help
---

### Post by JoeFriday49 on 2011-02-10
This is a follow up post to this one:
 [http://ubuntuforums.org/showthread.php?t=1683265](http://ubuntuforums.org/showthread.php?t=1683265)

I have been unable to make this motherboard work without giving thousands of errors. More info:
AMD64, Ubuntu 10.10 64bit os, with onboard video...  Works really well  all the way to 1680X1050 resolution, but I get this error every 10  seconds added to my syslog... (Using a lower resolution doesn't help)

Any idea's?

Feb  7 09:22:04 AMD-64 kernel: [ 2386.746569] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 62
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746571] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746573] <3>0f 03 03 03 03 01 03 03 03 01 03 03 03 03 03 03  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746575] <3>03 03 03 03 03 01 03 03 03 01 01 01 03 03 03 03  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746577] <3>03 03 03 01 03 01 01 01 01 01 03 03 03 03 03 03  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746579] <3>03 01 03 01 01 01 03 01 01 01 03 03 03 03 03 01  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746581] <3>03 03 03 03 03 03 03 01 03 03 01 01 01 01 03 01  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746584] <3>03 03 03 03 03 03 03 03 03 03 03 01 01 01 01 01  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746586] <3>03 03 03 03 03 03 03 03 03 01 03 03 03 03 01 01  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746590] <3>03 03 03 03 03 03 03 03 03 01 03 01 01 01 01 03  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746591] 
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746594] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746597] [drm:radeon_dvi_detect] *ERROR* DVI-D-1: probed a monitor but no|invalid EDID

I seem to have tried everything without result.  If anyone has been able to make this board run Linux without errors please let me know what version I need to install.  If it is just not compatible I'll add it to the hardware incompatibility list...

---

### Post by gordintoronto on 2011-02-10
You have not identified the motherboard in either message thread. If you open Accessories/Terminal and enter this command:
sudo lshw | more
the motherboard identification will appear on the first screen.

Is it an ECS A740GM-M? Is the BIOS up to date? From pictures on the ECS web site, that board has a DVI connector.

---

### Post by JoeFriday49 on 2011-02-11
> **gordintoronto said:**
> You have not identified the motherboard in either message thread. If you open Accessories/Terminal and enter this command:
sudo lshw | more
the motherboard identification will appear on the first screen.

Is it an ECS A740GM-M? Is the BIOS up to date? From pictures on the ECS web site, that board has a DVI connector.

Now that was strange...  I typed in a big long reply and posted it last night, now it's not here...  Wonder what thread I posted it too?...  LOL

Anyway, here is another reply.  The motherboard is indeed an A740GM-M.  It is a brand new board so should be up to date. The manual indicates that the DVI video is an option on this board, and the board looks to have solder pads available, just no connector or associated circuitry installed. 

I have searched all over this board and out on the web in general, but haven't been able to find anyone that wasn't having trouble with this board, but then again I haven't found another having this same problem either...  And as you know, no one seems to post good results only bad.  (Bit dog barking loudest and the like)

I would just purchase another video card and install it, but I don't want to pour good money after bad.  I can see no way to disable the onboard video in bios so even if another manufactures card didn't generate errors this one may continue.  If someone has installed another card and is using this setup I would love to know how they did it...

My rotate log seems to be working just fine as the log directory doesn't just keep growing, but since this problem generates thousands of lines every few minutes I don't have any usable history on file either...

Thanks for your interest...

---

### Post by JoeFriday49 on 2011-02-11
I booted this thing again just to see if I could find the video portion of the log.  It appears the OS "thinks" the DVI ports are there.  Does it look like it's even allocating memory to these non existent ports? Here's the part of the log: 

Feb 11 09:22:41 AMD-64 kernel: [   18.200096] usbcore: registered new interface driver uvcvideo
Feb 11 09:22:41 AMD-64 kernel: [   18.200098] USB Video Class driver (v0.1.0)
Feb 11 09:22:41 AMD-64 kernel: [   18.216136] [drm] radeon defaulting to kernel modesetting.
Feb 11 09:22:41 AMD-64 kernel: [   18.216140] [drm] radeon kernel modesetting enabled.
Feb 11 09:22:41 AMD-64 kernel: [   18.217040] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb 11 09:22:41 AMD-64 kernel: [   18.219409] [drm] initializing kernel modesetting (RS740 0x1002:0x796E).
Feb 11 09:22:41 AMD-64 kernel: [   18.228447] [drm] register mmio base: 0xFEAF0000
Feb 11 09:22:41 AMD-64 kernel: [   18.228450] [drm] register mmio size: 65536
Feb 11 09:22:41 AMD-64 kernel: [   18.229152] ATOM BIOS: ATI
Feb 11 09:22:41 AMD-64 kernel: [   18.229171] radeon 0000:01:05.0: VRAM: 128M 0xD8000000 - 0xDFFFFFFF (128M used)
Feb 11 09:22:41 AMD-64 kernel: [   18.229174] radeon 0000:01:05.0: GTT: 512M 0xA0000000 - 0xBFFFFFFF
Feb 11 09:22:41 AMD-64 kernel: [   18.229219] [drm] radeon: irq initialized.
Feb 11 09:22:41 AMD-64 kernel: [   18.230458] [drm] Detected VRAM RAM=128M, BAR=128M
Feb 11 09:22:41 AMD-64 kernel: [   18.230463] [drm] RAM width 128bits DDR
Feb 11 09:22:41 AMD-64 kernel: [   18.230549] [TTM] Zone  kernel: Available graphics memory: 1964216 kiB.
Feb 11 09:22:41 AMD-64 kernel: [   18.230551] [TTM] Initializing pool allocator.
Feb 11 09:22:41 AMD-64 kernel: [   18.230579] [drm] radeon: 128M of VRAM memory ready
Feb 11 09:22:41 AMD-64 kernel: [   18.230581] [drm] radeon: 512M of GTT memory ready.
Feb 11 09:22:41 AMD-64 kernel: [   18.230606] [drm] GART: num cpu pages 131072, num gpu pages 131072
Feb 11 09:22:41 AMD-64 kernel: [   18.236472] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
Feb 11 09:22:41 AMD-64 kernel: [   18.250473] [drm] Loading RS690/RS740 Microcode
Feb 11 09:22:41 AMD-64 kernel: [   18.263048] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 11 09:22:41 AMD-64 kernel: [   18.280022] [drm] radeon: ring at 0x00000000A0000000
Feb 11 09:22:41 AMD-64 kernel: [   18.280043] [drm] ring test succeeded in 1 usecs
Feb 11 09:22:41 AMD-64 kernel: [   18.280182] [drm] radeon: ib pool ready.
Feb 11 09:22:41 AMD-64 kernel: [   18.280253] [drm] ib test succeeded in 0 usecs
Feb 11 09:22:41 AMD-64 kernel: [   18.280261] failed to evaluate ATIF got AE_BAD_PARAMETER
Feb 11 09:22:41 AMD-64 kernel: [   18.280264] radeon 0000:01:05.0: Error during ACPI methods call
Feb 11 09:22:41 AMD-64 kernel: [   18.280324] [drm] Default TV standard: NTSC
Feb 11 09:22:41 AMD-64 kernel: [   18.280485] [drm] Radeon Display Connectors
Feb 11 09:22:41 AMD-64 kernel: [   18.280487] [drm] Connector 0:
Feb 11 09:22:41 AMD-64 kernel: [   18.280488] [drm]   VGA
Feb 11 09:22:41 AMD-64 kernel: [   18.280491] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
Feb 11 09:22:41 AMD-64 kernel: [   18.280492] [drm]   Encoders:
Feb 11 09:22:41 AMD-64 kernel: [   18.280494] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Feb 11 09:22:41 AMD-64 kernel: [   18.280495] [drm] Connector 1:
Feb 11 09:22:41 AMD-64 kernel: [   18.280496] [drm]   DVI-D
Feb 11 09:22:41 AMD-64 kernel: [   18.280498] [drm]   HPD2
Feb 11 09:22:41 AMD-64 kernel: [   18.280500] [drm]   DDC: 0x7e40 0x7e60 0x7e44 0x7e64 0x7e48 0x7e68 0x7e4c 0x7e6c
Feb 11 09:22:41 AMD-64 kernel: [   18.280501] [drm]   Encoders:
Feb 11 09:22:41 AMD-64 kernel: [   18.280503] [drm]     DFP2: INTERNAL_DDI
Feb 11 09:22:41 AMD-64 kernel: [   18.280504] [drm] Connector 2:
Feb 11 09:22:41 AMD-64 kernel: [   18.280505] [drm]   DVI-D
Feb 11 09:22:41 AMD-64 kernel: [   18.280507] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
Feb 11 09:22:41 AMD-64 kernel: [   18.280509] [drm]   Encoders:
Feb 11 09:22:41 AMD-64 kernel: [   18.280510] [drm]     DFP3: INTERNAL_LVTM1
Feb 11 09:22:41 AMD-64 kernel: [   18.307704] set volume quirk for QuickCam E3500

---

### Post by JoeFriday49 on 2011-02-25
I've tried 3 different video cards in an attempt to make this thing work without causing all the errors...  This one worked (Nvidia 8400GS pci-e) and disabled  the onboard video!...  No more errors...  I'm gonna' mark this as closed  even though I don't really think that throwing money at the problem was a  proper resolution, but in this case it worked...

---


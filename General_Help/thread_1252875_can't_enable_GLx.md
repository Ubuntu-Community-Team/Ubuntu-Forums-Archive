---
title: "can't enable GLx"
date: 2009-08-29
forum: General Help
---

### Post by sandyd on 2009-08-29
I currently cannot enable GLX in ubuntu.
im using the ati driver (from ati's site) and my card is a ati radeo 3650.

xorg.0.log
```
X.Org X Server 1.6.0                                                                                                                                                                                       
Release Date: 2009-2-25                                                                                                                                                                                    
X Protocol Version 11, Revision 0                                                                                                                                                                          
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu                                                                                                                                               
Current Operating System: Linux garytang-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64                                                                                       
Build Date: 09 April 2009  02:11:54AM                                                                                                                                                                      
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd)                                                                                                                                                      
        Before reporting problems, check http://wiki.x.org                                                                                                                                                 
        to make sure that you have the latest version.                                                                                                                                                     
Markers: (--) probed, (**) from config file, (==) default setting,                                                                                                                                         
        (++) from command line, (!!) notice, (II) informational,                                                                                                                                           
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.                                                                                                                                      
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 29 12:11:31 2009                                                                                                                                       
(==) Using config file: "/etc/X11/xorg.conf"                                                                                                                                                               
(==) ServerLayout "aticonfig Layout"                                                                                                                                                                       
(**) |-->Screen "aticonfig-Screen[0]-0" (0)                                                                                                                                                                
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"                                                                                                                                                              
(**) |   |-->Device "aticonfig-Device[0]-0"                                                                                                                                                                
(**) Option "DontZap" "False"                                                                                                                                                                              
(==) Automatically adding devices                                                                                                                                                                          
(==) Automatically enabling devices                                                                                                                                                                        
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.                                                                                                                                         
        Entry deleted from font path.                                                                                                                                                                      
(==) FontPath set to:                                                                                                                                                                                      
        /usr/share/fonts/X11/misc,                                                                                                                                                                         
        /usr/share/fonts/X11/100dpi/:unscaled,                                                                                                                                                             
        /usr/share/fonts/X11/75dpi/:unscaled,                                                                                                                                                              
        /usr/share/fonts/X11/Type1,                                                                                                                                                                        
        /usr/share/fonts/X11/100dpi,                                                                                                                                                                       
        /usr/share/fonts/X11/75dpi,                                                                                                                                                                        
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,                                                                                                                                                  
        built-ins                                                                                                                                                                                          
(==) ModulePath set to "/usr/lib/xorg/modules"                                                                                                                                                             
(**) Extension "Composite" is enabled                                                                                                                                                                      
(II) Cannot locate a core pointer device.                                                                                                                                                                  
(II) Cannot locate a core keyboard device.                                                                                                                                                                 
(II) The server relies on HAL to provide the list of input devices.                                                                                                                                        
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.                                                                                                                        
(II) Loader magic: 0xb40                                                                                                                                                                                   
(II) Module ABI versions:                                                                                                                                                                                  
        X.Org ANSI C Emulation: 0.4                                                                                                                                                                        
        X.Org Video Driver: 5.0                                                                                                                                                                            
        X.Org XInput driver : 4.0                                                                                                                                                                          
        X.Org Server Extension : 2.0                                                                                                                                                                       
(II) Loader running on linux                                                                                                                                                                               
(++) using VT number 7                                                                                                                                                                                     

(--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3650 rev 0, Mem @ 0xd0000000/268435456, 0xfc000000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)                                                                                                                   
(II) System resource ranges:                                                                                                                                        
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                                                                         
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                                                                     
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                                                                     
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                                                                     
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                                                                         
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]                                                                                                         
(II) "extmod" will be loaded by default.                                                                                                                            
(II) "dbe" will be loaded by default.                                                                                                                               
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.                                                                       
(II) "record" will be loaded by default.                                                                                                                            
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.                                                                       
(II) "dri2" will be loaded by default.                                                                                                                              
(II) LoadModule: "glx"                                                                                                                                              
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so                                                                                                            
(II) Module glx: vendor="FireGL - ATI Technologies Inc."                                                                                                            
        compiled for 7.4.0, module version = 1.0.0                                                                                                                  
(II) Loading extension GLX                                                                                                                                          
(II) LoadModule: "dri"                                                                                                                                              
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so                                                                                                            
(II) Module dri: vendor="X.Org Foundation"                                                                                                                          
        compiled for 7.4.0, module version = 1.0.0                                                                                                                  
(II) Loading extension XFree86-DRI                                                                                                                                  
(II) Loading sub module "fglrxdrm"                                                                                                                                  
(II) LoadModule: "fglrxdrm"                                                                                                                                         
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so                                                                                                            
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."                                                                                                       
        compiled for 1.4.99.906, module version = 8.64.3                                                                                                            
(II) LoadModule: "extmod"                                                                                                                                           
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so                                                                                                         
(II) Module extmod: vendor="X.Org Foundation"                                                                                                                       
        compiled for 1.6.0, module version = 1.0.0                                                                                                                  
        Module class: X.Org Server Extension                                                                                                                        
        ABI class: X.Org Server Extension, version 2.0                                                                                                              
(II) Loading extension MIT-SCREEN-SAVER                                                                                                                             
(II) Loading extension XFree86-VidModeExtension                                                                                                                     
(II) Loading extension XFree86-DGA                                                                                                                                  
(II) Loading extension DPMS                                                                                                                                         
(II) Loading extension XVideo                                                                                                                                       
(II) Loading extension XVideo-MotionCompensation                                                                                                                    
(II) Loading extension X-Resource                                                                                                                                   
(II) LoadModule: "dbe"                                                                                                                                              
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so                                                                                                            
(II) Module dbe: vendor="X.Org Foundation"                                                                                                                          
        compiled for 1.6.0, module version = 1.0.0                                                                                                                  
        Module class: X.Org Server Extension                                                                                                                        
        ABI class: X.Org Server Extension, version 2.0                                                                                                              
(II) Loading extension DOUBLE-BUFFER                                                                                                                                
(II) LoadModule: "record"                                                                                                                                           
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so                                                                                                         
(II) Module record: vendor="X.Org Foundation"                                                                                                                       
        compiled for 1.6.0, module version = 1.13.0                                                                                                                 
        Module class: X.Org Server Extension                                                                                                                        
        ABI class: X.Org Server Extension, version 2.0                                                                                                              
(II) Loading extension RECORD                                                                                                                                       
(II) LoadModule: "dri2"                                                                                                                                             
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so                                                                                                           
(II) Module dri2: vendor="X.Org Foundation"                                                                                                                         
        compiled for 1.6.0, module version = 1.0.0                                                                                                                  
        ABI class: X.Org Server Extension, version 2.0                                                                                                              
(II) Loading extension DRI2                                                                                                                                         
(II) LoadModule: "fglrx"                                                                                                                                            
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so                                                                                                            
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."                                                                                                          
        compiled for 1.4.99.906, module version = 8.64.3                                                                                                            
        Module class: X.Org Video Driver                                                                                                                            
(II) Primary Device is: PCI 01@00:00:0                                                                                                                              
(WW) Falling back to old probe method for fglrx                                                                                                                     
(II) ATI Proprietary Linux Driver Version Identifier:8.64.3                                                                                                         
(II) ATI Proprietary Linux Driver Release Identifier: 8.64                                                                                                          
(II) ATI Proprietary Linux Driver Build Date: Jul 14 2009 21:18:29                                                                                                  
(II) Loading PCS database from /etc/ati/amdpcsdb                                                                                                                    
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0                                                               
(WW) Video driver ABI version of the X server is 5.0                                                                                                                
(--) Chipset Supported AMD Graphics Processor (0x9591) found                                                                                                        
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found                                                                                       
(II) AMD Video driver is running on a device belonging to a group targeted for this release                                                                         
(II) AMD Video driver is signed                                                                                                                                     
(II) resource ranges after xf86ClaimFixedResources() call:                                                                                                          
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                                                                         
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                                                                     
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                                                                     
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                                                                     
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                                                                         
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]                                                                                                         
(II) fglrx(0): pEnt->device->identifier=0xaad880                                                                                                                    
(II) resource ranges after probing:                                                                                                                                 
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                                                                         
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                                                                     
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                                                                     
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                                                                     
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[b]                                                                                                     
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[b]                                                                                                      
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[b]                                                                                                      
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                                                                         
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]                                                                                                         
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[b]                                                                                                         
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[b]                                                                                                        
(II) Setting vga for screen 0.                                                                                                                                      
(II) fglrx(0): === [atiddxPreInit] === begin                                                                                                                        
(II) Loading sub module "vgahw"                                                                                                                                     
(II) LoadModule: "vgahw"                                                                                                                                            
(II) Loading /usr/lib/xorg/modules//libvgahw.so                                                                                                                     
(II) Module vgahw: vendor="X.Org Foundation"                                                                                                                        
        compiled for 1.6.0, module version = 0.1.0                                                                                                                  
        ABI class: X.Org Video Driver, version 5.0                                                                                                                  
(II) fglrx(0): PCI bus 1 card 0 func 0                                                                                                                              
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32                                                                                                                    
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)                                                                                             
(==) fglrx(0): Default visual is TrueColor                                                                                                                          
(**) fglrx(0): Option "dri" "true"                                                                                                                                  
(**) fglrx(0): Option "DPMS" "true"                                                                                                                                 
(==) fglrx(0): RGB weight 888                                                                                                                                       
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)                                                                                                                     
(==) fglrx(0): Gamma Correction for I is 0x06419064                                                                                                                 
(==) fglrx(0): Gamma Correction for II is 0x06419064                                                                                                                
(==) fglrx(0): Buffer Tiling is ON                                                                                                                                  
(II) Loading sub module "fglrxdrm"                                                                                                                                  
(II) LoadModule: "fglrxdrm"                                                                                                                                         
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so                                                                                                          
drmOpenDevice: node name is /dev/dri/card0                                                                                                                          
drmOpenDevice: open result is 9, (OK)                                                                                                                               
drmOpenByBusid: Searching for BusID PCI:1:0:0                                                                                                                       
drmOpenDevice: node name is /dev/dri/card0                                                                                                                          
drmOpenDevice: open result is 9, (OK)                                                                                                                               
drmOpenByBusid: drmOpenMinor returns 9                                                                                                                              
drmOpenByBusid: drmGetBusid reports PCI:1:0:0                                                                                                                       
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 3650" (Chipset = 0x9591)                                                                                            
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x02a0)                                                                                                       
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI                                                                                   
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000                                                                                                              
(--) fglrx(0): MMIO registers at 0xfc000000                                                                                                                         
(--) fglrx(0): I/O port at 0x00002000                                                                                                                               
(==) fglrx(0): ROM-BIOS at 0x000c0000                                                                                                                               
(II) fglrx(0): AC Adapter is used                                                                                                                                   
(II) fglrx(0): Primary V_BIOS segment is: 0xc000                                                                                                                    
(II) Loading sub module "vbe"                                                                                                                                       
(II) LoadModule: "vbe"                                                                                                                                              
(II) Loading /usr/lib/xorg/modules//libvbe.so                                                                                                                       
(II) Module vbe: vendor="X.Org Foundation"                                                                                                                          
        compiled for 1.6.0, module version = 1.1.0                                                                                                                  
        ABI class: X.Org Video Driver, version 5.0                                                                                                                  
(II) fglrx(0): VESA BIOS detected                                                                                                                                   
(II) fglrx(0): VESA VBE Version 3.0                                                                                                                                 
(II) fglrx(0): VESA VBE Total Mem: 16384 kB                                                                                                                         
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS                                                                                                                           
(II) fglrx(0): VESA VBE OEM Software Rev: 10.88                                                                                                                     
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.                                                                                            
(II) fglrx(0): VESA VBE OEM Product: M86                                                                                                                            
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00                                                                                                                      
(II) fglrx(0): ATI Video BIOS revision 9 or later detected                                                                                                          
(--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2                                                                                                                  
(II) fglrx(0): PCIE card detected                                                                                                                                   
(--) fglrx(0): Using per-process page tables (PPPT) as GART.                                                                                                        
(WW) fglrx(0): board is an unknown third party board, chipset is supported                                                                                          
(II) fglrx(0): Using adapter: 1:0.0.                                                                                                                                
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x20000000)                                                                                          
(II) fglrx(0): [pcie] 1992192 kB allocated                                                                                                                          
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536                                                                                            
(II) fglrx(0): Interrupt handler installed at IRQ 2297.                                                                                                             
(II) fglrx(0): IRQ 2297 Enabled.                                                                                                                                    
(II) fglrx(0): RandR 1.2 support is enabled!                                                                                                                        
(II) fglrx(0): RandR 1.2 rotation support is enabled!                                                                                                               
(==) fglrx(0): Center Mode is disabled                                                                                                                              
(II) Loading sub module "fb"                                                                                                                                        
(II) LoadModule: "fb"                                                                                                                                               
(II) Loading /usr/lib/xorg/modules//libfb.so                                                                                                                        
(II) Module fb: vendor="X.Org Foundation"                                                                                                                           
        compiled for 1.6.0, module version = 1.0.0                                                                                                                  
        ABI class: X.Org ANSI C Emulation, version 0.4                                                                                                              
(II) Loading sub module "ddc"                                                                                                                                       
(II) LoadModule: "ddc"                                                                                                                                              
(II) Module "ddc" already built-in                                                                                                                                  
(II) fglrx(0): Finished Initialize PPLIB!                                                                                                                           
(II) Loading sub module "ddc"                                                                                                                                       
(II) LoadModule: "ddc"                                                                                                                                              
(II) Module "ddc" already built-in                                                                                                                                  
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000002, disabled=0x00000000                                                                                    
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]                                                                                                      
(II) fglrx(0): Display1 EDID data ---------------------------                                                                                                       
(II) fglrx(0): Manufacturer: LPL  Model: 0  Serial#: 0                                                                                                              
(II) fglrx(0): Year: 2007  Week: 0                                                                                                                                  
(II) fglrx(0): EDID Version: 1.3                                                                                                                                    
(II) fglrx(0): Digital Display Input                                                                                                                                
(II) fglrx(0): Max Image Size [cm]: horiz.: 37  vert.: 23                                                                                                           
(II) fglrx(0): Gamma: 2.20                                                                                                                                          
(II) fglrx(0): No DPMS capabilities specified                                                                                                                       
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4                                                                                                     
(II) fglrx(0): First detailed timing is preferred mode                                                                                                              
(II) fglrx(0): redX: 0.602 redY: 0.351   greenX: 0.322 greenY: 0.554                                                                                                
(II) fglrx(0): blueX: 0.157 blueY: 0.146   whiteX: 0.312 whiteY: 0.328                                                                                              
(II) fglrx(0): Manufacturer's mask: 0                                                                                                                               
(II) fglrx(0): Supported additional Video Mode:                                                                                                                     
(II) fglrx(0): clock: 109.5 MHz   Image Size:  367 x 230 mm                                                                                                         
(II) fglrx(0): h_active: 1440  h_sync: 1510  h_sync_end 1550 h_blank_end 1974 h_border: 0                                                                           
(II) fglrx(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 912 v_border: 0                                                                               
(WW) fglrx(0): Unknown vendor-specific block 0                                                                                                                      
(II) fglrx(0):  RM247                                                                                                                                               
(II) fglrx(0):  .>ISt&#65533;&#65533;&#65533;                                                                                                                                            
(II) fglrx(0): EDID (in hex):                                                                                                                                       
(II) fglrx(0):  00ffffffffffff00320c000000000000                                                                                                                    
(II) fglrx(0):  00110103902517780a3b609a59528d28                                                                                                                    
(II) fglrx(0):  25505400000001010101010101010101                                                                                                                    
(II) fglrx(0):  010101010101c62aa01652840c304628                                                                                                                    
(II) fglrx(0):  13006fe6100000190000000000000000                                                                                                                    
(II) fglrx(0):  00000000000000000000000000fe0052                                                                                                                    
(II) fglrx(0):  4d323437003137315750340a000000fe                                                                                                                    
(II) fglrx(0):  002e3e49537497c6ff02010a20200065                                                                                                                    
(II) fglrx(0): End of Display1 EDID data --------------------                                                                                                       
(II) fglrx(0): Output LCD using monitor section aticonfig-Monitor[0]-0                                                                                              
(II) fglrx(0): Output DFP1 has no monitor section                                                                                                                   
(II) fglrx(0): Output CRT1 has no monitor section                                                                                                                   
(II) fglrx(0): EDID vendor "LPL", prod id 0                                                                                                                         
(II) fglrx(0):     EDID quirk: Detailed timings give sizes in cm.                                                                                                   
(II) fglrx(0): Printing DDC gathered Modelines:                                                                                                                     
(II) fglrx(0): Modeline "1440x900"x0.0  109.50  1440 1510 1550 1974  900 901 904 912 -hsync -vsync (55.5 kHz)                                                       
(II) fglrx(0): Output LCD connected                                                                                                                                 
(II) fglrx(0): Output DFP1 disconnected                                                                                                                             
(II) fglrx(0): Output CRT1 disconnected                                                                                                                             
(II) fglrx(0): Using exact sizes for initial modes                                                                                                                  
(II) fglrx(0): Output LCD using initial mode 1440x900                                                                                                               
(**) fglrx(0): Display dimensions: (370, 230) mm                                                                                                                    
(**) fglrx(0): DPI set to (98, 159)                                                                                                                                 
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)                                                                                                               
(==) fglrx(0): QBS disabled                                                                                                                                         
(==) fglrx(0): FAST_SWAP disabled                                                                                                                                   
(==) fglrx(0):  PseudoColor visuals disabled                                                                                                                        
(II) Loading sub module "ramdac"                                                                                                                                    
(II) LoadModule: "ramdac"                                                                                                                                           
(II) Module "ramdac" already built-in                                                                                                                               
(==) fglrx(0): NoAccel = NO                                                                                                                                         
(II) Loading sub module "xaa"                                                                                                                                       
(II) LoadModule: "xaa"                                                                                                                                              
(II) Loading /usr/lib/xorg/modules//libxaa.so                                                                                                                       
(II) Module xaa: vendor="X.Org Foundation"                                                                                                                          
        compiled for 1.6.0, module version = 1.2.1                                                                                                                  
        ABI class: X.Org Video Driver, version 5.0                                                                                                                  
(**) fglrx(0): NoDRI = NO                                                                                                                                           
(==) fglrx(0): Capabilities: 0x00000000                                                                                                                             
(==) fglrx(0): CapabilitiesEx: 0x00000000                                                                                                                           
(==) fglrx(0): cpuFlags: 0x8000001d                                                                                                                                 
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"                                                                                                              
(==) fglrx(0): UseFastTLS=0                                                                                                                                         
(==) fglrx(0): BlockSignalsOnLock=1                                                                                                                                 
(--) Depth 24 pixmap format is 32 bpp                                                                                                                               
(II) do I need RAC?  No, I don't.                                                                                                                                   
(II) resource ranges after preInit:                                                                                                                                 
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                                                                         
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                                                                     
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                                                                     
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                                                                     
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[b](OprU)                                                                                               
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)                                                                                                
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)                                                                                                
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                                                                         
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]                                                                                                         
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[b](OprU)                                                                                                   
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[b](OprU)                                                                                                  
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906                                                                                                        
(WW) fglrx(0): could not detect X server version (query_status=-1)                                                                                                  
(II) Loading extension ATIFGLRXDRI                                                                                                                                  
(II) fglrx(0): doing DRIScreenInit                                                                                                                                  
(II) fglrx(0): DRIScreenInit for fglrx driver                                                                                                                       
drmOpenDevice: node name is /dev/dri/card0                                                                                                                          
drmOpenDevice: open result is 12, (OK)                                                                                                                              
drmOpenDevice: node name is /dev/dri/card0                                                                                                                          
drmOpenDevice: open result is 12, (OK)                                                                                                                              
drmOpenByBusid: Searching for BusID PCI:1:0:0                                                                                                                       
drmOpenDevice: node name is /dev/dri/card0                                                                                                                          
drmOpenDevice: open result is 12, (OK)                                                                                                                              
drmOpenByBusid: drmOpenMinor returns 12                                                                                                                             
drmOpenByBusid: drmGetBusid reports PCI:1:0:0                                                                                                                       
(II) fglrx(0): [drm] DRM interface version 1.0                                                                                                                      
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"                                                                                                    
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x6f000                                                                                                               
(II) fglrx(0): [drm] mapped SAREA 0x6f000 to 0x7fbd370cf000                                                                                                         
(II) fglrx(0): [drm] framebuffer handle = 0x70000                                                                                                                   
(II) fglrx(0): [drm] added 1 reserved context for kernel                                                                                                            
(II) fglrx(0): DRIScreenInit done                                                                                                                                   
(II) fglrx(0): Kernel Module Version Information:                                                                                                                   
(II) fglrx(0):     Name: fglrx                                                                                                                                      
(II) fglrx(0):     Version: 8.64.3                                                                                                                                  
(II) fglrx(0):     Date: Jul 14 2009                                                                                                                                
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module                                                                                                               
(II) fglrx(0): Kernel Module version matches driver.                                                                                                                
(II) fglrx(0): Kernel Module Build Time Information:                                                                                                                
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.28-11-generic                                                                                               
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes                                                                                                             
(II) fglrx(0):     Build-Kernel __SMP__:            yes                                                                                                             
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000                                                                                                          
(II) fglrx(0): [drm] register handle = 0x00071000                                                                                                                   
(II) fglrx(0): Display width adjusted to to 1536 due to alignment constraints                                                                                       
(II) fglrx(0): DRI initialization successfull!                                                                                                                      
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x010c8000                                                                                                        
(II) fglrx(0): FBMM initialized for area (0,0)-(1536,2864)                                                                                                          
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1536,1536) (front color buffer - assumption)                                                                         
(II) fglrx(0): Largest offscreen area available: 1536 x 1328                                                                                                        
(==) fglrx(0): Backing store disabled                                                                                                                               
(II) Loading extension FGLRXEXTENSION                                                                                                                               
(II) Loading extension ATITVOUT                                                                                                                                     
(**) fglrx(0): DPMS enabled                                                                                                                                         
(**) fglrx(0): Textured Video is enabled.                                                                                                                           
(II) LoadModule: "glesx"                                                                                                                                            
(II) Loading /usr/lib/xorg/modules//glesx.so                                                                                                                        
(II) Module glesx: vendor="X.Org Foundation"                                                                                                                        
        compiled for 1.4.99.906, module version = 1.0.0                                                                                                             
(II) Loading extension GLESX                                                                                                                                        
(II) fglrx(0): GLESX enableFlags = 94                                                                                                                               
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)                                                                                                        
        Screen to screen bit blits                                                                                                                                  
        Solid filled rectangles                                                                                                                                     
        Solid Horizontal and Vertical Lines                                                                                                                         
        Driver provided ScreenToScreenBitBlt replacement                                                                                                            
        Driver provided FillSolidRects replacement                                                                                                                  
(II) fglrx(0): GLESX is enabled                                                                                                                                     
(II) LoadModule: "amdxmm"                                                                                                                                           
(II) Loading /usr/lib/xorg/modules//amdxmm.so                                                                                                                       
(II) Module amdxmm: vendor="X.Org Foundation"                                                                                                                       
        compiled for 1.4.99.906, module version = 1.0.0                                                                                                             
(II) Loading extension AMDXVOPL                                                                                                                                     
(II) fglrx(0): UVD2 feature is available                                                                                                                            
(II) fglrx(0): Enable composite support successfully                                                                                                                
(WW) fglrx(0): Option "AddARGBGLXVisuals" is not used                                                                                                               
(WW) fglrx(0): Option "AllowGLXWithComposite" is not used                                                                                                           
(WW) fglrx(0): Option "VendorName" is not used                                                                                                                      
(WW) fglrx(0): Option "ModelName" is not used                                                                                                                       
(II) fglrx(0): X context handle = 0x1                                                                                                                               
(II) fglrx(0): [DRI] installation complete                                                                                                                          
(==) fglrx(0): Silken mouse enabled                                                                                                                                 
(==) fglrx(0): Using HW cursor of display infrastructure!                                                                                                           
(==) fglrx(0): Using software cursor                                                                                                                                
(II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.                                                                                      
(II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'                                                                                                      
(II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'                                                                                                       
(--) RandR disabled                                                                                                                                                 
(II) Initializing built-in extension Generic Event Extension                                                                                                        
(II) Initializing built-in extension SHAPE                                                                                                                          
(II) Initializing built-in extension MIT-SHM                                                                                                                        
(II) Initializing built-in extension XInputExtension                                                                                                                
(II) Initializing built-in extension XTEST                                                                                                                          
(II) Initializing built-in extension BIG-REQUESTS                                                                                                                   
(II) Initializing built-in extension SYNC                                                                                                                           
(II) Initializing built-in extension XKEYBOARD                                                                                                                      
(II) Initializing built-in extension XC-MISC                                                                                                                        
(II) Initializing built-in extension SECURITY                                                                                                                       
(II) Initializing built-in extension XINERAMA                                                                                                                       
(II) Initializing built-in extension XFIXES                                                                                                                         
(II) Initializing built-in extension RENDER                                                                                                                         
(II) Initializing built-in extension RANDR                                                                                                                          
(II) Initializing built-in extension COMPOSITE                                                                                                                      
(II) Initializing built-in extension DAMAGE                                                                                                                         
(WW) AIGLX: 3D driver claims to not support visual 0x23                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x24                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x25                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x26                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x27                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x28                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x29                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x2a                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x2b                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x2c                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x2d                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x2e                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x2f                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x30                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x31                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x32                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x33                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x34                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x35                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x36                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x37                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x38                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x39                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x3a                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x3b                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x3c                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x3d                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x3e                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x3f                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x40                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x41                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x42                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x43                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x44                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x45                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x46                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x47                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x48                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x49                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x4a                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x4b                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x4c                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x4d                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x4e                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x4f                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x50                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x51                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x52                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x53                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x54                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x55                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x56                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x57                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x58                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x59                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x5a                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x5b                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x5c                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x5d                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x5e                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x5f                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x60                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x61                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x62                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x63                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x64                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x65                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x66                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x67                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x68                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x69                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x6a                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x6b                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x6c                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x6d                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x6e                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x6f                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x70                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x71                                                                                                             
(WW) AIGLX: 3D driver claims to not support visual 0x72                                                                                                             
(II) AIGLX: Loaded and initialized /usr/X11R6/lib64/modules/dri/fglrx_dri.so                                                                                        
(II) GLX: Initialized DRI GL provider for screen 0                                                                                                                  
(II) fglrx(0): Enable the clock gating!                                                                                                                             
(II) fglrx(0): Setting screen physical size to 367 x 230                                                                                                            
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments                                                                     
(II) config/hal: Adding input device AT Translated Set 2 keyboard                                                                                                   
(II) LoadModule: "evdev"                                                                                                                                            
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so                                                                                                              
(II) Module evdev: vendor="X.Org Foundation"                                                                                                                        
        compiled for 1.6.0, module version = 2.1.1                                                                                                                  
        Module class: X.Org XInput Driver                                                                                                                           
        ABI class: X.Org XInput driver, version 4.0                                                                                                                 
(**) AT Translated Set 2 keyboard: always reports core events                                                                                                       
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"                                                                                                      
(II) AT Translated Set 2 keyboard: Found keys                                                                                                                       
(II) AT Translated Set 2 keyboard: Configuring as keyboard                                                                                                          
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)                                                                           
(**) Option "xkb_rules" "evdev"                                                                                                                                     
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"                                                                                                               
(**) Option "xkb_model" "pc105"                                                                                                                                     
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"                                                                                                               
(**) Option "xkb_layout" "us"                                                                                                                                       
(**) AT Translated Set 2 keyboard: xkb_layout: "us"                                                                                                                 
(II) config/hal: Adding input device Macintosh mouse button emulation                                                                                               
(**) Macintosh mouse button emulation: always reports core events                                                                                                   
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"                                                                                                  
(II) Macintosh mouse button emulation: Found 3 mouse buttons                                                                                                        
(II) Macintosh mouse button emulation: Found x and y relative axes                                                                                                  
(II) Macintosh mouse button emulation: Configuring as mouse                                                                                                         
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5                                                                                                
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200                                                     
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)                                                                          
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1                                                                                        
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00                                                                                       
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms                                                                                             
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0                                                                                           
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint                                                                                                       
(II) LoadModule: "synaptics"                                                                                                                                        
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so                                                                                                          
(II) Module synaptics: vendor="X.Org Foundation"                                                                                                                    
        compiled for 1.6.0, module version = 0.99.3                                                                                                                 
        Module class: X.Org XInput Driver                                                                                                                           
        ABI class: X.Org XInput driver, version 4.0                                                                                                                 
(II) Synaptics touchpad driver version 0.99.3                                                                                                                       
(**) Option "Device" "/dev/input/event14"                                                                                                                           
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023                                                                                                                
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767                                                                                                                 
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127                                                                                                               
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0                                                                                                             
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle                                                                                                           
(II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...                                                                              
(--) AlpsPS/2 ALPS GlidePoint touchpad found                                                                                                                        
(**) AlpsPS/2 ALPS GlidePoint: always reports core events                                                                                                           
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)                                                                               
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1                                                                                                
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00                                                                                               
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms                                                                                                     
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0                                                                                                   
(--) AlpsPS/2 ALPS GlidePoint touchpad found                                                                                                                        
(II) config/hal: Adding input device PS/2 Mouse                                                                                                                     
(**) PS/2 Mouse: always reports core events                                                                                                                         
(**) PS/2 Mouse: Device: "/dev/input/event13"                                                                                                                       
(II) PS/2 Mouse: Found 3 mouse buttons                                                                                                                              
(II) PS/2 Mouse: Found x and y relative axes                                                                                                                        
(II) PS/2 Mouse: Configuring as mouse                                                                                                                               
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5                                                                                                                      
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200                                                                           
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)                                                                                                
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1                                                                                                              
(**) PS/2 Mouse: (accel) filter chain progression: 2.00                                                                                                             
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms                                                                                                                   
(**) PS/2 Mouse: (accel) set acceleration profile 0                                                                                                                 
(II) config/hal: Adding input device BTC USB Multimedia Keyboard                                                                                                    
(**) BTC USB Multimedia Keyboard: always reports core events                                                                                                        
(**) BTC USB Multimedia Keyboard: Device: "/dev/input/event8"                                                                                                       
(II) BTC USB Multimedia Keyboard: Found keys                                                                                                                        
(II) BTC USB Multimedia Keyboard: Configuring as keyboard                                                                                                           
(II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD)                                                                            
(**) Option "xkb_rules" "evdev"                                                                                                                                     
(**) BTC USB Multimedia Keyboard: xkb_rules: "evdev"                                                                                                                
(**) Option "xkb_model" "pc105"                                                                                                                                     
(**) BTC USB Multimedia Keyboard: xkb_model: "pc105"                                                                                                                
(**) Option "xkb_layout" "us"
(**) BTC USB Multimedia Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device BTC USB Multimedia Keyboard
(**) BTC USB Multimedia Keyboard: always reports core events
(**) BTC USB Multimedia Keyboard: Device: "/dev/input/event7"
(II) BTC USB Multimedia Keyboard: Found keys
(II) BTC USB Multimedia Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) BTC USB Multimedia Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) BTC USB Multimedia Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) BTC USB Multimedia Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event10"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event6"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) fglrx(0): EDID vendor "LPL", prod id 0
(II) fglrx(0):     EDID quirk: Detailed timings give sizes in cm.
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1440x900"x0.0  109.50  1440 1510 1550 1974  900 901 904 912 -hsync -vsync (55.5 kHz)
(II) fglrx(0): EDID vendor "LPL", prod id 0
(II) fglrx(0):     EDID quirk: Detailed timings give sizes in cm.
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1440x900"x0.0  109.50  1440 1510 1550 1974  900 901 904 912 -hsync -vsync (55.5 kHz)


```output of glxgears
```

Error: couldn't get an RGB, Double-buffered visual


```currently running jaunty x64

and heres the xorg extensions i have installed
```

FGL.renamed.libdri.so  libdbe.so   libdri.so     libglx.so
FGL.renamed.libglx.so  libdri2.so  libextmod.so  librecord.so

```

---

### Post by madu on 2009-08-30
I have the same problem.

My libglx.so file, which is a link to libglx.so.180.60 is in /usr/lib/xorg/modules.
And I have put this path to the xorg.conf but for some reason glx module is not loading. I get a similar response in glxinfo.
And Modprobe says FATAL: Module glx not found.

---

### Post by sandyd on 2009-08-30
i found a fix. open up a terminal and go into /usr/share/ati . then run the uninstallation script. then go and search for "ubuntu ati binary" on google. click the first link and follow the instructions.

---


---
title: "Installing Ubuntu broke Window's Ethernet"
date: 2009-10-31
forum: General Help
---

### Post by MysteryGuy on 2009-10-31
Hey! I downloaded and installed Ubuntu 9.10 while on Windows successfully, and then went straight to testing it, It was very good. 

After like 3hours of testing I decided I wanted to play a game. So I rebooted, switched to windows, and when I go there I notice my ethernet is not working. It says the cable is unplugged. Although it works fine in Linux.

---

### Post by Matt__ on 2009-10-31
what is the make of your ethernet card?
is your windows set to auto update?

I suggest you roll back the windows driver if you have auto update on as Ubuntu wont have done anything to it.
My realtek rtl810 had an update that disabled it in windows but let it still work in Ubuntu...solution=rollback crummy windows driver.

---

### Post by MysteryGuy on 2009-10-31
I tried roll backing but it said I didn't have backups, or something like that; don't remember quite well.

Anyways, here's my DxDiag:
(And yes, I'm Portuguese)

```
------------------ 
System Information 
------------------ 
Time of this report: 10/31/2009, 14:37:20 
       Machine name: XXX-B966A1CEA45 
   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 3 (2600.xpsp_sp3_gdr.090804-1435) 
           Language: Portuguese (Regional Setting: Portuguese) 
System Manufacturer: System manufacturer 
       System Model: System Product Name 
               BIOS: BIOS Date: 08/01/07 09:47:33 Ver: 08.00.10 
          Processor: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz (2 CPUs) 
             Memory: 2048MB RAM 
          Page File: 520MB used, 3418MB available 
        Windows Dir: C:\WINDOWS 
    DirectX Version: DirectX 9.0c (4.09.0000.0904) 
DX Setup Parameters: Not found 
     DxDiag Version: 5.03.2600.5512 32bit Unicode 
 
------------ 
DxDiag Notes 
------------ 
  DirectX Files Tab: No problems found. 
      Display Tab 1: No problems found. 
        Sound Tab 1: No problems found. 
          Music Tab: No problems found. 
          Input Tab: No problems found. 
        Network Tab: No problems found. 
 
-------------------- 
DirectX Debug Levels 
-------------------- 
Direct3D:    0/4 (n/a) 
DirectDraw:  0/4 (retail) 
DirectInput: 0/5 (n/a) 
DirectMusic: 0/5 (n/a) 
DirectPlay:  0/9 (retail) 
DirectSound: 0/5 (retail) 
DirectShow:  0/6 (retail) 
 
--------------- 
Display Devices 
--------------- 
        Card name: NVIDIA GeForce 8500 GT 
     Manufacturer: NVIDIA 
        Chip type: GeForce 8500 GT 
         DAC type: Integrated RAMDAC 
       Device Key: Enum\PCI\VEN_10DE&DEV_0421&SUBSYS_82451043&REV_A1 
   Display Memory: 512.0 MB 
     Current Mode: 1440 x 900 (32 bit) (60Hz) 
          Monitor: Monitor Plug and Play 
  Monitor Max Res: 1600,1200 
      Driver Name: nv4_disp.dll 
   Driver Version: 6.14.0011.9062 (English) 
      DDI Version: 9 (or higher) 
Driver Attributes: Final Retail 
 Driver Date/Size: 8/16/2009 23:57:00, 5845760 bytes 
      WHQL Logo'd: Yes 
  WHQL Date Stamp: n/a 
              VDD: n/d 
         Mini VDD: nv4_mini.sys 
    Mini VDD Date: 8/16/2009 23:57:00, 7729568 bytes 
Device Identifier: {D7B71E3E-4761-11CF-9550-4EA200C2CB35} 
        Vendor ID: 0x10DE 
        Device ID: 0x0421 
        SubSys ID: 0x82451043 
      Revision ID: 0x00A1 
      Revision ID: 0x00A1 
      Video Accel: ModeMPEG2_C ModeMPEG2_D  
 Deinterlace Caps: {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive  
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch  
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive  
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch  
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive  
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch  
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive  
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch  
         Registry: OK 
     DDraw Status: Enabled 
       D3D Status: Enabled 
       AGP Status: Enabled 
DDraw Test Result: Not run 
 D3D7 Test Result: Not run 
 D3D8 Test Result: Not run 
 D3D9 Test Result: Not run 
 
------------- 
Sound Devices 
------------- 
            Description: Realtek HD Audio output 
 Default Sound Playback: Yes 
 Default Voice Playback: Yes 
            Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0662&SUBSYS_10438290&REV_1001 
        Manufacturer ID: 1 
             Product ID: 100 
                   Type: WDM 
            Driver Name: RtkHDAud.sys 
         Driver Version: 5.10.0000.5397 (English) 
      Driver Attributes: Final Retail 
            WHQL Logo'd: Yes 
          Date and Size: 4/10/2007 18:04:40, 4397568 bytes 
            Other Files:  
        Driver Provider: Realtek Semiconductor Corp. 
         HW Accel Level: Full 
              Cap Flags: 0xF5F 
    Min/Max Sample Rate: 8000, 192000 
Static/Strm HW Mix Bufs: 33, 32 
 Static/Strm HW 3D Bufs: 33, 32 
              HW Memory: 0 
       Voice Management: No 
 EAX(tm) 2.0 Listen/Src: Yes, Yes 
   I3DL2(tm) Listen/Src: Yes, Yes 
Sensaura(tm) ZoomFX(tm): No 
               Registry: OK 
      Sound Test Result: Not run 
 
--------------------- 
Sound Capture Devices 
--------------------- 
            Description: Realtek HD Audio Input 
  Default Sound Capture: Yes 
  Default Voice Capture: Yes 
            Driver Name: RtkHDAud.sys 
         Driver Version: 5.10.0000.5397 (English) 
      Driver Attributes: Final Retail 
          Date and Size: 4/10/2007 18:04:40, 4397568 bytes 
              Cap Flags: 0x41 
           Format Flags: 0xFFF 
 
----------- 
DirectMusic 
----------- 
        DLS Path: C:\WINDOWS\SYSTEM32\drivers\GM.DLS 
     DLS Version: 1.00.0016.0002 
    Acceleration: n/a 
           Ports: Microsoft Synthesizer, Software (Not Kernel Mode), Output, DLS, Internal, Default Port 
                  Mapeador MIDI da Microsoft [Emulado], Hardware (Not Kernel Mode), Output, No DLS, Internal 
                  Sintetizador por software GS Wa [Emulado], Hardware (Not Kernel Mode), Output, No DLS, Internal 
        Registry: OK 
     Test Result: Not run 
 
------------------- 
DirectInput Devices 
------------------- 
      Device Name: Rato 
         Attached: 1 
    Controller ID: n/a 
Vendor/Product ID: n/a 
        FF Driver: n/a 
 
      Device Name: Teclado 
         Attached: 1 
    Controller ID: n/a 
Vendor/Product ID: n/a 
        FF Driver: n/a 
 
      Device Name: Microsoft® Digital Media Keyboard 
         Attached: 1 
    Controller ID: 0x0 
Vendor/Product ID: 0x045E, 0x00B4 
        FF Driver: n/a 
 
      Device Name: Microsoft® Digital Media Keyboard 
         Attached: 1 
    Controller ID: 0x0 
Vendor/Product ID: 0x045E, 0x00B4 
        FF Driver: n/a 
 
Poll w/ Interrupt: No 
         Registry: OK 
 
----------- 
USB Devices 
----------- 
+ Concentrador raiz USB (usbport) 
| Vendor/Product ID: 0x8086, 0x27CB 
| Matching Device ID: usb\root_hub 
| Service: usbhub 
| Driver: usbhub.sys, 4/13/2008 23:15:38, 59520 bytes 
| Driver: usbd.sys, 11/20/2001 12:00:00, 4736 bytes 
 
---------------- 
Gameport Devices 
---------------- 
 
------------ 
PS/2 Devices 
------------ 
+ Dispositivo de teclado HID 
| Vendor/Product ID: 0x045E, 0x00B4 
| Matching Device ID: hid_device_system_keyboard 
| Service: kbdhid 
| Driver: kbdhid.sys, 4/14/2008 20:13:14, 14720 bytes 
| Driver: kbdclass.sys, 4/14/2008 20:13:12, 25344 bytes 
|  
+ Controlador do teclado do servidor de terminais 
| Matching Device ID: root\rdp_kbd 
| Upper Filters: kbdclass 
| Service: TermDD 
| Driver: termdd.sys, 4/14/2008 20:40:32, 40840 bytes 
| Driver: kbdclass.sys, 4/14/2008 20:13:12, 25344 bytes 
|  
+ Microsoft USB Wheel Mouse Optical 
| Vendor/Product ID: 0x045E, 0x0040 
| Matching Device ID: hid\vid_045e&pid_0040 
| Service: mouhid 
| Driver: mouclass.sys, 4/14/2008 20:04:08, 23808 bytes 
| Driver: mouhid.sys, 11/20/2001 12:00:00, 12160 bytes 
|  
+ Controlador de rato do servidor de terminais 
| Matching Device ID: root\rdp_mou 
| Upper Filters: mouclass 
| Service: TermDD 
| Driver: termdd.sys, 4/14/2008 20:40:32, 40840 bytes 
| Driver: mouclass.sys, 4/14/2008 20:04:08, 23808 bytes 
 
---------------------------- 
DirectPlay Service Providers 
---------------------------- 
DirectPlay8 Modem Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.5512) 
DirectPlay8 Serial Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.5512) 
DirectPlay8 IPX Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.5512) 
DirectPlay8 TCP/IP Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.5512) 
Internet TCP/IP Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.5512) 
IPX Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.5512) 
Modem Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.5512) 
Serial Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.5512) 
 
DirectPlay Voice Wizard Tests: Full Duplex: Not run, Half Duplex: Not run, Mic: Not run 
DirectPlay Test Result: Not run 
Registry: OK 
 
------------------- 
DirectPlay Adapters 
------------------- 
DirectPlay8 Serial Service Provider: COM1 
DirectPlay8 TCP/IP Service Provider: Hamachi - IPv4 -  
 
----------------------- 
DirectPlay Voice Codecs 
----------------------- 
Voxware VR12 1.4kbit/s 
Voxware SC06 6.4kbit/s 
Voxware SC03 3.2kbit/s 
MS-PCM 64 kbit/s 
MS-ADPCM 32.8 kbit/s 
Microsoft GSM 6.10 13 kbit/s 
TrueSpeech(TM) 8.6 kbit/s 
 
------------------------- 
DirectPlay Lobbyable Apps 
------------------------- 
Age of Empires (DX7) - Registry: OK, ExeFile: Empires.Exe (0.09.0013.1115) 
Age of Empires Expansion (DX7) - Registry: OK, ExeFile: EmpiresX.Exe (0.01.0006.1115) 
Re-Volt (DX7) - Registry: OK, ExeFile: revolt.exe () 
Total Annihilation (DX7) - Registry: OK, ExeFile: TOTALA.EXE (3.00.0000.0001) 
 
------------------------ 
Disk & DVD/CD-ROM Drives 
------------------------ 
      Drive: C: 
 Free Space: 7.5 GB 
Total Space: 238.5 GB 
File System: NTFS 
      Model: WDC WD2500AAJS-22VWA0 
 
      Drive: D: 
      Model: ASUS DRW-2014L1T 
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.5512 (Portuguese), 4/13/2008 23:10:48, 62976 bytes 
 
      Drive: G: 
      Model: HGJI 1QBK9A3K1QJ SCSI CdRom Device 
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.5512 (Portuguese), 4/13/2008 23:10:48, 62976 bytes 
 
      Drive: F: 
      Model: MagicISO Virtual DVD-ROM0000 
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.5512 (Portuguese), 4/13/2008 23:10:48, 62976 bytes 
 
-------------- 
System Devices 
-------------- 
     Name: Controlador Dual Channel PCI IDE padrão 
Device ID: PCI\VEN_8086&DEV_27DF&SUBSYS_81791043&REV_01\3&11583659&0&F9 
   Driver: C:\WINDOWS\system32\DRIVERS\pciidex.sys, 5.01.2600.5512 (Portuguese), 4/13/2008 23:10:30, 24960 bytes 
   Driver: C:\WINDOWS\system32\DRIVERS\atapi.sys, 5.01.2600.5512 (English), 4/13/2008 23:10:32, 96512 bytes 
   Driver: C:\WINDOWS\system32\DRIVERS\pciide.sys, 5.01.2600.0000 (Portuguese), 11/20/2001 12:00:00, 3456 bytes 
 
     Name: Intel(R) 82801G (ICH7 Family) SMBus Controller - 27DA 
Device ID: PCI\VEN_8086&DEV_27DA&SUBSYS_81791043&REV_01\3&11583659&0&FB 
   Driver: n/a 
 
     Name: Controlador de Barramento UAA da Microsoft para High Definition Audio 
Device ID: PCI\VEN_8086&DEV_27D8&SUBSYS_82901043&REV_01\3&11583659&0&D8 
   Driver: C:\WINDOWS\system32\DRIVERS\hdaudbus.sys, 5.10.0001.5013 (English), 4/13/2008 21:06:06, 144384 bytes 
 
     Name: Bridge PCI padrão PCI-para-PCI 
Device ID: PCI\VEN_8086&DEV_27D2&SUBSYS_00000000&REV_01\3&11583659&0&E1 
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (Portuguese), 4/14/2008 20:17:56, 68992 bytes 
 
     Name: Bridge PCI padrão PCI-para-PCI 
Device ID: PCI\VEN_8086&DEV_27D0&SUBSYS_00000000&REV_01\3&11583659&0&E0 
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (Portuguese), 4/14/2008 20:17:56, 68992 bytes 
 
     Name: Controlador anfitrião padrão avançado PCI para USB 
Device ID: PCI\VEN_8086&DEV_27CC&SUBSYS_81791043&REV_01\3&11583659&0&EF 
   Driver: C:\WINDOWS\system32\drivers\usbehci.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:36, 30208 bytes 
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:38, 143872 bytes 
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (Portuguese), 4/14/2008 20:39:32, 77312 bytes 
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:38, 59520 bytes 
   Driver: C:\WINDOWS\system32\hccoin.dll, 5.01.2600.5512 (English), 4/14/2008 20:39:12, 7168 bytes 
 
     Name: Controlador de sistema anfitrião universal PCI de USB padrão 
Device ID: PCI\VEN_8086&DEV_27CB&SUBSYS_81791043&REV_01\3&11583659&0&EB 
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:36, 20608 bytes 
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:38, 143872 bytes 
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (Portuguese), 4/14/2008 20:39:32, 77312 bytes 
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:38, 59520 bytes 
 
     Name: Controlador de sistema anfitrião universal PCI de USB padrão 
Device ID: PCI\VEN_8086&DEV_27CA&SUBSYS_81791043&REV_01\3&11583659&0&EA 
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:36, 20608 bytes 
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:38, 143872 bytes 
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (Portuguese), 4/14/2008 20:39:32, 77312 bytes 
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:38, 59520 bytes 
 
     Name: Controlador de sistema anfitrião universal PCI de USB padrão 
Device ID: PCI\VEN_8086&DEV_27C9&SUBSYS_81791043&REV_01\3&11583659&0&E9 
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:36, 20608 bytes 
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:38, 143872 bytes 
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (Portuguese), 4/14/2008 20:39:32, 77312 bytes 
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:38, 59520 bytes 
 
     Name: Controlador de sistema anfitrião universal PCI de USB padrão 
Device ID: PCI\VEN_8086&DEV_27C8&SUBSYS_81791043&REV_01\3&11583659&0&E8 
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:36, 20608 bytes 
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:38, 143872 bytes 
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (Portuguese), 4/14/2008 20:39:32, 77312 bytes 
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English), 4/13/2008 23:15:38, 59520 bytes 
 
     Name: Controlador Dual Channel PCI IDE padrão 
Device ID: PCI\VEN_8086&DEV_27C0&SUBSYS_26011043&REV_01\3&11583659&0&FA 
   Driver: C:\WINDOWS\system32\DRIVERS\pciidex.sys, 5.01.2600.5512 (Portuguese), 4/13/2008 23:10:30, 24960 bytes 
   Driver: C:\WINDOWS\system32\DRIVERS\atapi.sys, 5.01.2600.5512 (English), 4/13/2008 23:10:32, 96512 bytes 
   Driver: C:\WINDOWS\system32\DRIVERS\pciide.sys, 5.01.2600.0000 (Portuguese), 11/20/2001 12:00:00, 3456 bytes 
 
     Name: Bridge PCI ISA padrão 
Device ID: PCI\VEN_8086&DEV_27B8&SUBSYS_00000000&REV_01\3&11583659&0&F8 
   Driver: C:\WINDOWS\system32\DRIVERS\isapnp.sys, 5.01.2600.5512 (Portuguese), 4/14/2008 20:12:42, 37760 bytes 
 
     Name: Bridge PCI padrão PCI-para-PCI 
Device ID: PCI\VEN_8086&DEV_2771&SUBSYS_00000000&REV_02\3&11583659&0&08 
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (Portuguese), 4/14/2008 20:17:56, 68992 bytes 
 
     Name: Bridge de CPU de sistemas PCI padrão 
Device ID: PCI\VEN_8086&DEV_2770&SUBSYS_00000000&REV_02\3&11583659&0&00 
   Driver: n/a 
 
     Name: Intel(R) 82801 PCI Bridge - 244E 
Device ID: PCI\VEN_8086&DEV_244E&SUBSYS_00000000&REV_E1\3&11583659&0&F0 
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (Portuguese), 4/14/2008 20:17:56, 68992 bytes 
 
     Name: Atheros L2 Fast Ethernet 10/100 Base-T Controller 
Device ID: PCI\VEN_1969&DEV_2048&SUBSYS_82331043&REV_A0\4&38D2602C&0&00E1 
   Driver: C:\WINDOWS\system32\DRIVERS\l251x86.sys, 2.05.6000.0000 (English), 7/3/2007 10:33:26, 29696 bytes 
 
     Name: Controlador de rede 
Device ID: PCI\VEN_1814&DEV_0302&SUBSYS_B8341462&REV_00\4&CF81C54&0&00F0 
   Driver: n/a 
 
     Name: NVIDIA GeForce 8500 GT 
Device ID: PCI\VEN_10DE&DEV_0421&SUBSYS_82451043&REV_A1\4&24AE49A5&0&0008 
   Driver: c:\nvidia\displaydriver\190.62\english\NvCplSetupEng.exe, 14.00.0000.0162 (English), 8/16/2009 23:57:00, 19458880 bytes 
   Driver: C:\WINDOWS\system32\DRIVERS\nv4_mini.sys, 6.14.0011.9062 (English), 8/16/2009 23:57:00, 7729568 bytes 
   Driver: C:\WINDOWS\system32\nv4_disp.dll, 6.14.0011.9062 (English), 8/16/2009 23:57:00, 5845760 bytes 
   Driver: C:\WINDOWS\system32\nvapi.dll, 6.14.0011.9062 (English), 8/16/2009 23:57:00, 868352 bytes 
   Driver: C:\WINDOWS\system32\nvcuda.dll, 6.14.0011.9062 (English), 8/16/2009 23:57:00, 2002944 bytes 
   Driver: C:\WINDOWS\system32\nvcuvenc.dll, 6.14.0011.9062 (English), 8/16/2009 23:57:00, 1706528 bytes 
   Driver: C:\WINDOWS\system32\nvcuvid.dll, 6.14.0011.9062 (English), 8/16/2009 23:57:00, 2189856 bytes 
   Driver: C:\WINDOWS\system32\nvdata.bin, 8/16/2009 23:57:00, 1597690 bytes 
   Driver: C:\WINDOWS\system32\nvoglnt.dll, 6.14.0011.9062 (English), 8/16/2009 23:57:00, 10457088 bytes 
   Driver: C:\WINDOWS\system32\nvcod.dll, 1.06.0002.0057 (English), 8/16/2009 23:57:00, 155648 bytes 
   Driver: C:\WINDOWS\system32\nvcodins.dll, 1.06.0002.0057 (English), 8/16/2009 23:57:00, 155648 bytes 
 
------------------ 
DirectX Components 
------------------ 
   ddraw.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 279552 bytes 
 ddrawex.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 27136 bytes 
   dxapi.sys: 5.01.2600.0000 English Final Retail 11/20/2001 12:00:00 10496 bytes 
    d3d8.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 1179648 bytes 
 d3d8thk.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 8192 bytes 
    d3d9.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 1689088 bytes 
   d3dim.dll: 5.01.2600.0000 English Final Retail 11/20/2001 12:00:00 436224 bytes 
d3dim700.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 824320 bytes 
 d3dramp.dll: 5.01.2600.0000 English Final Retail 11/20/2001 12:00:00 590336 bytes 
   d3drm.dll: 5.01.2600.0000 English Final Retail 11/20/2001 12:00:00 350208 bytes 
  d3dxof.dll: 5.01.2600.0000 English Final Retail 11/20/2001 12:00:00 47616 bytes 
d3dpmesh.dll: 5.01.2600.0000 English Final Retail 11/20/2001 12:00:00 34816 bytes 
   dplay.dll: 5.00.2134.0001 Portuguese Final Retail 11/20/2001 12:00:00 33040 bytes 
  dplayx.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 229888 bytes 
dpmodemx.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 24064 bytes 
 dpwsock.dll: 5.00.2134.0001 English Final Retail 11/20/2001 12:00:00 42768 bytes 
dpwsockx.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 57856 bytes 
dplaysvr.exe: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:46 29696 bytes 
  dpnsvr.exe: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:46 18432 bytes 
   dpnet.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 375296 bytes 
dpnlobby.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:37:12 3072 bytes 
 dpnaddr.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:37:12 3072 bytes 
 dpvoice.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 213504 bytes 
dpvsetup.exe: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:46 83456 bytes 
  dpvvox.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 116736 bytes 
  dpvacm.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 21504 bytes 
dpnhpast.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 35328 bytes 
dpnhupnp.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 60928 bytes 
dpserial.dll: 5.00.2134.0001 Portuguese Final Retail 11/20/2001 12:00:00 54032 bytes 
  dinput.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 166912 bytes 
 dinput8.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 189952 bytes 
   dimap.dll: 5.01.2600.0000 English Final Retail 11/20/2001 12:00:00 44032 bytes 
diactfrm.dll: 5.01.2600.0000 Portuguese Final Retail 11/20/2001 12:00:00 394752 bytes 
     joy.cpl: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:40:12 69632 bytes 
   gcdef.dll: 5.01.2600.0000 Portuguese Final Retail 11/20/2001 12:00:00 77312 bytes 
     pid.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:24 35328 bytes 
  dsound.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 367616 bytes 
dsound3d.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 1293824 bytes 
  dswave.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 19456 bytes 
   dsdmo.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 181248 bytes 
dsdmoprp.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 72192 bytes 
  dmusic.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 104448 bytes 
  dmband.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 28672 bytes 
dmcompos.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 61440 bytes 
   dmime.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 181248 bytes 
dmloader.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 35840 bytes 
 dmstyle.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 105984 bytes 
 dmsynth.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 103424 bytes 
dmscript.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 82432 bytes 
   dx7vb.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 619008 bytes 
   dx8vb.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 1227264 bytes 
 dxdiagn.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 2113536 bytes 
   mfc40.dll: 4.01.0000.6140 English Final Retail 11/20/2001 12:00:00 924432 bytes 
   mfc42.dll: 6.02.4131.0000 English Final Retail 4/14/2008 20:39:14 1028096 bytes 
 wsock32.dll: 5.01.2600.5512 Portuguese Final Retail 4/14/2008 20:39:36 25600 bytes 
amstream.dll: 6.05.2600.5512 English Final Retail 4/14/2008 20:39:08 70656 bytes 
 devenum.dll: 6.05.2600.5512 Portuguese Final Retail 4/14/2008 20:39:10 59904 bytes 
  dxmasf.dll: 6.04.0009.1133 Portuguese Final Retail 4/14/2008 20:39:10 499766 bytes 
mciqtz32.dll: 6.05.2600.5512 Portuguese Final Retail 4/14/2008 20:39:14 35328 bytes 
 mpg2splt.ax: 6.05.2600.5512 English Final Retail 4/14/2008 20:40:12 148992 bytes 
   msdmo.dll: 6.05.2600.5512 English Final Retail 4/14/2008 20:39:16 14336 bytes 
  encapi.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:10 20480 bytes 
    qasf.dll: 11.00.5721.5145 English Final Retail 10/18/2006 20:47:18 211456 bytes 
    qcap.dll: 6.05.2600.5512 Portuguese Final Retail 4/14/2008 20:39:24 192512 bytes 
     qdv.dll: 6.05.2600.5512 Portuguese Final Retail 4/14/2008 20:39:24 279040 bytes 
    qdvd.dll: 6.05.2600.5512 Portuguese Final Retail 4/14/2008 20:39:24 387072 bytes 
   qedit.dll: 6.05.2600.5512 Portuguese Final Retail 4/14/2008 20:39:24 563200 bytes 
qedwipes.dll: 6.05.2600.5512 English Final Retail 4/13/2008 21:51:34 733696 bytes 
  quartz.dll: 6.05.2600.5822 Portuguese Final Retail 6/3/2009 19:10:28 1297920 bytes 
 strmdll.dll: 4.01.0000.3938 Portuguese Final Retail 8/26/2009 08:01:17 247326 bytes 
 iac25_32.ax: 2.00.0005.0053 English Final Retail 4/14/2008 20:40:12 199680 bytes 
  ir41_32.ax: 4.51.0016.0003 English Final Retail 4/14/2008 20:40:12 848384 bytes 
 ir41_qc.dll: 4.30.0062.0002 English Final Retail 4/14/2008 20:39:12 120320 bytes 
ir41_qcx.dll: 4.30.0064.0001 English Final Retail 4/14/2008 20:39:12 338432 bytes 
 ir50_32.dll: 5.2562.0015.0055 English Final Retail 4/14/2008 20:39:12 755200 bytes 
 ir50_qc.dll: 5.00.0063.0048 English Final Retail 4/14/2008 20:39:12 200192 bytes 
ir50_qcx.dll: 5.00.0064.0048 English Final Retail 4/14/2008 20:39:12 183808 bytes 
   ivfsrc.ax: 5.10.0002.0051 English Final Retail 4/14/2008 20:40:12 154624 bytes 
mswebdvd.dll: 6.05.2600.5857 Portuguese Final Retail 8/5/2009 09:00:10 205824 bytes 
      ks.sys: 5.03.2600.5512 Portuguese Final Retail 4/13/2008 23:46:38 141056 bytes 
  ksproxy.ax: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:40:12 129536 bytes 
  ksuser.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:14 4096 bytes 
  stream.sys: 5.03.2600.5512 Portuguese Final Retail 4/13/2008 23:15:16 49408 bytes 
mspclock.sys: 5.03.2600.5512 Portuguese Final Retail 4/13/2008 23:09:52 5376 bytes 
   mspqm.sys: 5.01.2600.5512 Portuguese Final Retail 4/13/2008 23:09:52 4992 bytes 
 mskssrv.sys: 5.03.2600.5512 Portuguese Final Retail 4/13/2008 23:09:54 7552 bytes 
  swenum.sys: 5.03.2600.5512 Portuguese Final Retail 4/13/2008 23:09:54 4352 bytes 
   mstee.sys: 5.03.2600.5512 Portuguese Final Retail 4/13/2008 23:09:52 5504 bytes 
   ipsink.ax: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:40:12 16384 bytes 
mpeg2data.ax: 6.05.2600.5512 English Final Retail 4/14/2008 20:40:12 118272 bytes 
  ndisip.sys: 5.03.2600.5512 English Final Retail 4/13/2008 23:16:24 10880 bytes 
streamip.sys: 5.03.2600.5512 English Final Retail 4/13/2008 23:16:22 15232 bytes 
msvidctl.dll: 6.05.2600.5512 Portuguese Final Retail 4/14/2008 20:39:18 1435136 bytes 
    slip.sys: 5.03.2600.5512 English Final Retail 4/13/2008 23:16:24 11136 bytes 
nabtsfec.sys: 5.03.2600.5512 English Final Retail 4/13/2008 23:16:26 85248 bytes 
ccdecode.sys: 5.03.2600.5512 English Final Retail 4/13/2008 23:16:24 17024 bytes 
  vbisurf.ax: 5.03.2600.5512 English Final Retail 4/14/2008 20:40:12 30208 bytes 
   msyuv.dll: 5.03.2600.5512 English Final Retail 4/14/2008 20:39:18 16896 bytes 
 kstvtune.ax: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:40:12 61952 bytes 
   ksxbar.ax: 5.03.2600.5512 English Final Retail 4/14/2008 20:40:12 43008 bytes 
 kswdmcap.ax: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:40:12 92160 bytes 
vfwwdm32.dll: 5.01.2600.5512 Portuguese Final Retail 4/14/2008 20:39:32 54784 bytes 
wstcodec.sys: 5.03.2600.5512 English Final Retail 4/13/2008 23:16:26 19200 bytes 
wstdecod.dll: 5.03.2600.5512 Portuguese Final Retail 4/14/2008 20:39:36 51200 bytes 
 
------------------ 
DirectShow Filters 
------------------ 
 
Codecs VBI de fluxo WDM: 
NABTS/FEC VBI Codec,0x00200000,2,1,,5.03.2600.5512 
Descodificador CC,0x00200000,2,1,,5.03.2600.5512 
WST Codec,0x00200000,1,1,,5.03.2600.5512 
 
DirectShow Filters: 
WMAudio Decoder DMO,0x00800800,1,1,, 
WMAPro over S/PDIF DMO,0x00600800,1,1,, 
WMA Voice Decoder DMO,0x00600800,1,1,, 
WMVideo Advanced Decoder DMO,0x00800001,1,1,, 
Mpeg4s Decoder DMO,0x00800001,1,1,, 
WMV Screen decoder DMO,0x00800001,1,1,, 
WMVideo Decoder DMO,0x00800001,1,1,, 
Mpeg43 Decoder DMO,0x00800001,1,1,, 
Mpeg4 Decoder DMO,0x00800001,1,1,, 
DivX Decoder Filter,0x00800000,1,1,divxdec.ax,5.00.0005.0830 
Subtitle Mixer,0x0080000a,2,1,, 
WMT MuxDeMux Filter,0x00200000,0,0,wmm2filt.dll,2.01.4026.0000 
ffdshow Video Decoder,0xff800001,2,1,ffdshow.ax,1.00.0005.2488 
Full Screen Renderer,0x00200000,1,0,quartz.dll,6.05.2600.5822 
CoreVorbis Audio Decoder,0x00800000,1,1,CoreVorbis.ax,1.01.0000.0079 
ffdshow raw video filter,0x00200000,2,1,ffdshow.ax,1.00.0005.2488 
RealPlayer Video Filter,0x00200000,1,1,rdsf3260.dll,6.00.0013.0068 
Nero Scene Detector 2,0x00200000,2,0,NeSceneDetector.ax,3.02.0000.0020 
ffdshow Audio Decoder,0x3fffffff,1,1,ffdshow.ax,1.00.0005.2488 
DV Muxer,0x00400000,0,0,qdv.dll,6.05.2600.5512 
MPC - Mpeg Source (Gabest),0x00200000,0,0,MpegSplitter.ax,1.02.0997.0000 
Nero Digital Audio Decoder,0x00600000,1,1,NeAudio.ax,3.02.0000.0020 
DV Scenes,0x00200000,1,1,NVDV.dll,3.00.0002.0000 
Color Space Converter,0x00400001,1,1,quartz.dll,6.05.2600.5822 
WM ASF Reader,0x00400000,0,0,qasf.dll,11.00.5721.5145 
AVI Splitter,0x00600000,1,1,quartz.dll,6.05.2600.5822 
WMT AudioAnalyzer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
VGA 16 Color Ditherer,0x00400000,1,1,quartz.dll,6.05.2600.5822 
Indeo® video 5.10 Compression Filter,0x00200000,1,1,ir50_32.dll,5.2562.0015.0055 
Windows Media Audio Decoder,0x00800001,1,1,msadds32.ax,8.00.0000.4487 
RealVideo Decoder,0x00400000,1,1,RealMediaSplitter.ax,1.00.0001.0000 
MONOGRAM AMR Splitter,0x00600000,1,1,mmamr.ax,1.00.0001.0000 
AC3 Parser Filter,0x00600000,1,1,mpg2splt.ax,6.05.2600.5512 
WMT Format Conversion,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
StreamBufferSink,0x00200000,0,0,sbe.dll,6.05.2600.5512 
WMT Black Frame Generator,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
Nero Resize,0x00200000,1,1,NeResize.ax,3.02.0000.0020 
MJPEG Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.5822 
Indeo® video 5.10 Decompression Filter,0x00640000,1,1,ir50_32.dll,5.2562.0015.0055 
DivX for Blizzard Decoder Filter,0x00800000,1,1,blizzard.ax,5.00.0002.0000 
WMT Screen Capture filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000 
Microsoft Screen Video Decompressor,0x00800000,1,1,msscds32.ax,8.00.0000.4487 
MPEG-1 Stream Splitter,0x00600000,1,2,quartz.dll,6.05.2600.5822 
SAMI (CC) Parser,0x00400000,1,1,quartz.dll,6.05.2600.5822 
Dump,0x00200000,1,0,dump.ax,8.01.0000.0000 
CyberLink Video/SP Decoder (PDVD8),0x00800001,2,3,CLVSD.ax,8.02.0000.1211 
MPEG Layer-3 Decoder,0x00810000,1,1,l3codecx.ax,1.05.0000.0050 
Nero Audio Stream Renderer,0x00200000,1,0,NeRender.ax,3.02.0000.0020 
MPEG-2 Splitter,0x005fffff,1,0,mpg2splt.ax,6.05.2600.5512 
MP4 Source,0x00600000,0,0,MP4Splitter.ax,1.00.0000.0005 
ACELP.net Sipro Lab Audio Decoder,0x00800001,1,1,acelpdec.ax,1.04.0000.0000 
Nero Digital AVC Audio Encoder,0x00200000,1,2,NeNDAud.ax,3.02.0000.0020 
Nero Digital AVC File Writer,0x00200000,1,0,NeNDMux.ax,3.02.0000.0020 
Nero Digital AVC Null Renderer,0x00200000,1,0,NeNDMux.ax,3.02.0000.0020 
Nero Digital AVC Muxer,0x00200000,2,1,NeNDMux.ax,3.02.0000.0020 
Nero Digital AVC Video Enc,0x00200000,1,2,, 
ZJSoft Avi Splitter,0x00200000,1,1,AviSplitter.ax,1.00.0000.0004 
ZJSoft Avi Source,0x00200000,0,0,AviSplitter.ax,1.00.0000.0004 
ZJSoft Matroska Splitter,0x00200000,1,1,MatroskaSplitter.ax,1.00.0002.0006 
ZJSoft Matroska Source,0x00200000,0,0,MatroskaSplitter.ax,1.00.0002.0006 
ZJSoft Ogg Splitter,0x00200000,1,1,OggSplitter.ax,1.00.0000.0000 
ZJSoft Ogg Source,0x00200000,0,0,OggSplitter.ax,1.00.0000.0000 
ZJSoft RealMedia Splitter,0x00200000,1,1,RealMediaSplitter.ax,1.00.0001.0000 
ZJSoft RealMedia Source,0x00200000,0,0,RealMediaSplitter.ax,1.00.0001.0000 
ZJSoft RealVideo Decoder,0x00200000,1,1,RealMediaSplitter.ax,1.00.0001.0000 
ZJSoft RealAudio Decoder,0x00200000,1,1,RealMediaSplitter.ax,1.00.0001.0000 
Nero QuickTime(tm) Video Decoder,0x00400000,1,1,NeQTDec.ax,3.02.0000.0020 
FLV Splitter,0x00800001,1,1,FLVSplitter.ax,1.00.0000.0005 
Internal Script Command Renderer,0x00800001,1,0,quartz.dll,6.05.2600.5822 
AVS Video Out,0x00200000,0,1,AVSVideoOutFilter3.ax,1.00.0000.0225 
MPEG Audio Decoder,0x03680001,1,1,quartz.dll,6.05.2600.5822 
_ VSO Preview Filter,0x00200000,0,1,VsoVprev.ax,3.00.0001.0043 
WavPack Audio Decoder,0x00600000,1,1,WavPackDSDecoder.ax,1.01.0000.0484 
File Source (Netshow URL),0x00400000,0,1,wmpasf.dll,9.00.0000.4503 
TC MPEG Encoder,0x00200000,2,2,TCMpegFilter.ax,1.00.0003.0002 
Nero Format Converter,0x00200000,1,1,NeroFormatConv.ax,3.02.0000.0020 
WMT Import Filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000 
DV Splitter,0x00600000,1,2,qdv.dll,6.05.2600.5512 
Bitmap Generate,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
Windows Media Video Decoder,0x00800000,1,1,wmvds32.ax,8.00.0000.4487 
MONOGRAM AMR Decoder,0x00600000,1,1,mmamr.ax,1.00.0001.0000 
Video Mixing Renderer 9,0x00200000,1,0,quartz.dll, 
Windows Media Video Decoder,0x00800000,1,1,wmv8ds32.ax,8.00.0000.4000 
Subtitle Parser,0x00600000,1,1,, 
Nero Photo Source,0x00200000,0,1,NePhotoSource.ax,3.02.0000.0020 
MONOGRAM Musepack Decoder,0x00600000,1,1,mmmpcdec.ax,0.09.0002.0000 
Haali Media Splitter,0x00800001,0,1,splitter.ax,1.09.0042.0001 
Haali Media Splitter (AR),0x00400000,1,1,splitter.ax,1.09.0042.0001 
WMT VIH2 Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
Nero Video Analyzer,0x00200000,2,0,NeVideoAnalyzer.ax,3.02.0000.0020 
Record Queue,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
Nero ES Video Reader,0x00600000,0,1,NDParser.ax,3.02.0000.0020 
HP VTK MPEG-1 Encoder,0x00200000,3,3,hpqvtk01.dll,90.00.0146.0000 
DV Source Filter,0x00400000,0,1,NVDV.dll,3.00.0002.0000 
MP4 Splitter,0x00600001,1,1,MP4Splitter.ax,1.00.0000.0005 
Nero Audio CD Filter,0x00200000,0,1,NeAudCD.ax,3.02.0000.0020 
Windows Media Multiplexer,0x00600000,1,1,wmpasf.dll,9.00.0000.4503 
ASX file Parser,0x00600000,1,1,wmpasf.dll,9.00.0000.4503 
ASX v.2 file Parser,0x00600000,1,0,wmpasf.dll,9.00.0000.4503 
NSC file Parser,0x00600000,1,1,wmpasf.dll,9.00.0000.4503 
File Source (Monkey Audio),0x00400000,0,1,MonkeySource.ax, 
Pixela DVdata,0x00200000,1,1,PxDVdata.ax,1.00.0000.0003 
ACM Wrapper,0x00600000,1,1,quartz.dll,6.05.2600.5822 
madFlac Decoder,0x00600000,1,1,madFlac.ax,1.08.0000.0000 
Windows Media source filter,0x00600000,0,2,wmpasf.dll,9.00.0000.4503 
Video Renderer,0x00800001,1,0,quartz.dll,6.05.2600.5822 
Frame Eater,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
Nero DVD Navigator,0x00600000,0,4,NeDVD.ax,3.02.0000.0020 
MPEG-2 Video Stream Analyzer,0x00200000,0,0,sbe.dll,6.05.2600.5512 
Line 21 Decoder,0x00600000,1,1,qdvd.dll,6.05.2600.5512 
Video Port Manager,0x00600000,2,1,quartz.dll,6.05.2600.5822 
WST Decoder,0x00600000,1,1,wstdecod.dll,5.03.2600.5512 
Video Renderer,0x00400000,1,0,quartz.dll,6.05.2600.5822 
Microsoft MPEG-4 Video Decompressor,0x00800000,1,1,mp4sds32.ax,8.00.0000.0344 
Haali Video Renderer,0x00200000,1,0,dxr.dll, 
RealMedia Source,0x00600000,0,0,RealMediaSplitter.ax,1.00.0001.0000 
Nero Audio Sample Renderer,0x00200000,1,0,NeRender.ax,3.02.0000.0020 
MPEG PS MULTIPLEXER PIXELA,0x00200000,2,1,PSMulPlx.ax,1.00.0000.0004 
Nero Vcd Navigator,0x00600000,0,2,NeVcd.ax,3.02.0000.0020 
DivX Decoder Filter,0x00800000,1,1,divxdec.ax,5.00.0005.0830 
DivXAntiFreeze,0x00800001,1,1,, 
Nero Audio Processor,0x00200000,1,1,NeAudioConv.ax,3.02.0000.0020 
HP VTK Rotate Filter,0x00200000,1,1,hpqvtk01.dll,90.00.0146.0000 
WM ASF Writer,0x00400000,0,0,qasf.dll,11.00.5721.5145 
FLV4 Video Decoder,0x00400000,1,1,FLVSplitter.ax,1.00.0000.0005 
WMT Sample Information Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
Nero Mpeg2 Encoder,0x00200000,2,1,NeVCR.ax,3.02.0000.0020 
Sony Wave Hammer Surround,0x00200000,1,1,mchammer.dll,1.00.0000.0224 
VBI Surface Allocator,0x00600000,1,1,vbisurf.ax,5.03.2600.5512 
Microsoft MPEG-4 Video Decompressor,0x00800000,1,1,mpg4ds32.ax,8.00.0000.4487 
Nero Video Stream Renderer,0x00200000,1,0,NeRender.ax,3.02.0000.0020 
File writer,0x00200000,1,0,qcap.dll,6.05.2600.5512 
Nero PS Muxer,0x00200000,1,1,NePSMuxer.ax,3.02.0000.0020 
Haali Simple Media Splitter,0x00200000,0,1,splitter.ax,1.09.0042.0001 
WMT Log Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
WMT Virtual Renderer,0x00200000,1,0,wmm2filt.dll,2.01.4026.0000 
DirectVobSub,0x00200000,2,1,vsfilter.dll,2.39.0005.0001 
RealAudio Decoder,0x00400000,1,1,RealMediaSplitter.ax,1.00.0001.0000 
DirectVobSub (auto-loading version),0x00800002,2,1,vsfilter.dll,2.39.0005.0001 
SC Subtitle Filter,0x00200000,1,1,SCSubtitleFilter.ax,0.00.0000.0000 
MONOGRAM AMR Encoder,0x00600000,1,1,mmamr.ax,1.00.0001.0000 
BSwitch Filter,0x00200000,1,1,BSwitch.ax,1.08.0004.0000 
DVD Navigator,0x00200000,0,2,qdvd.dll,6.05.2600.5512 
Overlay Mixer2,0x00400000,1,1,qdvd.dll,6.05.2600.5512 
Haali Matroska Muxer,0x00200000,1,0,splitter.ax,1.09.0042.0001 
Nero Splitter,0x00600000,1,3,NeSplitter.ax,3.02.0000.0020 
AVI Draw,0x00600064,9,1,quartz.dll,6.05.2600.5822 
.RAM file Parser,0x00600000,1,0,wmpasf.dll,9.00.0000.4503 
muvee Video Analyser,0x00200000,1,0,mvvanalyse.ax,4.00.0000.0004 
muvee Music Analyser,0x00200000,1,0,mvmanalyse.ax,4.00.0000.0004 
MONOGRAM AMR Mux,0x00600000,1,1,mmamr.ax,1.00.0001.0000 
Nero File Source / Splitter,0x00600000,0,3,NeFSource.ax,3.02.0000.0020 
DC-Bass Source,0x00400000,0,1,DCBassSource.ax,1.02.0000.0000 
BMPCapture,0x00200000,1,1,BMPCapture.ax, 
WMT DirectX Transform Wrapper,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
G.711 Codec,0x00200000,1,1,g711codc.ax,5.01.2600.0000 
MPEG-2 Demultiplexer,0x00600000,1,1,mpg2splt.ax,6.05.2600.5512 
DV Video Decoder,0x00800000,1,1,qdv.dll,6.05.2600.5512 
RealPlayer Transcode Filter,0x00600000,0,0,rdsf3260.dll,6.00.0013.0068 
Indeo® audio software,0x00500000,1,1,iac25_32.ax,2.00.0005.0053 
Windows Media Update Filter,0x00400000,1,0,wmpasf.dll,9.00.0000.4503 
ffdshow Audio Processor,0x00200000,1,1,ffdshow.ax,1.00.0005.2488 
ASF DIB Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.4503 
ASF ACM Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.4503 
ASF ICM Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.4503 
ASF URL Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.4503 
ASF JPEG Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.4503 
ASF DJPEG Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.4503 
ASF embedded stuff Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.4503 
9x8Resize,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
WIA Stream Snapshot Filter,0x00200000,1,1,wiasf.ax,1.00.0000.0000 
Nero Video Processor,0x00200000,1,1,NeroVideoProc.ax,3.02.0000.0020 
HP VTK Frame Grabber Filter,0x00200000,1,1,hpqvtk01.dll,90.00.0146.0000 
Nero Video Decoder,0x00600000,2,2,NeVideo.ax,3.02.0000.0020 
Allocator Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
SampleGrabber,0x00200000,1,1,qedit.dll,6.05.2600.5512 
Null Renderer,0x00200000,1,0,qedit.dll,6.05.2600.5512 
VP7 Decompressor,0x00800000,1,1,vp7dec.ax,7.00.0010.0000 
Aspect Ratio Resizer 16x9,0x00200000,1,1,AspectRatioConverter16x9.ax,4.00.0000.0004 
MONOGRAM Musepack Splitter,0x00600000,1,1,mmmpcdmx.ax,0.04.0000.0000 
WMT Virtual Source,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000 
madFlac Source,0x00600000,0,1,madFlac.ax,1.08.0000.0000 
MPEG-2 Sections and Tables,0x005fffff,1,0,mpeg2data.ax, 
WMT Interlacer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
Nero Audio CD Navigator,0x00200000,0,1,NeAudCD.ax,3.02.0000.0020 
FLV Source,0x00600001,0,0,FLVSplitter.ax,1.00.0000.0005 
StreamBufferSource,0x00200000,0,0,sbe.dll,6.05.2600.5512 
Pixela ReSizeBF,0x00200000,1,1,PxReSizeBF.ax,1.00.0000.0002 
Smart Tee,0x00200000,1,2,qcap.dll,6.05.2600.5512 
Overlay Mixer,0x00200000,0,0,qdvd.dll,6.05.2600.5512 
Nero Scene Detector,0x00200000,1,0,NeSceneDetector.ax,3.02.0000.0020 
RealPlayer Audio Filter,0x00200000,1,1,rdsf3260.dll,6.00.0013.0068 
AVI Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.5822 
Uncompressed Domain Shot Detection Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
AVI/WAV File Source,0x00400000,0,2,quartz.dll,6.05.2600.5822 
Morgan Stream Switcher,0x00800003,1,1,, 
MPEG4 Video Splitter,0x00600000,1,1,MP4Splitter.ax,1.00.0000.0005 
QuickTime Movie Parser,0x00600000,1,1,quartz.dll,6.05.2600.5822 
Wave Parser,0x00400000,1,1,quartz.dll,6.05.2600.5822 
MIDI Parser,0x00400000,1,1,quartz.dll,6.05.2600.5822 
Multi-file Parser,0x00400000,1,1,quartz.dll,6.05.2600.5822 
File stream renderer,0x00400000,1,1,quartz.dll,6.05.2600.5822 
XML Playlist,0x00400000,1,0,wmpasf.dll,9.00.0000.4503 
Nero File Source,0x00200000,0,1,NeFileSrc.ax,3.02.0000.0020 
Nero QuickTime(tm) Audio Decoder,0x00400000,1,1,NeQTDec.ax,3.02.0000.0020 
WavPack Audio Splitter,0x00600000,1,1,WavPackDSSplitter.ax,1.01.0000.0323 
HP VTK Resize Filter,0x00200000,1,1,hpqvtk01.dll,90.00.0146.0000 
Nero File Source (Async.),0x00400000,0,1,NeFileSourceAsync.ax,3.02.0000.0020 
ffdshow subtitles filter,0x00200000,2,1,ffdshow.ax,1.00.0005.2488 
MPC - Mpeg Splitter (Gabest),0x00400001,1,1,MpegSplitter.ax,1.02.0997.0000 
Nero DVD Decoder,0x00600000,2,2,NeVideo.ax,3.02.0000.0020 
Nero Digital Parser,0x00600000,0,3,NDParser.ax,3.02.0000.0020 
RealMedia Splitter,0x00600000,1,1,RealMediaSplitter.ax,1.00.0001.0000 
AVI Mux,0x00200000,1,0,qcap.dll,6.05.2600.5512 
MPEG4 Video Source,0x00600000,0,0,MP4Splitter.ax,1.00.0000.0005 
Subtitle Dest,0x00200000,1,1,, 
Line 21 Decoder 2,0x00600002,1,1,quartz.dll,6.05.2600.5822 
File Source (Async.),0x00400000,0,1,quartz.dll,6.05.2600.5822 
File Source (URL),0x00400000,0,1,quartz.dll,6.05.2600.5822 
WMT DV Extract,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
Nero Frame Capture,0x00200000,1,1,NeCapture.ax,3.02.0000.0020 
WMT Switch Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
WMT Volume,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
Nero Video Sample Renderer,0x00200000,1,0,NeRender.ax,3.02.0000.0020 
Haali Video Sink,0x00200000,1,0,splitter.ax,1.09.0042.0001 
Stretch Video,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000 
Aspect Ratio Resizer 4x3,0x00200000,1,1,AspectRatioConverter4x3.ax,4.00.0000.0004 
AC3File,0x00600000,0,1,ac3file.ax, 
Infinite Pin Tee Filter,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Nero DV Splitter,0x00200000,1,2,NeDVSplitter.ax,3.02.0000.0020 
QT Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.5822 
Pixela ReSize,0x00200000,1,1,PxReSize.ax,1.00.0000.0001 
MPEG Video Decoder,0x40000001,1,1,quartz.dll,6.05.2600.5822 
Sony ExpressFX Chorus,0x00200000,1,1,sfxpfx2.dll,1.00.0000.0527 
Sony ExpressFX Delay,0x00200000,1,1,sfxpfx2.dll,1.00.0000.0527 
Sony ExpressFX Distortion,0x00200000,1,1,sfxpfx1.dll,1.00.0000.0527 
Sony ExpressFX Equalization,0x00200000,1,1,sfxpfx2.dll,1.00.0000.0527 
Sony ExpressFX Flange/Wah-Wah,0x00200000,1,1,sfxpfx1.dll,1.00.0000.0527 
Sony ExpressFX Amplitude Modulation,0x00200000,1,1,sfxpfx2.dll,1.00.0000.0527 
Sony ExpressFX Reverb,0x00200000,1,1,sfxpfx1.dll,1.00.0000.0527 
Sony ExpressFX Stutter,0x00200000,1,1,sfxpfx1.dll,1.00.0000.0527 
Sony ExpressFX Dynamics,0x00200000,1,1,sfxpfx3.dll,1.00.0000.0166 
Sony ExpressFX Graphic EQ,0x00200000,1,1,sfxpfx3.dll,1.00.0000.0166 
Sony ExpressFX Noise Gate,0x00200000,1,1,sfxpfx3.dll,1.00.0000.0166 
Sony ExpressFX Time Stretch,0x00200000,1,1,sfxpfx3.dll,1.00.0000.0166 
Sony ExpressFX Audio Restoration,0x00200000,1,1,xpvinyl.dll,1.00.0000.0987 
Sony Multi-Band Dynamics,0x00200000,1,1,sfppack2.dll,1.00.0000.0585 
IL FL Studio DXi,0x00200000,1,1,FL Studio DXi.dll,1.00.0012.0000 
{2206C458-1E6B-4D65-B0F7-A74EEE8496B6},0x00800000,1,0,, 
Sony Track Compressor,0x00200000,1,1,sftrkfx1.dll,1.00.0000.0511 
Sony Dither,0x00200000,1,1,sftrkfx1.dll,1.00.0000.0511 
Sony Chorus,0x00200000,1,1,sfppack1.dll,1.00.0000.0590 
Indeo® video 4.4 Decompression Filter,0x00640000,1,1,ir41_32.ax,4.51.0016.0003 
Sony Distortion,0x00200000,1,1,sfppack3.dll,1.00.0000.0604 
Sony Gapper/Snipper,0x00200000,1,1,sfppack3.dll,1.00.0000.0604 
IL Multi FL Studio DXi,0x00200000,1,1,FL Studio DXi (Multi).dll,1.00.0012.0000 
Sony Simple Delay,0x00200000,1,1,sfppack1.dll,1.00.0000.0590 
Sony Reverb,0x00200000,1,1,sfppack1.dll,1.00.0000.0590 
{61D528DA-7582-4336-9E9B-092D7C127F5C},0x00800000,1,0,, 
Sony Multi-Tap Delay,0x00200000,1,1,sfppack1.dll,1.00.0000.0590 
Sony Track Noise Gate,0x00200000,1,1,sftrkfx1.dll,1.00.0000.0511 
Sony Graphic EQ,0x00200000,1,1,sfppack2.dll,1.00.0000.0585 
Sony Track EQ,0x00200000,1,1,sftrkfx1.dll,1.00.0000.0511 
Sony Smooth/Enhance,0x00200000,1,1,sfppack3.dll,1.00.0000.0604 
Indeo® video 4.4 Compression Filter,0x00200000,1,1,ir41_32.ax,4.51.0016.0003 
Sony Resonant Filter,0x00200000,1,1,sfresfilter.dll,1.00.0000.0298 
Sony Parametric EQ,0x00200000,1,1,sfppack2.dll,1.00.0000.0585 
Sony Time Stretch,0x00200000,1,1,sfppack1.dll,1.00.0000.0590 
Sony Noise Gate,0x00200000,1,1,sfppack2.dll,1.00.0000.0585 
Sony Paragraphic EQ,0x00200000,1,1,sfppack2.dll,1.00.0000.0585 
Sony Vibrato,0x00200000,1,1,sfppack3.dll,1.00.0000.0604 
Sony Pan,0x00200000,1,1,sffrgpnv.dll,1.00.0000.0237 
Sony Pitch Shift,0x00200000,1,1,sfppack1.dll,1.00.0000.0590 
Sony Volume,0x00200000,1,1,sffrgpnv.dll,1.00.0000.0237 
Sony Flange/Wah-wah,0x00200000,1,1,sfppack3.dll,1.00.0000.0604 
Sony Graphic Dynamics,0x00200000,1,1,sfppack2.dll,1.00.0000.0585 
Sony Amplitude Modulation,0x00200000,1,1,sfppack3.dll,1.00.0000.0604 
 
Dispositivos de bifurcação/T de sequência WDM: 
Conversor Tee/Sink-to-Sink,0x00200000,1,1,,5.03.2600.5512 
 
Transformação de dados de fluxo WDM: 
Microsoft Kernel Acoustic Echo Canceller,0x00000000,0,0,, 
Microsoft - sintetizador Kernel GS Wavetable,0x00200000,1,1,,5.03.2600.5512 
Sintetizador Microsoft Kernel DLS,0x00200000,1,1,,5.03.2600.5512 
Microsoft Kernel DRM Descrambler Filter,0x00200000,1,1,,5.03.2600.5512 
 
Video Compressors: 
WMVideo Encoder DMO,0x00600800,1,1,, 
WMVideo8 Encoder DMO,0x00600800,1,1,, 
MSScreen encoder DMO,0x00600800,1,1,, 
WMVideo8 Encoder DMO,0x00600800,1,1,, 
WMVideo9 Encoder DMO,0x00600800,1,1,, 
MSScreen 9 encoder DMO,0x00600800,1,1,, 
DV Video Encoder,0x00200000,0,0,qdv.dll,6.05.2600.5512 
ffdshow video encoder,0x00100000,1,1,ffdshow.ax,1.00.0005.2488 
Indeo® video 5.10 Compression Filter,0x00100000,1,1,ir50_32.dll,5.2562.0015.0055 
MJPEG Compressor,0x00200000,0,0,quartz.dll,6.05.2600.5822 
Nero Digital AVC Video Enc,0x00200000,1,2,NeNDVid.ax,3.02.0000.0020 
Cinepak Codec by Radius,0x00200000,1,1,qcap.dll,6.05.2600.5512 
DivX 6.8.5 Codec (2 Logical CPUs),0x00200000,1,1,qcap.dll,6.05.2600.5512 
ffdshow Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Intel 4:2:0 Video V2.50,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Intel Indeo(R) Video R3.2,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Intel Indeo® Video 4.5,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Indeo® video 5.10,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Codec Intel IYUV,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Microsoft H.261 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Microsoft H.263 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Microsoft RLE,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Microsoft Video 1,0x00200000,1,1,qcap.dll,6.05.2600.5512 
VP60® Simple Profile ,0x00200000,1,1,qcap.dll,6.05.2600.5512 
VP61® Advanced Profile,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Xfire Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Xvid MPEG-4 Codec,0x00200000,1,1,qcap.dll,6.05.2600.5512 
Helix YV12 YUV Codec,0x00200000,1,1,qcap.dll,6.05.2600.5512 
 
Audio Compressors: 
WMA Voice Encoder DMO,0x00600800,1,1,, 
WM Speech Encoder DMO,0x00600800,1,1,, 
WMAudio Encoder DMO,0x00600800,1,1,, 
IAC2,0x00200000,1,1,quartz.dll,6.05.2600.5822 
Lernout & Hauspie CELP 4.8kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.5822 
Lernout & Hauspie SBC 8kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.5822 
Lernout & Hauspie SBC 12kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.5822 
Lernout & Hauspie SBC 16kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.5822 
IMA ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.5822 
PCM,0x00200000,1,1,quartz.dll,6.05.2600.5822 
Ogg Vorbis (mode1),0x00200000,1,1,quartz.dll,6.05.2600.5822 
Ogg Vorbis (mode2),0x00200000,1,1,quartz.dll,6.05.2600.5822 
Ogg Vorbis (mode3),0x00200000,1,1,quartz.dll,6.05.2600.5822 
Ogg Vorbis (mode1+),0x00200000,1,1,quartz.dll,6.05.2600.5822 
Ogg Vorbis (mode2+),0x00200000,1,1,quartz.dll,6.05.2600.5822 
Ogg Vorbis (mode3+),0x00200000,1,1,quartz.dll,6.05.2600.5822 
Microsoft ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.5822 
ACELP.net,0x00200000,1,1,quartz.dll,6.05.2600.5822 
DSP Group TrueSpeech(TM),0x00200000,1,1,quartz.dll,6.05.2600.5822 
Windows Media Audio V1,0x00200000,1,1,quartz.dll,6.05.2600.5822 
Windows Media Audio V2,0x00200000,1,1,quartz.dll,6.05.2600.5822 
GSM 6.10,0x00200000,1,1,quartz.dll,6.05.2600.5822 
Messenger Audio Codec,0x00200000,1,1,quartz.dll,6.05.2600.5822 
Microsoft G.723.1 ,0x00200000,1,1,quartz.dll,6.05.2600.5822 
CCITT A-Law,0x00200000,1,1,quartz.dll,6.05.2600.5822 
CCITT u-Law,0x00200000,1,1,quartz.dll,6.05.2600.5822 
AC-3 ACM Codec,0x00200000,1,1,quartz.dll,6.05.2600.5822 
MPEG Layer-3,0x00200000,1,1,quartz.dll,6.05.2600.5822 
 
Audio Capture Sources: 
Realtek HD Audio Input,0x00200000,0,0,qcap.dll,6.05.2600.5512 
 
Midi Renderers: 
Default MidiOut Device,0x00800000,1,0,quartz.dll,6.05.2600.5822 
Sintetizador por software GS Wa,0x00200000,1,0,quartz.dll,6.05.2600.5822 
 
Dispositivos de captura de sequência WDM: 
,0x00000000,0,0,, 
ScreenCamera HR,0x00200000,1,2,,5.03.2600.5512 
WebcamMax Capture,0x00200000,0,1,,5.03.2600.5512 
 
Dispositivos de composição de sequência WDM: 
Realtek HD Audio output,0x00200000,2,1,,5.03.2600.5512 
 
BDA Rendering Filters: 
BDA IP Sink,0x00200000,1,1,,5.03.2600.5512 
 
Video Capture Sources: 
ScreenCamera HR,0x00200000,1,2,,5.03.2600.5512 
WebcamMax Capture,0x00200000,0,1,,5.03.2600.5512 
 
BDA Transport Information Renderers: 
MPEG-2 Sections and Tables,0x00600000,1,0,mpeg2data.ax, 
 
Dispositivos de sintonização de TV de sequência WDM: 
WebcamMax, WDM Video Capture,0x00000000,0,0,, 
 
Dispositivos Crossbar de sequência WDM: 
WebcamMax, WDM Video Capture,0x00000000,0,0,, 
 
Dispositivos de áudio para TV de sequência WDM: 
WebcamMax, WDM Video Capture,0x00000000,0,0,, 
 
Dispositivos de mistura de sequenciador WDM: 
Microsoft - misturador de áudio Kernel Wave,0x00000000,0,0,, 
 
BDA CP/CA Filters: 
Decrypt/Tag,0x00600000,1,0,encdec.dll,6.05.2600.5512 
Encrypt/Tag,0x00200000,0,0,encdec.dll,6.05.2600.5512 
XDS Codec,0x00200000,0,0,encdec.dll,6.05.2600.5512 
 
Transformação de comunicação de sequência WDM: 
Conversor Tee/Sink-to-Sink,0x00200000,1,1,,5.03.2600.5512 
 
Audio Renderers: 
Realtek HD Audio output,0x00200000,1,0,quartz.dll,6.05.2600.5822 
Default DirectSound Device,0x00800000,1,0,quartz.dll,6.05.2600.5822 
Default WaveOut Device,0x00200000,1,0,quartz.dll,6.05.2600.5822 
DirectSound: Realtek HD Audio output,0x00200000,1,0,quartz.dll,6.05.2600.5822 
 
Dispositivos de sistema de fluxo WDM: 
Realtek HD Audio Input,0x00200000,4,1,,5.03.2600.5512 
Realtek HD Audio output,0x00200000,11,1,,5.03.2600.5512 
 
BDA Receiver Component: 
BDA Slip De-Framer,0x00600000,1,1,,5.03.2600.5512 
 
```Hope I can get it fixed  ](*,)

I think it's this:

     Name: Atheros L2 Fast Ethernet 10/100 Base-T Controller 
Device ID: PCI\VEN_1969&DEV_2048&SUBSYS_82331043&REV_A0\4&38D2602C&0&00E1 
   Driver: C:\WINDOWS\system32\DRIVERS\l251x86.sys, 2.05.6000.0000 (English), 7/3/2007 10:33:26, 29696 bytes

---

### Post by MysteryGuy on 2009-10-31
I downloaded the newest driver and fixed it by transfering it to a pen drive and installing it on Windows.

Thanks for the help anyways Matt. :KS

---


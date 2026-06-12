---
title: "Google Earth Signal 11 Errors - solution"
date: 2012-10-02
forum: General Help
---

### Post by Andrew F in Australia on 2012-10-02
Hi All, 

Another with a Google Earth Signal 11 error.  Libgoogleearth_free.so errors according to the crashlog.



This started out as a cry for help, but in quadruple checking things, found a glitch in Ubuntu that may be causing others problems as well.


The System Settings|Additional Drivers button that picks up third party drivers said that I had current Graphics Card Drivers, but not the case.


Installing correct and current driver from the manufacturer's website fixed the problem.


(other things listed in points 1-3 below were also made - couldn't be bothered changing them back, so they also may be necessary.)


Google earth works well now on Ubuntu 12.04 Pangolin.


 Cheers,


AF


History below


```

 

 horace@horace-HP-ProBook-4730s:/opt/google/earth/free$ google-earth  
 Google Earth has caught signal 11.  
 

 We apologize for the inconvenience, but Google Earth has crashed.  
  This is a bug in the program, and should never happen under normal  
  circumstances. A bug report and debugging data have been written  
  to this text file:  
 

  /home/horace/.googleearth/crashlogs/crashlog-506ac54a.txt  
 

 Please include this file if you submit a bug report to Google.
 

 
``` **Crashlog **```

 Major Version 6  
 Minor Version 0  
 Build Number 0003  
 Build Date May 17 2011  
 Build Time 00:40:40  
 OS Type 3  
 OS Major Version 3  
 OS Minor Version 2  
 OS Build Version 0  
 OS Patch Version 0  
 Crash Signal 11  
 Crash Time 1349174602  
 Up Time 2.32906  
 

 Stacktrace from glibc:  
 ./libgoogleearth_free.so(+0xab953)[0xb76c4953] 
 ./libgoogleearth_free.so(+0xabad3)[0xb76c4ad3] 
 [0xb772f400] 
```
 Installed as per official advice:
 

 [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)
 

 
I've tried most of the suggested fixes that I could find through a forum search here and other google links.

eg:   
 

 (1)
 adding a line to the .GoogleEarthPlus.conf file to disable tool tips

(2)
 Uninstalled the Google-provided DEB file and reinstalled the stable Google Earth package instead of the latest one through the Software Centre.

sudo apt-get install googleearth-package
make-googleearth-package --force
Double-click on the resulting .deb file -- if I remember correctly, it lands on your Desktop -- and follow the instructions. (Once installed, you can delete the .deb file.)

(3)
 **Navigating to /opt/google/earth/free and running the following:**
 **[B]sudo **[/B]**wget [http://librarian.launchpad.net/7037027/libGL.so.1](http://librarian.launchpad.net/7037027/libGL.so.1)**
 Then run the following command: **sudo ****chmod a+x libGL.so.1**
 


 **(4)**
 [B]cd ~/.googleearth
wget [http://mymediasystem.net/wp/2009/01/libGL.so.1.2](http://mymediasystem.net/wp/2009/01/libGL.so.1.2)
ln -s ~/.googleearth/libGL.so.1.2 /usr/lib32/libGL.so.1 
googleearth[/B]
 [B]
(didn't work, no such directory.)[/B]
 


 **(5)**
 
[LIST=1]
[*]**[Get     a copy of ]("http://www.ground-impact.com/libGL.so.1.2")***[libGL.so.1.2]("http://www.ground-impact.com/libGL.so.1.2")*
[*]Put the file in the Google Earth     directory (usually /usr/local/google-earth)
[*]Rename the file to *libGL.so.1*
[*]Start Google Earth and enjoy!
[/LIST]
 **(no such directory – must be operating differently now.)**
 


 (6)
 

 It appears as though it may be a graphics driver issue  AMD/ATI Radeon 6400M
 

 I thought that I was running the current stable release of the AMD driver, the post-release updates crash. [the system settings button picked up a current third party release – stable driver]
 

 This was not the case:
 

 I uninstalled all proprietary drivers  
 

 sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
 then sudo apt-get autoremove to get rid of some unused dependencies.
 

 Downloaded the correct driver from:
 

 [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
 

 Rebooted, then installed new driver.
 

 Google earth works well now
 

 

 

 

 

 

 

 

 

 Output from  
 

 lspci
 

 ```

 horace@horace-HP-ProBook-4730s:~$ lspci 
 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)  
 00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)  
 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)  
 00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)  
 00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)  
 00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)  
 00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)  
 00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)  
 00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)  
 00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)  
 00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)  
 00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b4)  
 00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)  
 00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)  
 00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)  
 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] 
 24:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)  
 24:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)  
 24:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)  
 25:00.0 Network controller: Ralink corp. Device 3592  
 26:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)  
 27:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)  
 horace@horace-HP-ProBook-4730s:~$ 
```
 Is it possible that the two VGA controllers are conflicting?
 

 lspci | grep -i vga ```

 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)  
 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] 
```
 lspci -v | grep -iA12 vga  
 ```
 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller]) 
     Subsystem: Hewlett-Packard Company Device 167d  
     Flags: bus master, fast devsel, latency 0, IRQ 58  
     Memory at d4000000 (64-bit, non-prefetchable) [size=4M]  
     Memory at c0000000 (64-bit, prefetchable) [size=256M]  
     I/O ports at 6000 [size=64]  
     Expansion ROM at <unassigned> [disabled]  
     Capabilities: <access denied>  
     Kernel driver in use: i915  
     Kernel modules: i915  
   
 00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)  
     Subsystem: Hewlett-Packard Company Device 167c  
 --  
 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] (prog-if 00 [VGA controller])  
     Subsystem: Hewlett-Packard Company Device 167d  
     Flags: bus master, fast devsel, latency 0, IRQ 16  
     Memory at b0000000 (64-bit, prefetchable) [size=256M]  
     Memory at d4a00000 (64-bit, non-prefetchable) [size=128K]  
     I/O ports at 5000 [size=256]  
     Expansion ROM at d4a20000 [disabled] [size=128K]  
     Capabilities: <access denied>  
     Kernel driver in use: fglrx_pci  
     Kernel modules: fglrx, radeon  
 

 24:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)  
     Subsystem: Hewlett-Packard Company Device 167c  
 horace@horace-HP-ProBook-4730s:/opt/google/earth/free$ 
```
 glxinfo```
horace@horace-HP-ProBook-4730s:~$ glxinfo | grep render  
 X Error of failed request:  BadRequest (invalid request code or no such operation)  
   Major opcode of failed request:  154 (GLX)  
   Minor opcode of failed request:  19 (X_GLXQueryServerString)  
   Serial number of failed request:  12  
   Current serial number in output stream:  12  
 horace@horace-HP-ProBook-4730s:~$
```
 sudo lshw -C display
 ```
  
 horace@horace-HP-ProBook-4730s:~$  sudo lshw -C display  
 [sudo] password for horace:  
   *-display                
        description: VGA compatible controller  
        product: Seymour [Radeon HD 6400M Series]  
        vendor: Hynix Semiconductor (Hyundai Electronics)  
        physical id: 0  
        bus info: pci@0000:01:00.0  
        version: 00  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm pciexpress msi vga_controller bus_master cap_list rom  
        configuration: driver=fglrx_pci latency=0  
        resources: irq:16 memory:b0000000-bfffffff memory:d4a00000-d4a1ffff ioport:5000(size=256) memory:d4a20000-d4a3ffff  
   *-display  
        description: VGA compatible controller  
        product: 2nd Generation Core Processor Family Integrated Graphics Controller  
        vendor: Intel Corporation  
        physical id: 2  
        bus info: pci@0000:00:02.0  
        version: 09  
        width: 64 bits  
        clock: 33MHz  
        capabilities: msi pm vga_controller bus_master cap_list rom  
        configuration: driver=i915 latency=0  
        resources: irq:58 memory:d4000000-d43fffff memory:c0000000-cfffffff ioport:6000(size=64)  
 horace@horace-HP-ProBook-4730s:~$ 
```

---


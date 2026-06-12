---
title: "Display sleeping when it shouldn't"
date: 2012-05-27
forum: General Help
---

### Post by Zukaro on 2012-05-27
In Ubuntu 12.04 I set my display to never sleep and to not lock my computer, but it still goes into sleep mode after a certain amount of time.  How do I fix this?

---

### Post by carl4926 on 2012-05-27
What about in the Power settings?

---

### Post by Zukaro on 2012-05-28
It doesn't show anything about the display in power settings.

---

### Post by carl4926 on 2012-05-28
Are you only using Unity?

---

### Post by Zukaro on 2012-05-28
Yes.
(it's also a fresh install)

---

### Post by carl4926 on 2012-05-28
Not sure then.
I haven't seen this on any of my 12.04 installs
There may be a way of seeing what is calling the sleep (log?) but not sure?

---

### Post by Zukaro on 2012-05-28
I don't know how to access the log of what's been called or anything like that.

---

### Post by gordintoronto on 2012-05-28
I assume you ran: System Settings, Display and Lock, and selected "Turn screen off" never.

If that didn't work, tell us about your computer. Desktop or laptop? Brand and model? Video card? Monitor? CPU? Memory?

---

### Post by Zukaro on 2012-05-31
My computer is a desktop, it's custom made but I'm not sure as to what the specs are.  All I know is that it uses an AMD CPU, it has 938.0MiB of RAM (in the terminal it says 960508 kB of RAM).  The GPU is integrated with the motherboard.
The monitor connected to my computer is a TOSHIBA TV.

---

### Post by gordintoronto on 2012-05-31
To get all the information about your computer, open Terminal and paste this command from the Edit menu:
sudo lshw -html > Desktop/config.htm

Enter your password when requested. A file will appear on your desktop. When you double-click it, it should open in your browser, with a formatted display of all the information about your computer hardware.

---

### Post by Zukaro on 2012-06-01
Okay; I've done that.  Since I can't post the file here in an attachment (it's too big/wrong format (converting it to another format doesn't help as it's too big)) I'm posting the HTML code here.

From what I've read in it already it's giving me pretty much the same info as I had before (just a lot more info also).

Also, the OS I put on is 32-bit (as I think it's a 32-bit system, but in the HTML document it says the CPU has a 64-bit width (I don't know what that means) yet says the desktop's width is 32-bit (so I just posted the code here instead)).


[HTML]<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta name="generator"  content="lshw-B.02.15" />
<style type="text/css">
  .first {font-weight: bold; margin-left: none; padding-right: 1em;vertical-align: top; }
  .second {padding-left: 1em; width: 100%; vertical-align: center; }
  .id {font-family: monospace;}
  .indented {margin-left: 2em; border-left: dotted thin #dde; padding-bottom: 1em; }
  .node {border: solid thin #ffcc66; padding: 1em; background: #ffffcc; }
  .node-unclaimed {border: dotted thin #c3c3c3; padding: 1em; background: #fafafa; color: red; }
  .node-disabled {border: solid thin #f55; padding: 1em; background: #fee; color: gray; }
</style>
<title>minecraft-server</title>
</head>
<body>
<div class="indented">
<table width="100%" class="node" summary="attributes of minecraft-server">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">minecraft-server</div></td></tr></thead>
 <tbody>
    <tr><td class="first">description: </td><td class="second">Desktop Computer</td></tr>
    <tr><td class="first">product: </td><td class="second">MS-7142</td></tr>
    <tr><td class="first">vendor: </td><td class="second">MICRO-STAR INTERNATIONAL CO., LTD</td></tr>
    <tr><td class="first">version: </td><td class="second">1.00</td></tr>
    <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
    <tr><td class="first">capabilities: </td><td class="second"><dfn title="SMBIOS version 2.3">smbios-2.3</dfn> <dfn title="DMI version 2.3">dmi-2.3</dfn> <dfn title="SMP specification v1.4">smp-1.4</dfn> <dfn title="Symmetric Multi-Processing">smp</dfn> </td></tr>
    <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of minecraft-server"><tr><td class="sub-first"> boot</td><td>=</td><td>normal</td></tr><tr><td class="sub-first"> chassis</td><td>=</td><td>desktop</td></tr><tr><td class="sub-first"> cpus</td><td>=</td><td>1</td></tr></table></td></tr>
 </tbody></table></div>
<div class="indented">
        <div class="indented">
    <table width="100%" class="node" summary="attributes of core">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">core</div></td></tr></thead>
 <tbody>
       <tr><td class="first">description: </td><td class="second">Motherboard</td></tr>
       <tr><td class="first">product: </td><td class="second">MS-7142</td></tr>
       <tr><td class="first">vendor: </td><td class="second">MICRO-STAR INTERNATIONAL CO., LTD</td></tr>
       <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
       <tr><td class="first">version: </td><td class="second">1.00</td></tr>
 </tbody>    </table></div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of firmware">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">firmware</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">BIOS</td></tr>
          <tr><td class="first">vendor: </td><td class="second">Phoenix Technologies, LTD</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
          <tr><td class="first">version: </td><td class="second">6.00 PG</td></tr>
          <tr><td class="first">date: </td><td class="second">06/01/2005</td></tr>
          <tr><td class="first">size: </td><td class="second">128KiB</td></tr>
          <tr><td class="first">capacity: </td><td class="second">448KiB</td></tr>
          <tr><td class="first">capabilities: </td><td class="second"><dfn title="ISA bus">isa</dfn> <dfn title="PCI bus">pci</dfn> <dfn title="Plug-and-Play">pnp</dfn> <dfn title="Advanced Power Management">apm</dfn> <dfn title="BIOS EEPROM can be upgraded">upgrade</dfn> <dfn title="BIOS shadowing">shadowing</dfn> <dfn title="ESCD">escd</dfn> <dfn title="Booting from CD-ROM/DVD">cdboot</dfn> <dfn title="Selectable boot path">bootselect</dfn> <dfn title="BIOS ROM is socketed">socketedrom</dfn> <dfn title="Enhanced Disk Drive extensions">edd</dfn> <dfn title="5.25&quot; 360KB floppy">int13floppy360</dfn> <dfn title="5.25&quot; 1.2MB floppy">int13floppy1200</dfn> <dfn title="3.5&quot; 720KB floppy">int13floppy720</dfn> <dfn title="3.5&quot; 2.88MB floppy">int13floppy2880</dfn> <dfn title="Print Screen key">int5printscreen</dfn> <dfn title="i8042 keyboard controller">int9keyboard</dfn> <dfn title="INT14 serial line control">int14serial</dfn> <dfn title="INT17 printer control">int17printer</dfn> <dfn title="INT10 CGA/Mono video">int10video</dfn> <dfn title="ACPI">acpi</dfn> <dfn title="USB legacy emulation">usb</dfn> <dfn title="AGP">agp</dfn> <dfn title="Booting from LS-120">ls120boot</dfn> <dfn title="Booting from ATAPI ZIP">zipboot</dfn> <dfn title="BIOS boot specification">biosbootspecification</dfn> </td></tr>
 </tbody>       </table></div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of cpu">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">cpu</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">CPU</td></tr>
          <tr><td class="first">product: </td><td class="second">AMD Hammer Family processor - Model Unknown</td></tr>
          <tr><td class="first">vendor: </td><td class="second">Hynix Semiconductor (Hyundai Electronics)</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">4</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">cpu@0</div></td></tr>
          <tr><td class="first">version: </td><td class="second">15.12.2</td></tr>
          <tr><td class="first">slot: </td><td class="second">Socket 940</td></tr>
          <tr><td class="first">size: </td><td class="second">1600MHz</td></tr>
          <tr><td class="first">capacity: </td><td class="second">3GHz</td></tr>
          <tr><td class="first">width: </td><td class="second">64 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">200MHz</td></tr>
          <tr><td class="first">capabilities: </td><td class="second"><dfn title="boot processor">boot</dfn> <dfn title="mathematical co-processor">fpu</dfn> <dfn title="FPU exceptions reporting">fpu_exception</dfn> <dfn title="">wp</dfn> <dfn title="virtual mode extensions">vme</dfn> <dfn title="debugging extensions">de</dfn> <dfn title="page size extensions">pse</dfn> <dfn title="time stamp counter">tsc</dfn> <dfn title="model-specific registers">msr</dfn> <dfn title="4GB+ memory addressing (Physical Address Extension)">pae</dfn> <dfn title="machine check exceptions">mce</dfn> <dfn title="compare and exchange 8-byte">cx8</dfn> <dfn title="on-chip advanced programmable interrupt controller (APIC)">apic</dfn> <dfn title="fast system calls">sep</dfn> <dfn title="memory type range registers">mtrr</dfn> <dfn title="page global enable">pge</dfn> <dfn title="machine check architecture">mca</dfn> <dfn title="conditional move instruction">cmov</dfn> <dfn title="page attribute table">pat</dfn> <dfn title="36-bit page size extensions">pse36</dfn> <dfn title="">clflush</dfn> <dfn title="multimedia extensions (MMX)">mmx</dfn> <dfn title="fast floating point save/restore">fxsr</dfn> <dfn title="streaming SIMD extensions (SSE)">sse</dfn> <dfn title="streaming SIMD extensions (SSE2)">sse2</dfn> <dfn title="fast system calls">syscall</dfn> <dfn title="no-execute bit (NX)">nx</dfn> <dfn title="multimedia extensions (MMXExt)">mmxext</dfn> <dfn title="">fxsr_opt</dfn> <dfn title="64bits extensions (x86-64)">x86-64</dfn> <dfn title="multimedia extensions (3DNow!Ext)">3dnowext</dfn> <dfn title="multimedia extensions (3DNow!)">3dnow</dfn> <dfn title="">up</dfn> <dfn title="">pni</dfn> <dfn title="">lahf_lm</dfn> </td></tr>
 </tbody>       </table></div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of cache:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">cache:0</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">L1 cache</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">8</div></td></tr>
             <tr><td class="first">slot: </td><td class="second">Internal Cache</td></tr>
             <tr><td class="first">size: </td><td class="second">128KiB</td></tr>
             <tr><td class="first">capacity: </td><td class="second">128KiB</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="Synchronous">synchronous</dfn> <dfn title="Internal">internal</dfn> <dfn title="Write-back">write-back</dfn> </td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of cache:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">cache:1</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">L2 cache</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">9</div></td></tr>
             <tr><td class="first">slot: </td><td class="second">External Cache</td></tr>
             <tr><td class="first">size: </td><td class="second">256KiB</td></tr>
             <tr><td class="first">capacity: </td><td class="second">256KiB</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="Synchronous">synchronous</dfn> <dfn title="Internal">internal</dfn> <dfn title="Write-back">write-back</dfn> </td></tr>
 </tbody>          </table></div>
          </div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of memory">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">memory</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">System Memory</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">19</div></td></tr>
          <tr><td class="first">slot: </td><td class="second">System board or motherboard</td></tr>
          <tr><td class="first">size: </td><td class="second">2GiB</td></tr>
 </tbody>       </table></div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of bank:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">bank:0</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">DIMM</td></tr>
             <tr><td class="first">product: </td><td class="second">None</td></tr>
             <tr><td class="first">vendor: </td><td class="second">None</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
             <tr><td class="first">serial: </td><td class="second">None</td></tr>
             <tr><td class="first">slot: </td><td class="second">A0</td></tr>
             <tr><td class="first">size: </td><td class="second">1GiB</td></tr>
             <tr><td class="first">width: </td><td class="second">64 bits</td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of bank:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">bank:1</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">DIMM</td></tr>
             <tr><td class="first">product: </td><td class="second">None</td></tr>
             <tr><td class="first">vendor: </td><td class="second">None</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">1</div></td></tr>
             <tr><td class="first">serial: </td><td class="second">None</td></tr>
             <tr><td class="first">slot: </td><td class="second">A1</td></tr>
             <tr><td class="first">size: </td><td class="second">1GiB</td></tr>
             <tr><td class="first">width: </td><td class="second">64 bits</td></tr>
 </tbody>          </table></div>
          </div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:0</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">K8M800 Host Bridge</td></tr>
          <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">100</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.0</div></td></tr>
          <tr><td class="first">version: </td><td class="second">00</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
          <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of pci:0"><tr><td class="sub-first"> driver</td><td>=</td><td>agpgart-amd64</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>8</td></tr></table></td></tr>
          <tr><td class="first">resources:</td><td class="second"><table summary="resources of pci:0"><tr><td class="sub-first"> irq</td><td>:</td><td>0</td></tr><tr><td class="sub-first"> memory</td><td>:</td><td>e0000000-efffffff</td></tr></table></td></tr>
 </tbody>       </table></div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of pci">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">PCI bridge</td></tr>
             <tr><td class="first">product: </td><td class="second">VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South]</td></tr>
             <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">1</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:01.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">00</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="">pci</dfn> <dfn title="Power Management">pm</dfn> <dfn title="">normal_decode</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> </td></tr>
             <tr><td class="first">resources:</td><td class="second"><table summary="resources of pci"><tr><td class="sub-first"> memory</td><td>:</td><td>f4000000-f5ffffff</td></tr><tr><td class="sub-first"> memory</td><td>:</td><td>f0000000-f3ffffff</td></tr></table></td></tr>
 </tbody>          </table></div>
<div class="indented">
                          <div class="indented">
             <table width="100%" class="node-unclaimed" summary="attributes of display">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">display</div></td></tr></thead>
 <tbody>
                <tr><td class="first">description: </td><td class="second">VGA compatible controller</td></tr>
                <tr><td class="first">product: </td><td class="second">K8M800/K8N800/K8N800A [S3 UniChrome Pro]</td></tr>
                <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
                <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
                <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:01:00.0</div></td></tr>
                <tr><td class="first">version: </td><td class="second">01</td></tr>
                <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
                <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
                <tr><td class="first">capabilities: </td><td class="second"><dfn title="Power Management">pm</dfn> <dfn title="AGP">agp</dfn> <dfn title="AGP 3.0">agp-3.0</dfn> <dfn title="">vga_controller</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> </td></tr>
                <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of display"><tr><td class="sub-first"> latency</td><td>=</td><td>32</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>2</td></tr></table></td></tr>
                <tr><td class="first">resources:</td><td class="second"><table summary="resources of display"><tr><td class="sub-first"> memory</td><td>:</td><td>f0000000-f3ffffff</td></tr><tr><td class="sub-first"> memory</td><td>:</td><td>f4000000-f4ffffff</td></tr><tr><td class="sub-first"> memory</td><td>:</td><td>f5000000-f500ffff</td></tr></table></td></tr>
 </tbody>             </table></div>
             </div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-disabled" summary="attributes of network:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">network:0</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">Wireless interface</td></tr>
             <tr><td class="first">product: </td><td class="second">RT2561/RT61 802.11g PCI</td></tr>
             <tr><td class="first">vendor: </td><td class="second">Ralink corp.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">8</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:08.0</div></td></tr>
             <tr><td class="first">logical name: </td><td class="second"><div class="id">wlan0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">00</td></tr>
             <tr><td class="first">serial: </td><td class="second">00:1f:1f:1d:28:f8</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="Power Management">pm</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> <dfn title="">ethernet</dfn> <dfn title="Physical interface">physical</dfn> <dfn title="Wireless-LAN">wireless</dfn> </td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of network:0"><tr><td class="sub-first"> broadcast</td><td>=</td><td>yes</td></tr><tr><td class="sub-first"> driver</td><td>=</td><td>rt61pci</td></tr><tr><td class="sub-first"> driverversion</td><td>=</td><td>3.2.0-24-generic-pae</td></tr><tr><td class="sub-first"> firmware</td><td>=</td><td>N/A</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>32</td></tr><tr><td class="sub-first"> link</td><td>=</td><td>no</td></tr><tr><td class="sub-first"> multicast</td><td>=</td><td>yes</td></tr><tr><td class="sub-first"> wireless</td><td>=</td><td>IEEE 802.11bg</td></tr></table></td></tr>
             <tr><td class="first">resources:</td><td class="second"><table summary="resources of network:0"><tr><td class="sub-first"> irq</td><td>:</td><td>16</td></tr><tr><td class="sub-first"> memory</td><td>:</td><td>f6000000-f6007fff</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of ide">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">ide</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">IDE interface</td></tr>
             <tr><td class="first">product: </td><td class="second">VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE</td></tr>
             <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">f</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0f.0</div></td></tr>
             <tr><td class="first">logical name: </td><td class="second"><div class="id">scsi0</div></td></tr>
             <tr><td class="first">logical name: </td><td class="second"><div class="id">scsi1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">06</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="">ide</dfn> <dfn title="Power Management">pm</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> <dfn title="Emulated device">emulated</dfn> </td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of ide"><tr><td class="sub-first"> driver</td><td>=</td><td>pata_via</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>32</td></tr></table></td></tr>
             <tr><td class="first">resources:</td><td class="second"><table summary="resources of ide"><tr><td class="sub-first"> irq</td><td>:</td><td>20</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>1f0(size=8)</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>3f6</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>170(size=8)</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>376</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>e000(size=16)</td></tr></table></td></tr>
 </tbody>          </table></div>
<div class="indented">
                          <div class="indented">
             <table width="100%" class="node" summary="attributes of disk">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">disk</div></td></tr></thead>
 <tbody>
                <tr><td class="first">description: </td><td class="second">ATA Disk</td></tr>
                <tr><td class="first">product: </td><td class="second">HDS728080PLAT20</td></tr>
                <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
                <tr><td class="first">bus info: </td><td class="second"><div class="id">scsi@0:0.0.0</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sda</div></td></tr>
                <tr><td class="first">version: </td><td class="second">PF2O</td></tr>
                <tr><td class="first">serial: </td><td class="second">PFD242SDU3V9MB</td></tr>
                <tr><td class="first">size: </td><td class="second">76GiB (82GB)</td></tr>
                <tr><td class="first">capabilities: </td><td class="second"><dfn title="Partitioned disk">partitioned</dfn> <dfn title="MS-DOS partition table">partitioned:dos</dfn> </td></tr>
                <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of disk"><tr><td class="sub-first"> ansiversion</td><td>=</td><td>5</td></tr><tr><td class="sub-first"> signature</td><td>=</td><td>0008abe7</td></tr></table></td></tr>
 </tbody>             </table></div>
<div class="indented">
                                <div class="indented">
                <table width="100%" class="node" summary="attributes of volume:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">volume:0</div></td></tr></thead>
 <tbody>
                   <tr><td class="first">description: </td><td class="second">EXT4 volume</td></tr>
                   <tr><td class="first">vendor: </td><td class="second">Linux</td></tr>
                   <tr><td class="first">physical id: </td><td class="second"><div class="id">1</div></td></tr>
                   <tr><td class="first">bus info: </td><td class="second"><div class="id">scsi@0:0.0.0,1</div></td></tr>
                   <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sda1</div></td></tr>
                   <tr><td class="first">logical name: </td><td class="second"><div class="id">/</div></td></tr>
                   <tr><td class="first">version: </td><td class="second">1.0</td></tr>
                   <tr><td class="first">serial: </td><td class="second">1fe220b7-82dd-446b-9d66-022322fccab7</td></tr>
                   <tr><td class="first">size: </td><td class="second">75GiB</td></tr>
                   <tr><td class="first">capacity: </td><td class="second">75GiB</td></tr>
                   <tr><td class="first">capabilities: </td><td class="second"><dfn title="Primary partition">primary</dfn> <dfn title="Bootable partition (active)">bootable</dfn> <dfn title="">journaled</dfn> <dfn title="Extended Attributes">extended_attributes</dfn> <dfn title="4GB+ files">large_files</dfn> <dfn title="16TB+ files">huge_files</dfn> <dfn title="directories with 65000+ subdirs">dir_nlink</dfn> <dfn title="needs recovery">recover</dfn> <dfn title="extent-based allocation">extents</dfn> <dfn title="">ext4</dfn> <dfn title="EXT2/EXT3">ext2</dfn> <dfn title="initialized volume">initialized</dfn> </td></tr>
                   <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of volume:0"><tr><td class="sub-first"> created</td><td>=</td><td>2012-05-27 20:24:15</td></tr><tr><td class="sub-first"> filesystem</td><td>=</td><td>ext4</td></tr><tr><td class="sub-first"> lastmountpoint</td><td>=</td><td>/</td></tr><tr><td class="sub-first"> modified</td><td>=</td><td>2012-05-27 20:48:48</td></tr><tr><td class="sub-first"> mount.fstype</td><td>=</td><td>ext4</td></tr><tr><td class="sub-first"> mount.options</td><td>=</td><td>rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered</td></tr><tr><td class="sub-first"> mounted</td><td>=</td><td>2012-05-31 11:53:23</td></tr><tr><td class="sub-first"> state</td><td>=</td><td>mounted</td></tr></table></td></tr>
 </tbody>                </table></div>
                </div>
<div class="indented">
                                <div class="indented">
                <table width="100%" class="node" summary="attributes of volume:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">volume:1</div></td></tr></thead>
 <tbody>
                   <tr><td class="first">description: </td><td class="second">Extended partition</td></tr>
                   <tr><td class="first">physical id: </td><td class="second"><div class="id">2</div></td></tr>
                   <tr><td class="first">bus info: </td><td class="second"><div class="id">scsi@0:0.0.0,2</div></td></tr>
                   <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sda2</div></td></tr>
                   <tr><td class="first">size: </td><td class="second">958MiB</td></tr>
                   <tr><td class="first">capacity: </td><td class="second">958MiB</td></tr>
                   <tr><td class="first">capabilities: </td><td class="second"><dfn title="Primary partition">primary</dfn> <dfn title="Extended partition">extended</dfn> <dfn title="Partitioned disk">partitioned</dfn> <dfn title="Extended partition">partitioned:extended</dfn> </td></tr>
 </tbody>                </table></div>
<div class="indented">
                                      <div class="indented">
                   <table width="100%" class="node" summary="attributes of logicalvolume">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">logicalvolume</div></td></tr></thead>
 <tbody>
                      <tr><td class="first">description: </td><td class="second">Linux swap / Solaris partition</td></tr>
                      <tr><td class="first">physical id: </td><td class="second"><div class="id">5</div></td></tr>
                      <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sda5</div></td></tr>
                      <tr><td class="first">capacity: </td><td class="second">958MiB</td></tr>
                      <tr><td class="first">capabilities: </td><td class="second"><dfn title="No filesystem">nofs</dfn> </td></tr>
 </tbody>                   </table></div>
                   </div>
                </div>
             </div>
<div class="indented">
                          <div class="indented">
             <table width="100%" class="node" summary="attributes of cdrom">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">cdrom</div></td></tr></thead>
 <tbody>
                <tr><td class="first">description: </td><td class="second">DVD-RAM writer</td></tr>
                <tr><td class="first">product: </td><td class="second">DVDRAM GSA-4163B</td></tr>
                <tr><td class="first">vendor: </td><td class="second">HL-DT-ST</td></tr>
                <tr><td class="first">physical id: </td><td class="second"><div class="id">1</div></td></tr>
                <tr><td class="first">bus info: </td><td class="second"><div class="id">scsi@1:0.0.0</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/cdrom</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/cdrw</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/dvd</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/dvdrw</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sr0</div></td></tr>
                <tr><td class="first">version: </td><td class="second">A103</td></tr>
                <tr><td class="first">capabilities: </td><td class="second"><dfn title="support is removable">removable</dfn> <dfn title="Audio CD playback">audio</dfn> <dfn title="CD-R burning">cd-r</dfn> <dfn title="CD-RW burning">cd-rw</dfn> <dfn title="DVD playback">dvd</dfn> <dfn title="DVD-R burning">dvd-r</dfn> <dfn title="DVD-RAM burning">dvd-ram</dfn> </td></tr>
                <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of cdrom"><tr><td class="sub-first"> ansiversion</td><td>=</td><td>5</td></tr><tr><td class="sub-first"> status</td><td>=</td><td>nodisc</td></tr></table></td></tr>
 </tbody>             </table></div>
             </div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">usb:0</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">USB controller</td></tr>
             <tr><td class="first">product: </td><td class="second">VT82xxxxx UHCI USB 1.1 Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">10</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:10.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">81</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="Power Management">pm</dfn> <dfn title="Universal Host Controller Interface (USB1)">uhci</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> </td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of usb:0"><tr><td class="sub-first"> driver</td><td>=</td><td>uhci_hcd</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>32</td></tr></table></td></tr>
             <tr><td class="first">resources:</td><td class="second"><table summary="resources of usb:0"><tr><td class="sub-first"> irq</td><td>:</td><td>21</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>e100(size=32)</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">usb:1</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">USB controller</td></tr>
             <tr><td class="first">product: </td><td class="second">VT82xxxxx UHCI USB 1.1 Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">10.1</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:10.1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">81</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="Power Management">pm</dfn> <dfn title="Universal Host Controller Interface (USB1)">uhci</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> </td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of usb:1"><tr><td class="sub-first"> driver</td><td>=</td><td>uhci_hcd</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>32</td></tr></table></td></tr>
             <tr><td class="first">resources:</td><td class="second"><table summary="resources of usb:1"><tr><td class="sub-first"> irq</td><td>:</td><td>21</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>e200(size=32)</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:2">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">usb:2</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">USB controller</td></tr>
             <tr><td class="first">product: </td><td class="second">VT82xxxxx UHCI USB 1.1 Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">10.2</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:10.2</div></td></tr>
             <tr><td class="first">version: </td><td class="second">81</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="Power Management">pm</dfn> <dfn title="Universal Host Controller Interface (USB1)">uhci</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> </td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of usb:2"><tr><td class="sub-first"> driver</td><td>=</td><td>uhci_hcd</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>32</td></tr></table></td></tr>
             <tr><td class="first">resources:</td><td class="second"><table summary="resources of usb:2"><tr><td class="sub-first"> irq</td><td>:</td><td>21</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>e300(size=32)</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:3">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">usb:3</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">USB controller</td></tr>
             <tr><td class="first">product: </td><td class="second">VT82xxxxx UHCI USB 1.1 Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">10.3</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:10.3</div></td></tr>
             <tr><td class="first">version: </td><td class="second">81</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="Power Management">pm</dfn> <dfn title="Universal Host Controller Interface (USB1)">uhci</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> </td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of usb:3"><tr><td class="sub-first"> driver</td><td>=</td><td>uhci_hcd</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>32</td></tr></table></td></tr>
             <tr><td class="first">resources:</td><td class="second"><table summary="resources of usb:3"><tr><td class="sub-first"> irq</td><td>:</td><td>21</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>e400(size=32)</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:4">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">usb:4</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">USB controller</td></tr>
             <tr><td class="first">product: </td><td class="second">USB 2.0</td></tr>
             <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">10.4</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:10.4</div></td></tr>
             <tr><td class="first">version: </td><td class="second">86</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="Power Management">pm</dfn> <dfn title="Enhanced Host Controller Interface (USB2)">ehci</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> </td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of usb:4"><tr><td class="sub-first"> driver</td><td>=</td><td>ehci_hcd</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>32</td></tr></table></td></tr>
             <tr><td class="first">resources:</td><td class="second"><table summary="resources of usb:4"><tr><td class="sub-first"> irq</td><td>:</td><td>21</td></tr><tr><td class="sub-first"> memory</td><td>:</td><td>f6008000-f60080ff</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of isa">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">isa</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">ISA bridge</td></tr>
             <tr><td class="first">product: </td><td class="second">VT8237 ISA bridge [KT600/K8T800/K8T890 South]</td></tr>
             <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">11</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:11.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">00</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="">isa</dfn> <dfn title="Power Management">pm</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> </td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of isa"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of multimedia">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">multimedia</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">Multimedia audio controller</td></tr>
             <tr><td class="first">product: </td><td class="second">VT8233/A/8235/8237 AC97 Audio Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">11.5</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:11.5</div></td></tr>
             <tr><td class="first">version: </td><td class="second">60</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="Power Management">pm</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> </td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of multimedia"><tr><td class="sub-first"> driver</td><td>=</td><td>snd_via82xx</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
             <tr><td class="first">resources:</td><td class="second"><table summary="resources of multimedia"><tr><td class="sub-first"> irq</td><td>:</td><td>22</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>e500(size=256)</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of network:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">network:1</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">Ethernet interface</td></tr>
             <tr><td class="first">product: </td><td class="second">VT6102 [Rhine-II]</td></tr>
             <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">12</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:12.0</div></td></tr>
             <tr><td class="first">logical name: </td><td class="second"><div class="id">eth0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">78</td></tr>
             <tr><td class="first">serial: </td><td class="second">00:13:d3:17:38:c8</td></tr>
             <tr><td class="first">size: </td><td class="second">100Mbit/s</td></tr>
             <tr><td class="first">capacity: </td><td class="second">100Mbit/s</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second"><dfn title="Power Management">pm</dfn> <dfn title="bus mastering">bus_master</dfn> <dfn title="PCI capabilities listing">cap_list</dfn> <dfn title="">ethernet</dfn> <dfn title="Physical interface">physical</dfn> <dfn title="twisted pair">tp</dfn> <dfn title="Media Independent Interface">mii</dfn> <dfn title="10Mbit/s">10bt</dfn> <dfn title="10Mbit/s (full duplex)">10bt-fd</dfn> <dfn title="100Mbit/s">100bt</dfn> <dfn title="100Mbit/s (full duplex)">100bt-fd</dfn> <dfn title="Auto-negotiation">autonegotiation</dfn> </td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of network:1"><tr><td class="sub-first"> autonegotiation</td><td>=</td><td>on</td></tr><tr><td class="sub-first"> broadcast</td><td>=</td><td>yes</td></tr><tr><td class="sub-first"> driver</td><td>=</td><td>via-rhine</td></tr><tr><td class="sub-first"> driverversion</td><td>=</td><td>1.5.0</td></tr><tr><td class="sub-first"> duplex</td><td>=</td><td>full</td></tr><tr><td class="sub-first"> ip</td><td>=</td><td>192.168.3.100</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>32</td></tr><tr><td class="sub-first"> link</td><td>=</td><td>yes</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>8</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>3</td></tr><tr><td class="sub-first"> multicast</td><td>=</td><td>yes</td></tr><tr><td class="sub-first"> port</td><td>=</td><td>MII</td></tr><tr><td class="sub-first"> speed</td><td>=</td><td>100Mbit/s</td></tr></table></td></tr>
             <tr><td class="first">resources:</td><td class="second"><table summary="resources of network:1"><tr><td class="sub-first"> irq</td><td>:</td><td>23</td></tr><tr><td class="sub-first"> ioport</td><td>:</td><td>e600(size=256)</td></tr><tr><td class="sub-first"> memory</td><td>:</td><td>f6009000-f60090ff</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:1</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">K8M800 Host Bridge</td></tr>
          <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">101</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.1</div></td></tr>
          <tr><td class="first">version: </td><td class="second">00</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
 </tbody>       </table></div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci:2">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:2</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">K8M800 Host Bridge</td></tr>
          <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">102</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.2</div></td></tr>
          <tr><td class="first">version: </td><td class="second">00</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
 </tbody>       </table></div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci:3">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:3</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">K8M800 Host Bridge</td></tr>
          <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">103</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.3</div></td></tr>
          <tr><td class="first">version: </td><td class="second">00</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
 </tbody>       </table></div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci:4">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:4</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">K8M800 Host Bridge</td></tr>
          <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">104</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.4</div></td></tr>
          <tr><td class="first">version: </td><td class="second">00</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
 </tbody>       </table></div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci:5">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:5</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">K8M800 Host Bridge</td></tr>
          <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">105</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.7</div></td></tr>
          <tr><td class="first">version: </td><td class="second">00</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
 </tbody>       </table></div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci:6">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:6</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">K8 [Athlon64/Opteron] HyperTransport Technology Configuration</td></tr>
          <tr><td class="first">vendor: </td><td class="second">Hynix Semiconductor (Hyundai Electronics)</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">106</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:18.0</div></td></tr>
          <tr><td class="first">version: </td><td class="second">00</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
 </tbody>       </table></div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci:7">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:7</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">K8 [Athlon64/Opteron] Address Map</td></tr>
          <tr><td class="first">vendor: </td><td class="second">Hynix Semiconductor (Hyundai Electronics)</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">107</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:18.1</div></td></tr>
          <tr><td class="first">version: </td><td class="second">00</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
 </tbody>       </table></div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci:8">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:8</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">K8 [Athlon64/Opteron] DRAM Controller</td></tr>
          <tr><td class="first">vendor: </td><td class="second">Hynix Semiconductor (Hyundai Electronics)</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">108</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:18.2</div></td></tr>
          <tr><td class="first">version: </td><td class="second">00</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
 </tbody>       </table></div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci:9">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:9</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">K8 [Athlon64/Opteron] Miscellaneous Control</td></tr>
          <tr><td class="first">vendor: </td><td class="second">Hynix Semiconductor (Hyundai Electronics)</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">109</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:18.3</div></td></tr>
          <tr><td class="first">version: </td><td class="second">00</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
          <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of pci:9"><tr><td class="sub-first"> driver</td><td>=</td><td>k8temp</td></tr></table></td></tr>
          <tr><td class="first">resources:</td><td class="second"><table summary="resources of pci:9"><tr><td class="sub-first"> irq</td><td>:</td><td>0</td></tr></table></td></tr>
 </tbody>       </table></div>
       </div>
    </div>
</body>
</html>[/HTML]

---

### Post by LinGNUbie on 2012-06-01
Just a thought, but perhaps power setting in the bios could be taking control via acpi? I.E.- standby or screen powerdown after X-minutes.

---

### Post by Zukaro on 2012-06-01
There's nothing in the BIOS about putting the monitor to sleep or anything like that.

---

### Post by LinGNUbie on 2012-06-01
It was just a thought, but some BIOS have such power saving settings after X amount of time of inactivity, which does affect displays. I have not ventured into 12.04 yet, but the Screensaver in 11.10 also had settings that would put the display to sleep.

---

### Post by Zukaro on 2012-06-02
K.  As for the screen saver, I've disabled the screen saver (I clicked the "do not put monitor to sleep" option, yet it still sleeps).

---

### Post by Zukaro on 2012-06-07
Anyone know of a way to fix this?

---


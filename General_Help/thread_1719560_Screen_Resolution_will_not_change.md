---
title: "Screen Resolution will not change"
date: 2011-04-01
forum: General Help
---

### Post by ridethepanther on 2011-04-01
I cannot get my screen resolution to change from 1600x1200. This is a new install of Ubuntu 10.10 and the desired option ( 1024x768 ) is listed under System/Preferences/Monitors. Changing the resolution and clicking Apply results in a screen refresh, but the resolution remains at 1600x1200.

I have gone through just about every tutorial and thread I can find, but nothing works. Here is some relevant information I have gathered:

**XRandR:**

Failed to get size of gamma for output default
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200      65.0*    60.0  
   1400x1050      75.0     70.0     60.0  
   1280x1024      75.0     60.0  
   1280x960       85.0     60.0  
   1024x768       87.0     85.0     75.0     70.0     60.0  
   800x600        85.0     75.0     72.0     65.0     60.0     56.0  
   640x480        85.0     75.0     60.0     73.0  
   640x400        85.0  
   512x384        87.0     85.0     75.0     70.0     60.0  
   400x300        85.0     75.0     72.0     60.0     56.0  
   320x240        85.0     75.0     73.0     60.0  
   320x200        85.0  

**lspci |grep VGA:**

01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

**sudo lshw -C video:**

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=32 maxlatency=255 mingnt=4
       resources: memory:e1000000-e107ffff memory:d8000000-dfffffff memory:e0000000-e000ffff


Any ideas?

---

### Post by ApocryphalAuthor on 2011-04-02
What kind of graphics card to you have in this system?  Are there proprietary drivers available for it, and if so do you have them installed?

---


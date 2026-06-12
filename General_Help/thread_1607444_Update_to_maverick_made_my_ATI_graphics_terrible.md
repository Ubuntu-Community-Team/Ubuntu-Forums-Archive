---
title: "Update to maverick made my ATI graphics terrible"
date: 2010-10-27
forum: General Help
---

### Post by tarekeldeeb on 2010-10-27
Hello all,

I used to have lucid, with the open source ATI drivers installed.
Got the driver: System > Admin > Additional Drivers >> Activate the ATI

sudo lshw gets:

*-display
                description: VGA compatible controller
                product: RS482 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8

When I updated to meverick , the driver could not be found under  System > Admin > Additional Drivers. Although I can enable desktop effects and play some videos, online video streaming is bad, glxgears does not exceed 60 fps.

Can anyone point out how to get the driver installed?

Thanks in advance,
Tarek

---


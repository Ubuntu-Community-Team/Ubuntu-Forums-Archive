---
title: "No sound on Dell Mini 9 with 10.04 UNR"
date: 2011-11-07
forum: General Help
---

### Post by JEBB on 2011-11-07
Somehow I've turned off the sound on my DM9.  Using the System Preferences won't turn it back on.  I know it isn't a sound card or speaker problem because I can start the DM9 from a flash drive and the sound works.  Any suggestions about where to look?  Thanks.

---

### Post by bluexrider on 2011-11-07
Would be strange but System> Preferences> Sound> hardware tab double check if the correct profile is listed and the mute box is not checked. 

Terminal:

sudo lshw

to confirm the driver is correct 
 *-multimedia:0
             description: Multimedia audio controller
configuration: driver=

---

### Post by JEBB on 2011-11-07
When I entered   sudo lshw  in terminal, I got:
------------------------------------------
*-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f0540000-f0543fff
--------------------------------------------------

That looks ok to me.  How does it look to you?

---

### Post by JEBB on 2011-11-07
Because of a problem with the sensitivity of the touchpad, I have put in commands to turn it off at startup.  Maybe that also turns off the sound.

---

### Post by bluexrider on 2011-11-07
Whatever commands you entered may have disabled the sound. I would look at that. 

As you said if you boot from the USB it works fine. Need to backtrack those entries.

---

### Post by wildmanne39 on 2011-11-07
Hi, here is a sound guide that may help.
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)
Please let us know if it helps it is still a work in progress.
Thank you

---


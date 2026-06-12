---
title: "No Sound, Only Dummy Output"
date: 2011-05-18
forum: General Help
---

### Post by matt18224 on 2011-05-18
I recently installed Ubuntu 11.04 on a desktop I have just purchased.After having had Ubuntu on my new computer for a week or so, I needed to reboot. Now, all traces of sound hardware in the Sounds menu are gone, and the only output option is "Dummy Output." I've searched everywhere and tried everything I could find to fix it, including purging and reinstalling ALSA, removing possible conflicting packages, etc. Any help would be greatly appreciated.

---

### Post by lmarmisa on 2011-05-18
Open a terminal and type these commands:

```

cd
mv .pulse .pulse.old

```

Then reboot the computer. 

If your problem is related to a corrupted sound config file on your user account, this command will fix it.

---

### Post by matt18224 on 2011-05-18
I already removed the ~/.pulse folder and rebooted a few minutes before I posted here and it did not fix my problem.

---

### Post by lmarmisa on 2011-05-18
Type this command in order to verify that the audio controller is correctly identified:

```

luis@UB1104ENG:~$ sudo lshw -class multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: 82801AA AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=64
       resources: irq:5 ioport:d100(size=256) ioport:d200(size=64)
luis@UB1104ENG:~$ 


```

---

### Post by matt18224 on 2011-05-18
This is the result. Since I have two graphics cards and an audio card, I guess that's why there's three. The first two are from the graphics cards, so the last one is my audio card, which is what I'd be using. 
```

matt@matt-Aurora-R3:~$ sudo lshw -class multimedia
  *-multimedia UNCLAIMED  
       description: Audio device
       product: GF104 High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fa080000-fa083fff
  *-multimedia UNCLAIMED
       description: Audio device
       product: GF104 High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6080000-f6083fff
  *-multimedia UNCLAIMED
       description: Audio device
       product: 6 Series Chipset Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6100000-f6103fff
matt@matt-Aurora-R3:~$

```

---

### Post by lmarmisa on 2011-05-18
Your problem is related to drivers. 

A node is marked as UNCLAIMED if no specific support for it has been loaded (or lshw has been unable to identify the driver).

---

### Post by lmarmisa on 2011-05-18
Take a look to System -> Administration -> Additional Drivers.

---

### Post by matt18224 on 2011-05-18
The Additional Drivers window says, "No proprietary drivers are in use on this system." It lists a single driver that it says is available, but not in use for my NVidia graphics cards. If the problem has to do with drivers, then why would it work at first, then suddenly not work? I haven't really messed with any hardware settings since I've installed Ubuntu.

---

### Post by lmarmisa on 2011-05-18
I am sorry. I can not give an answer to your questions. 

Try to do this test. Boot into a Ubuntu Live CD/USB and check if you recover the sound in this case. If your sound is good, repeat the command in those conditions:

```

sudo lshw -class multimedia

```

---

### Post by lmarmisa on 2011-05-18
> **matt18224 said:**
> The Additional Drivers window says, "No proprietary drivers are in use on this system." It lists a single driver that it says is available, but not in use for my NVidia graphics cards. If the problem has to do with drivers, then why would it work at first, then suddenly not work? I haven't really messed with any hardware settings since I've installed Ubuntu.

I recommend to activate the NVidia driver.

This examples belong to a computer with graphical and multimedia devices manufactured by NVidia.

```

luis@UB1010ZOTAC:~$ sudo lshw -class multimedia
[sudo] password for luis: 
  *-multimedia            
       description: Audio device
       product: MCP79 High Definition Audio
       vendor: nVidia Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       version: b1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:20 memory:fae78000-fae7bfff
luis@UB1010ZOTAC:~$

```

---


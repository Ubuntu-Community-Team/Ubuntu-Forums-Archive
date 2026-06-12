---
title: "Unable to install ATI display drivers"
date: 2010-05-31
forum: General Help
---

### Post by Dhahlia on 2010-05-31
[SIZE="4"]**[CENTER](THIS IS BEING DONE WITHIN A VIRTUAL MACHINE)[/CENTER]**[/SIZE]
I'm trying to install the catalyst control center for my Ati Radeon 4890 graphics card, running the file through the terminal comes back with a missing "vcdk" file, picture related.

[[IMG]http://img405.imageshack.us/img405/2527/screenshotyx.th.png[/IMG]](http://img405.imageshack.us/i/screenshotyx.png/)



```

dahlia@dahlia-desktop:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=0
       resources: memory:e0000000-e0ffffff(prefetchable)

```
So because I'm running this within a VirtualMachine the system is unable to detect the proper hardware, what are my alternatives (besides not using a VM).Proprietary drivers are enabled.

---


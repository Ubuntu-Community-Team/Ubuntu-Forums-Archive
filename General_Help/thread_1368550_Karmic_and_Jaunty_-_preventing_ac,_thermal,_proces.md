---
title: "Karmic and Jaunty - preventing ac, thermal, processor, battery modules from loading"
date: 2009-12-30
forum: General Help
---

### Post by james_mcl on 2009-12-30
Hi,

I've got a Compaq Presario laptop with two partitions, one being Ubuntu Hardy. I've tried this past year to install Intrepid, Jaunty, and Karmic on the other partition, but have encountered a "repeating keyboard" bug each time which has rendered the new installation unusable and forced me to go back to Hardy.

(see [http://ubuntuforums.org/showthread.php?t=1268739](http://ubuntuforums.org/showthread.php?t=1268739), also [http://ubuntuforums.org/showthread.php?t=1029783](http://ubuntuforums.org/showthread.php?t=1029783))

While trying to look for workarounds, I found [http://bugzilla.kernel.org/show_bug.cgi?id=9147](http://bugzilla.kernel.org/show_bug.cgi?id=9147) . To see if this is the problem, it seems I need to:

"restart with 'acpi=off' kernel parameter (radical approach) or unload the 'ac,thermal,processor,battery' modules (much better)"

Is there a file I can edit so that when the machine is booted, these modules are not loaded? Or, if they have to be unloaded, a way to ensure they will be unloaded at boot time automatically?

Thanks,

James.

PS. Any advice on the consequences of acpi=off would also be appreciated.

---


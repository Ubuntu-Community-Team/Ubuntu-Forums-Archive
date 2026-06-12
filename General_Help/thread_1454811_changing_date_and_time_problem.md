---
title: "changing date and time problem"
date: 2010-04-15
forum: General Help
---

### Post by iageoscience on 2010-04-15
I installed my linux os  in vmware .
I need to set time of  virtual machine to later time  ( 2005 ) .
I have an application whose  license expires at 2006 so I have to do this in order for it to work .
but  when I change it it comes back to the current time ,
so what is the  solution for this .
Thanks in advance

---

### Post by SoftPops on 2010-04-15
Your VM will be picking up the time/date from the main OS (or system clock). If you reset this before loading Linux in the VM you should be okay. Probably best if you are not connected to a network in case your main OS is picking up date/time from a time server.
 
Hope this helps.

---

### Post by srs5694 on 2010-04-15
You can disable network time syncs by uninstalling the ntp package.

I'm not very familiar with VMware. It may have an option to adjust the hardware clock when it's launched. I know that QEMU has such an option (-startdate), but that's no guarantee that VMware has an equivalent. If not, you'll just have to manually adjust it, preferably in VMware's BIOS or BIOS equivalent, each time you boot.

---


---
title: "graphical LVM manager"
date: 2009-07-12
forum: General Help
---

### Post by unix1adm on 2009-07-12
I loaded the graphical LMV application but it will not launch. 

Is there any good readme on using the LVM. I read the man pages but was looking for a graphical interface if possible. 

This is the program I loaded. 
Logical Volume Management
System-config-lvm provides a graphical interface to the LVM tools (and related utilities, including fsck and resize2fs) which is good for non-emergency storage administration. It enables you to manage your logical volume and filesystem configuration with a few mouse clicks, and it prevents potentially- disasterous command-line mistakes such as reducing a logical volume size before reducing the filesystem contained within that volume.  
(One word of warning: system-config-lvm does not recognize RAID elements as being in use, and therefore lists them as "Unitnitialized Entities". If you are using a LVM-on-RAID configuration, system-config-lvm will let you wipe out RAID elements by making them into PVs. Be careful!)

---

### Post by unix1adm on 2009-07-12
anyone use this?

---

### Post by unix1adm on 2009-07-30
I tried to run this from command line and i see the following. Makes no sense to me. I uninstalled and reinstalled. 


sudo ./system-config-lvm.py
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Traceback (most recent call last):
  File "./system-config-lvm.py", line 173, in <module>
    runFullGUI()
  File "./system-config-lvm.py", line 158, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "./system-config-lvm.py", line 108, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 133, in __init__
    self.prepare_tree()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 214, in prepare_tree
    self.model_factory.reload()
  File "/usr/share/system-config-lvm/lvm_model.py", line 164, in reload
    self.__PVs = self.__query_partitions()
  File "/usr/share/system-config-lvm/lvm_model.py", line 198, in __query_partitions
    multipath_data = multipath_obj.get_multipath_data()
  File "/usr/share/system-config-lvm/Multipath.py", line 30, in get_multipath_data
    raise CommandError('FATAL', COMMAND_FAILURE % ("dmsetup",cmdstr, e))
NameError: global name 'CommandError' is not defined

---

### Post by unix1adm on 2009-07-30
post deleted

---

### Post by unix1adm on 2009-07-31
lvcreate
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.27 (2008-06-25)(compat) and kernel driver 
  striped: Required device-mapper target(s) not detected in your kernel
  Run `lvcreate --help' for more information.

---


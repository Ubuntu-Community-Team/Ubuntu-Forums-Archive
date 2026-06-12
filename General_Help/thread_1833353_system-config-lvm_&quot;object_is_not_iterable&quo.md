---
title: "system-config-lvm &quot;object is not iterable&quot;"
date: 2011-08-25
forum: General Help
---

### Post by jason50146 on 2011-08-25
I'm trying to run system-config-lvm and get the output below.  Worked fine immediately after installing 11.04, but not now.  I've tried re-installing system-config-lvm and python.

Thoughts?

```
jason@jason-MS-7599:~$ sudo system-config-lvm
Traceback (most recent call last):
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 172, in <module>
    runFullGUI()
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 157, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 105, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 133, in __init__
    self.prepare_tree()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 214, in prepare_tree
    self.model_factory.reload()
  File "/usr/share/system-config-lvm/lvm_model.py", line 165, in reload
    self.__PVs = self.__query_partitions()
  File "/usr/share/system-config-lvm/lvm_model.py", line 276, in __query_partitions
    pv.setPartition(old_pv.getPartition())
  File "/usr/share/system-config-lvm/PhysicalVolume.py", line 135, in setPartition
    def setPartition(self, (devname, part)):
TypeError: 'NoneType' object is not iterable

```

---

### Post by jason50146 on 2011-08-27
I believe the problem was caused by adding a hard drive to my system that had been part of a different logical volume.  Apparently system-config-lvm choked when it found a physical volume that was part of a non-existant logical volume.  I added the drive manually to my current logical volume and now system-config-lvm is working again.

---


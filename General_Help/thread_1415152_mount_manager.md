---
title: "mount manager"
date: 2010-02-24
forum: General Help
---

### Post by nischalinn on 2010-02-24
I don't know how to use Mount Manager,can anyone brief me.
Thank You.

---

### Post by chaanakya_chiraag on 2010-02-24
See here:
[http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html]("http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html")

---

### Post by nischalinn on 2010-02-24
When I open Mount Manager from System->Administration->Mount Manager it asks for my password.After I enter my password,it disappears.It don not shows the mount manager,or I can not find it.I can not understand.:( Any one have idea,where it lies.

---

### Post by rbc on 2010-02-24
Open terminal and type *mountmanager*. It will probably show some errors that you can post back with

---

### Post by nischalinn on 2010-02-25
> **rbc said:**
> Open terminal and type *mountmanager*. It will probably show some errors that you can post back with

Thanks for your suggestion.

I am posting the whole of the terminal screen. Now can you tell me what has happened.

 sarkar@sarkar-desktop:~$ mountmanager
4 records in /etc/fstab were detected. 
[G] DBus interface was created
[G] All devices were recieved
[I] Storage device was detected: "/dev/sda2" 
[I] Storage device was detected: "/dev/sda8" 
[I] Storage device was detected: "/dev/sda7" 
[I] Storage device was detected: "/dev/sda1" 
[I] Storage device was detected: "/dev/sda6" 
[I] Storage device was detected: "/dev/sda5" 
[I] Storage device was detected: "/dev/sr0" 
[I] Storage device was detected: "/dev/sda" 
[G] Parsing of  "/usr/share/mountmanager/options/common.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/iso9660.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/udf.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/vfat.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/ntfs-3g.xml"  was successful 
Segmentation fault

---

### Post by frodon on 2010-02-25
Threads merged.

Please do not open more than one thread per support request.

---

### Post by chaanakya_chiraag on 2010-02-25
That doesn't look good...it's crashing :(  I'm not sure why it would be, though.

---

### Post by chaanakya_chiraag on 2010-02-25
Try running ```
mm --debug
``` and post back the output.

---

### Post by nischalinn on 2010-02-26
> **chaanakya_chiraag said:**
> Try running ```
mm --debug
``` and post back the output.

Thanks for your suggestion.I've tried the command "mm --debug" and I got:


$ mm --debug
4 records in /etc/fstab were detected. [G] DBus interface was created
[G] All devices were recieved
[I] Storage device was detected: "/dev/sda8" 
[I] Storage device was detected: "/dev/sda7" 
[I] Storage device was detected: "/dev/sda6" 
[I] Storage device was detected: "/dev/sda2" 
[I] Storage device was detected: "/dev/sda5" 
[I] Storage device was detected: "/dev/sr0" 
[I] Storage device was detected: "/dev/sda1" 
[I] Storage device was detected: "/dev/sda" 
[G] Parsing of  "/usr/share/mountmanager/options/common.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/vfat.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/iso9660.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/udf.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/ntfs-3g.xml"  was successful

---


---
title: "Sharing with Windows on same computer"
date: 2010-10-28
forum: General Help
---

### Post by toddvb on 2010-10-28
I have Ubuntu and Windows 7 on my laptop and want to share files.  Is there a way do to this?

---

### Post by harrismh777 on 2010-10-28
There are several ways to accomplish this little trick.

The best (easiest,safest) is to create two partitions for windows prior to installing ubuntu. The first is the boot partition (holding windows) the second is a fat32 partition that will be used only for data. 

Ubuntu will be able to mount (access) the second partition for storing or retrieving shared files. 

If your machine is setup properly, then Ubuntu will be able to mount and access the main windows partition as well;;; but this is not recommended. Create a separate partition for shared files that each OS can mount safely.

---

### Post by toddvb on 2010-10-28
Thanks for responding.  

I just used the wubi install file and I only see one partition/drive  while in Windows. I didn't see a option to create a new partition in the  install, but I'm new to Ubuntu (and linux).

---

### Post by yetiman64 on 2010-10-28
> **toddvb said:**
> Thanks for responding.  

I just used the wubi install file and I only see one partition/drive  while in Windows. I didn't see a option to create a new partition in the  install, but I'm new to Ubuntu (and linux).
With a wubi install you can access your Windows host with this info,

> The Windows partition where you installed Wubi is available as /host  within Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable media from this community documentation [--link--]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?")

Separate partition information previously mentioned is for separate partition dual boot installs, compared to wubi which is Ubuntu installed into a file within the NTFS filesystem.

---

### Post by Dion18 on 2010-10-28
This is actually one of the reasons why I joined this forum. I want  to do the same for my laptop. I don't know if it is possible. I just installed ubuntu and now I know that I can share files. This is very useful for me. Thanks! :KS

---

### Post by sgage on 2010-10-28
I have Windows 7 and Ubuntu on my computer. For email, I just point Thunderbird to the Windows mailstore folder, and symlink abook.mab from Windows to Ubuntu.

For Firefox, I symlink *.sqlite from Windows to Ubuntu.

Rhythmbox can use my iTunes music directory, OpenOffice accesses my documents folders on Windows just fine.

I've been doing it this way for years. It works seamlessly, and sometimes I almost forget what platform I'm on.

---


---
title: "can't move files in host to trash -- prompted to delete permanently"
date: 2011-07-23
forum: General Help
---

### Post by webcomm on 2011-07-23
ubuntu 11.04
ubuntu classic
wubi

When I try to delete a file in the host directory (and sub-directories), I see the prompt, 'Cannot move file to trash, do you want to delete immediately?'

I googled this issue and see some solutions that require editing fstab, but not sure if that's the right approach in wubi, and not so sure what edits I would make in fstab anyway.

---

### Post by bcbc on 2011-07-23
The files in /host are outside of the virtual disk Wubi installs Ubuntu on. So it doesn't make sense for these to be 'deleted' and moved into the virtual disk's trash. If you want to delete them and keep them in the recycle bin, do it from Windows or move them onto the virtual disk first.

Personally I'd recommend keeping your data on the /host and not on the virtual disk as the host ntfs file system is more reliable than the virtual disk.

---

### Post by webcomm on 2011-07-23
> **bcbc said:**
> The files in /host are outside of the virtual disk Wubi installs Ubuntu on. So it doesn't make sense for these to be 'deleted' and moved into the virtual disk's trash. If you want to delete them and keep them in the recycle bin, do it from Windows or move them onto the virtual disk first.

Makes sense.

> **bcbc said:**
> Personally I'd recommend keeping your data on the /host and not on the virtual disk as the host ntfs file system is more reliable than the virtual disk.

Good to know.  I wonder if that's generally agreed, that the virtual disk is not as reliable.

I guess if I keep data on the host but work in ubuntu then I just have to live without the safety of moving things to the trash before deleting.  Hmm.  Not an easy choice.

---

### Post by bcbc on 2011-07-23
> **webcomm said:**
> Makes sense.



Good to know.  I wonder if that's generally agreed, that the virtual disk is not as reliable.

I guess if I keep data on the host but work in ubuntu then I just have to live without the safety of moving things to the trash before deleting.  Hmm.  Not an easy choice.

Personally I've never had a problem with the virtual disk. But if you make a habit of manually powering off your computer, then you can corrupt the virtual disk. Every now and then I see a thread where someone has this problem. So... it doesn't mean it happens to everyone, but if you're worried about your data, then it's best to keep it outside the virtual disk. 

Actually I keep all my important data backed up whether on virtual or physical disks. But I'm probably in the minority.

PS if you use Ubuntu a lot you can drop the wubi install and move to a native install (or [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") the wubi). This is better for long term use. You can still share data between Windows and Ubuntu on an ntfs partition if you need to.

---


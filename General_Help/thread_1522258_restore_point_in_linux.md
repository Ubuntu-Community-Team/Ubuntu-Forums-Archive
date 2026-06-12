---
title: "restore point in linux"
date: 2010-07-01
forum: General Help
---

### Post by Praveen30 on 2010-07-01
As in windows when i suffer the problem i just restore it on some previous date when it was running quite lucid..well is there anything like this in ubuntu and if yes then how to restore it on some previous date as we can do in the windows...

---

### Post by artemyv on 2010-07-02
You can use some backup program like "Simple Backup" - to backup your home and config files... Later ou'll be able to use it again to restore your system state to the point where you made a backup

---

### Post by Praveen30 on 2010-07-02
> **artemyv said:**
> You can use some backup program like "Simple Backup" - to backup your home and config files... Later ou'll be able to use it again to restore your system state to the point where you made a backup


it means there is no option like in window........i can't restore my system on some previous date...

---

### Post by indytim on 2010-07-02
> it means there is no option like in window........i can't restore my system on some previous date...

Not really.

One solution is to use partition level image backup program(s).  If used properly, this will give you restore points. There are 2 apps that are readily available in Debian-based Linux.

Partimage is an old app that has been around for quite some time.  It has a basic GUI that is run from the command level.  It will produce partition images on partitions that are not mounted (i.e.  you cannot image the currently booted partition (there are work-arounds).  The big limitation for Partimage is that it is designed for ext3.  It cannot do ext4 and is considered "experimental" in NTFS.  It is not available in the latest Ubuntu repositories ( I believe because of the ext4 thinger).

fsarchiver is the latest entry (that I'm aware of).  It is capable of imaging ext3, ext4 and NTFS and others.  It is a command line run program, but the structure is pretty straight forward.  It is also bundled with the RescueCD which gives a complete work-around to the currently mounted situation.  Supposedly, fsarchiver will allow imaging mounted partitions (haven't tested it yet).

I'm at work on a Windows machine, so I don't have access to links etc.

Hope this helps.

IndyTim / DataMan

---


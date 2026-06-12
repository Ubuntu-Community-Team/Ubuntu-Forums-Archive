---
title: "mount a NTFS drive as NFS?"
date: 2011-02-18
forum: General Help
---

### Post by dan.povall on 2011-02-18
Hello!

We have a VMware box that is connected to a Thecus. The Thecus FTPS the WMware virtual machines onto a PC which has a 2TB drive.

We are trying to see if we can get the FTP'd VMware Virtual machines to run on another WMware node. 

However Vmware use's NFS so we can't mount the drive as it's NTFS.

We are attempting to mount the NTFS drive in ubuntu. Can this be done and can it be turned into a NFS share without formatting the drive.

I know the question might not make sense, but thats what were trying to do basically.

Thanks,
Dan.:o

---

### Post by dabl on 2011-02-18
I'm not an NFS expert, but my understanding is that both systems to be networked have to be running the NFS host and guest packages, as well as be configured, via static IP addresses, appropriately.  This means, by inference, that both systems must be running Linux (or unix).  I have not read that the filesystem itself (of the share) is limited to Linux filesystems.

Here's the best guide I know of:

[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

---

### Post by apmcd47 on 2011-02-18
I'm confused. You are proposing to smb-mount the PC disk on an Ubuntu system then share it over NFS? It might be possible but I doubt it. It would be easier to install an NFS server on the PC. Just google search for NFS server and Windows.

If you are proposing running Ubuntu on the PC and sharing the disk by NFS I would imagine that is possible.

Andrew

---


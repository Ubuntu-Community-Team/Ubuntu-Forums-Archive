---
title: "Encrypted backups on NFS or SSFS share"
date: 2011-11-28
forum: General Help
---

### Post by brendanpiater on 2011-11-28
Been going around in square circles here so any help and/or suggestions welcome!

**Goal:**

> encrypt my backup data on network server (shared via NFS or SSHFS)
> want the encrypted folder to be transparent to my local machine, i.e work as a normal mounted NFS or SSHFS folder would.
>> This is so that I can keep using "backintime" as a backup tool. It does everything I need except encryption
> The encrypted folder should be mounted automatically on login. E.g. same as encrypted private directory.

*Some notes*
> My home directory is already encrypted, but I don't just want to copy over the encrypted files because then I won't have any version'ing. 
> Tried to use encfs and also Cryptkeeper. Using local folders works fine but when trying to set-up the encrypted folder on the NFS share it fails.
> Running Lucid, 10.04
> I'd like to set this up on all clients on the local network to backup to the same local networked server also running Lucid 10.04.

Thanks in advance.

Cheers
Brendan

---

### Post by brendanpiater on 2011-12-03
Quick bump - thanks for the help.

---

### Post by garolou on 2011-12-16
I don't use encryption so I can't help you in that regards. I have used NFS and I was content with it until I realised that symlinks don't work. My preference is leaning towards SSHFS because it is possible to get symlinks to work. For a home network it seems robust enough.

---


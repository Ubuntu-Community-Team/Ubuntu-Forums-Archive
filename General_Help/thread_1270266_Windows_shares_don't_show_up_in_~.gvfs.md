---
title: "Windows shares don't show up in ~/.gvfs"
date: 2009-09-19
forum: General Help
---

### Post by bburtin on 2009-09-19
When I connect to an SMB share on my NAS, I can browse it in Nautilus, but I don't see it in ~/.gvfs.  Any suggestions about how to diagnose what's going wrong?

```

[~]$ gvfs-mount -l
Drive(0): SCSI Drive
  Volume(0): windows
Drive(1): CD-ROM/DVD-ROM Drive
Mount(0): public on qnap -> smb://qnap/public/
[~]$ ls ~/.gvfs
[~]$ 
```

---

### Post by bburtin on 2009-09-19
Ok, this is crazy.  I rebooted and it started working:

```
[~]$ gvfs-mount -l
Drive(0): SCSI Drive
  Volume(0): windows
    Mount(0): windows -> file:///media/windows
Drive(1): CD-ROM/DVD-ROM Drive
Mount(0): public on qnap -> smb://qnap/public/
[~]$ ls ~/.gvfs
public on qnap
[~]$ ls -ld ~/.gvfs
dr-x------ 3 boris boris 0 2009-09-19 08:23 /home/boris/.gvfs
[~]$ 
```

Not sure which of the things that I did was the one that fixed the problem.  It was either "sudo apt-get install gvfs-bin", making ~/.gvfs writable (although it was reverted back to 500 after reboot, from what I can tell), or rebooting, or some combination of those.

Sorry that I couldn't be more specific with the fix.  If this happens to someone else, hopefully my fumbling will give them some ideas about how to fix the problem.

---

### Post by carlomag on 2009-09-26
I have had the very same problem.
I don't know if my solution is useful, but I rebooted with an older kernel which I have (2.6.15-generic). In that way all was properly working. Then, I rebooted once again with my usal kernel ( 2.6.29-02062906-generic) and now .gvfs is working as well.
I mainly use it with Exaile in order to listen my MP3 collection on a Iomega network disk.
Not brilliant...but it worked.:confused:

Bye

---


---
title: "stumped by stale nfs file handler"
date: 2009-08-27
forum: General Help
---

### Post by fatdaddy on 2009-08-27
I have an situation that requires me to delete a users folder and then replaces it at each boot.  Somehow the tar file that restores the users folder got damaged and i needed to make changes to /etc/rc.local.

When I set the computer up several weeks ago sudo gedit rc.local worked fine.  Now i get 2 errors.  One from the terminal screen with this error --
** (gedit:26270): WARNING **: Hit unhandled case 0 (Stale NFS file handle) in parse_error

Then when i make my corrections i get this error from gedit
Could not save the file /etc/rc.local followed by Unexpected error: Stale NFS file handle.

I am able to work around it using pico  (sudo pico rc.local)

My concern is that there is an underlying problem about to explode.  I have run some disk diagnostics and memory diagnostics and they all check ok. 

And what does stale NFS file handle mean and any ideas to resolve the above would be greatly appreciated.

Thanks in advance

---

### Post by bab1 on 2009-08-27
> **fatdaddy said:**
> I have an situation that requires me to delete a users folder and then replaces it at each boot.  Somehow the tar file that restores the users folder got damaged and i needed to make changes to /etc/rc.local.

When I set the computer up several weeks ago sudo gedit rc.local worked fine.  Now i get 2 errors.  One from the terminal screen with this error --
** (gedit:26270): WARNING **: Hit unhandled case 0 (Stale NFS file handle) in parse_error

Then when i make my corrections i get this error from gedit
Could not save the file /etc/rc.local followed by Unexpected error: Stale NFS file handle.

I am able to work around it using pico  (sudo pico rc.local)

My concern is that there is an underlying problem about to explode.  I have run some disk diagnostics and memory diagnostics and they all check ok. 

And what does stale NFS file handle mean and any ideas to resolve the above would be greatly appreciated.

Thanks in advance

See [_[COLOR="DarkSlateGray"]**here**[/COLOR]_]("http://www.cyberciti.biz/tips/nfs-stale-file-handle-error-and-solution.html").

---

### Post by fatdaddy on 2009-08-27
Well I read the referenced material and tried the dismount, and since it was the system volumne it came up as busy.  So i loaded the ubuntu CD and and mounted and dismounted and mounted the system disk.  Then i went to edit rc.local with gedit and when i went to save it i had the same error stale nfs file handler.  Also I am getting another abnormal action from this computer.  When i do ALT F2 and type in su gedit or sudo gedit I get no response from the system.  Both with or without the run with file.  This is a very locked down system with the user having no privileges at all.  It is used in a detention facility to reference electronic law library and is not on a network and i am the only one with the sudo user password. 

I am at a complete loss.  Come to my aide all you mega beans
PLZ

---

### Post by bab1 on 2009-08-27
> **fatdaddy said:**
> Well I read the referenced material and tried the dismount, and since it was the system volumne it came up as busy.
So i loaded the ubuntu CD and and mounted and dismounted and mounted the system disk.  Then i went to edit rc.local with gedit and when i went to save it i had the same error stale nfs file handler.  Also I am getting another abnormal action from this computer.  When i do ALT F2 and type in su gedit or sudo gedit I get no response from the system.  Both with or without the run with file.  This is a very locked down system with the user having no privileges at all.  It is used in a detention facility to reference electronic law library and is not on a network and i am the only one with the sudo user password. 

One assumes that when you have NFS stale file handles you have a NFS mount somewhere on the system.  But then again the operative word here is ASSUME.  

Confirm that this is a STAND ALONE system (only the one computer).  Are you mounting the "reference electronic law library" data from a cd or some such external device?

A quick guess is that this is a Gnome/Nautilus problem with gedit.  Sometimes gedit does funny things when interoperating with the system directly.  Specifically saving things on remote or secondarily  mounted partitions.  In most of these cases a non Gnome based editor works fine e.g. VIM or nano.

From the CLI provide the output of ```
fdisk -l
```

```
mount
```

```
df -h
```

---


---
title: "Auto-mount SMB shares in Nautilus"
date: 2010-10-27
forum: General Help
---

### Post by gradysghost on 2010-10-27
Folks, I would like to be able to log into my system and have Nautilus automatically mount a handful of Windows shares from around the office.  Is there a good way to do this?  I'm about to start digging through Nautilus's manpages, but I'm short on time this morning.

Thanks in advance!

---

### Post by gradysghost on 2010-10-27
I should clarify that I could use CIFS to actually mount these shares in the fstab, but that requires superuser rights, and I would much rather just automate the Nautilus process.  It's cleaner from a user perspective, and I'm ultimately looking for a way to distribute this functionality *en masse* to several PCs.

---

### Post by Morbius1 on 2010-10-27
There's a couple of ways to do this:

[1] When you browse the network and click on a remote share what nautilus does is execute this command:

```
gvfs-mount smb://server/share
```Now if you have a remote guest share you could simply add that line to the the autostart program:
Preferences > Startup Applications > Add 

If the remote share requires authentication it gets a little more complicated. What you'd like to do is something like this:
```
gvfs-mount smb:username:password@//server/share
```But that really doesn't work outside of the command line. This HowTo shows you how to do that with authentication:
[http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

[2] Gigolo
It browses, automounts, and a whole bunch more. A mini HowTo here:
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

After years of adding lines to fstab to do this sort of thing I now use Gigolo because it dependably automounts remote shares when the remote server becomes available.

---


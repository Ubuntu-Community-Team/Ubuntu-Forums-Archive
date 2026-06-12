---
title: "Mounting shared drives Virtualbox"
date: 2009-11-25
forum: General Help
---

### Post by Gary Nored on 2009-11-25
Still having trouble connecting guest (Win7) to host (Ubuntu 9.1) folders. 
Here's what I've done so far.

Installed Guest Additions
Shared the desired folders on Ubuntu (9.10)
Shared the desired folders in Vbox
Viewed folders in Win7 Explorer

The shared folders appear in the Network section of Windows Explorer. However, when I try to browse them or mount them I get an error msg saying Windows cannot connect to them. 

Any suggestions as to what is broken in this convoluted chain?

---

### Post by falconindy on 2009-11-25
Provided the 'net' command hasn't changed in Win7, its a lot easier to do this from the command line:
```
net use x: \\VBOXSVR\sharename /persistent:yes
```
Just replace sharename with the name you gave to the share and modify the x: to the drive letter of your liking.

---

### Post by Gary Nored on 2009-11-25
Thanks for the suggestion. I tried that and seem to have gotten further along. The drives now show up in explorer as mounted, but when I try to browse them, I get a new error saying that "x: refers to a location that is unavailable."

I tried pinging \\VBOXSVR too with no response. Any ideas?

---

### Post by falconindy on 2009-11-25
VBOXSVR is just an alias that VirtualBox knows about to link your shared folders to the guest. It won't resolve as a real host.

Looks like you're not the only one having problems with Win7 and shared folders.

[http://forums.virtualbox.org/viewtopic.php?f=8&t=13180](http://forums.virtualbox.org/viewtopic.php?f=8&t=13180)

Are you using the latest release?

---

### Post by Gary Nored on 2009-11-25
Solved. The problem was with Samba. Though I'd shared the folders, and they reported as shared through the gui, they weren't. I unshared them, and reshared them, and now they work. 

Thanks again for you help. Without the net command I probably would never have succeeded.

Regards
Gary

---

### Post by falconindy on 2009-11-25
Huh, interesting. You don't need to share them on the host side at all. Samba shouldn't even come into play here. Maybe it had something to do with the handle that VBox uses to share that somehow conflicted with Samba. When you unshared them, VBox "completed" its lock? NFI, glad it's working.

---


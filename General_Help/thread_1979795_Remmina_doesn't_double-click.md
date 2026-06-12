---
title: "Remmina doesn't double-click"
date: 2012-05-14
forum: General Help
---

### Post by prowla on 2012-05-14
I've just upgraded from Ubuntu 10 to 12, and I use it within a VMware player VM to give a canned environment through to some systems (UNIX, Linux and Widnows) that I support.

One of the changes with Ubuntu 12 is the shift from tsclient to Remmina for remote desktop access to Windows servers. It's mostly fine, but there is one issue.

Double-clicking isn't working on the remote desktop. For example, if I double-click on the remote desktop's "My Computer" it just highlights the icon instead of opening a window. But if I right-click and choose "Open" from the popup menu then the window opens as normal.

I double-checked that it wasn't a setting on the remote machine; I ran up my old Ubuntu 10 VM on my same host PC and connected in with tsclient (which took over my session from my Ubuntu 12 desktop), and double-click worked fine.

So it looks like this does relate to Remmina on Ubuntu 12.

Have I missed a config, is there a bug, Is this expected behaviour?

Thanks for looking...

---

### Post by dcstar on 2012-05-15
> **prowla said:**
> 
..........
So it looks like this does relate to Remmina on Ubuntu 12.

Have I missed a config, is there a bug, Is this expected behaviour?

Thanks for looking...

Check this:

[https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522)

---

### Post by prowla on 2012-05-15
> **dcstar said:**
> Check this:

[https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522)Thanks for the info.

That's not my specific issue, but I could chuck that into the mix too...

regards,
Paul

---

### Post by prowla on 2012-07-12
FYI I did an update of Ubuntu 12 recently, and it now looks like works, so I guess the fix was included.

---


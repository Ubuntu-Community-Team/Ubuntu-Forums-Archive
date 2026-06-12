---
title: "Samba acting quirky"
date: 2010-11-18
forum: General Help
---

### Post by snorkytheweasel on 2010-11-18
I have 2 ubuntu machines running Samba. One recognizes my windows network shares, the other doesn't. They sit side-by-side - same subnet, same windows domain, both using Dolphin as a file manager.

[LIST=1]
[*]One is old and tired (the hardware, not the OS) and needs to go to the recycling bin. It's running Gutsy (after upgrading from Breezy).
[*]The other is fairly new, much faster, and the proud possessor of a big hard drive - which is what it needs, since it operates primarily as a file server. It runs Maverick.
[/LIST]
The problem is that 
[LIST]
[*]_On the old machine_, Samba sees all of the windows domains and sees all of the Windows shares on each. I must have tweaked that one correctly. 
This old one even sees the new computer in the appropriate Windows share.
[*]_On the new one_, Samba sees only one windows domain, and sees no shares - other than itself - on that one windows domain.
[LIST]
[*]I've tried tweaking smb.conf, but nothing I've tried works.
[*]I copied the functioning smb.conf from the oldie-but-goodie to the newbie, but the result is the same: Samba sees one windows domain, and sees no shares on that one windows domain.
[/LIST]
[/LIST]

The functioning smb.conf.txt is attached. I had to change the name to get the forum software to accept it (pretend the ".txt" isn't there.)

**NOTE: This is cross-posted from the Networking forum. In that forum it got lots of views, but 0 answers.**

---

### Post by papibe on 2010-11-18
> **snorkytheweasel said:**
> ...
They sit side-by-side - same subnet, **same** windows domain, ...

The problem is that On the old machine, Samba sees **all** of the windows domains and sees all of the Windows shares on each....
...
On the new one, Samba sees **only one** windows domain, and sees no shares - other than itself - on that one windows domain.


I'm a little confused. Are you sure they are both in the same domain?  if so, what are the other domains use for? 

Regards.

---

### Post by snorkytheweasel on 2010-11-20
Why so many domains?

My organization manages / supports networks for 2 school districts, a city, and a county. We also have a separate highly secure domain for that city's police department. The 6th domain is for testing.

Multiple domains is not unusual with large, diverse companies. When a forest is set up properly it's simple to set up trusts within and across domains. 

None the less, I can say with 100% certainty that they are in the same domain, same subnet [I know because 1) I set them up, 2) I checked the IPs].

There are 2 ubuntu machines, same domain, same subnet. At this point in time they have an identical smb.conf. Previous tweaks on the smb.conf failed.

The one that works properly is running karmic. It has never given a bit of trouble. But for many reasons I have to take that hardware out of service. Per my boss's instructions, I can't reuse the old disk. It has to get a DOD disk wipe and then go to recycling.

As a last resort I can try using clonezilla to ghost the old  the system's disk and restore it into the new one. But I don't look forward to telling my boss why I'm using a version that is 6 releases old. I could use Fedora or CentOS (we are using both). But I really prefer Ubuntu.

---

### Post by papibe on 2010-11-20
I see. Your network's complexity is way beyond my home network.

I don't know if this is going to help, but I took a look of your smb.conf and I have a couple of comments:

[LIST=1]
[*]If both servers have the same smb.conf, be sure the share dirs are the same on both servers.
[*]You use the option security=domain. I haven't found detail info on that opttion, but for me security=user always has worked fine.
[/LIST]

BTW, it's easier to read your samba configuration using the testparm command (it just prints the 'on' options of smb.conf).

---

### Post by dry_egg on 2010-11-20
thank you!

---


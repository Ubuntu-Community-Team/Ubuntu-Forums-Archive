---
title: "Giving Permission to Apps to Access Hard Drives"
date: 2009-12-31
forum: General Help
---

### Post by I Forgot My Username on 2009-12-31
Related to VMware, posted here because question is focused on general access/rights.

I'm using VMware to simultaneously boot Linux/Windows but Linux is blocking VM's access to the hard drive(partitioned).  How do I grant permission for VM to access /dev/sda1(actually, it blocks all of sda, but I'm only interested in sda1)?  Any help appreciated, thanks.
[edit]
More info,
/dev/sda1/ is mounted
[/edit]

---

### Post by 3rdalbum on 2009-12-31
A virtual machine does not directly access your local hard disks. That would be a Very Bad Idea :-)

What you need to do is mount your hard disk in the host operating system (Linux), set up Samba file sharing in the host for this hard disk, and then access the share in the guest operating system (Windows).

I believe VMware can also do a "shared folder", which is where a folder on the host also becomes virtually shared with the guest. So, the guest sees it as a Samba share, and the host sees it as a regular folder. For more information on this, consult the manual for your VMWare program.

---

### Post by I Forgot My Username on 2009-12-31
I'm aware of what **could** happen, all I need to know is how to give VMware access to the hd.  It's actually an accepted use of a virtual box [http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html#wp1046601](http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html#wp1046601).

Thanks for the warning though.

---

### Post by 3rdalbum on 2009-12-31
Apparently your user account needs to be a member of the "disk" group - you can do this in System > Administration > Users And Groups. Click the key icon to authenticate yourself, click the Manage Groups button, click the Disk group and click Properties. Now tick the box next to your name, log out and log in (and make sure you're logged out of all VTs too), and Vmware should be able to access whatever partitions you want.

As far as I can tell from that thing that you linked to.

---

### Post by I Forgot My Username on 2009-12-31
Well, this sucks, but you were right, about a hour in, I got the blue screen of death:(:(:(.  To get it to access the hd I just used "sudo vmware", wouldn't recommend trying it though:(.  If I did it right, I attached a png of Vista trying to fix itself.

---

### Post by gnomme on 2009-12-31
I also think that it is not possible to do...

---

### Post by I Forgot My Username on 2010-01-01
It's possible(see pic above), but I defiantly wouldn't recomend it.  Turns out Windows was fine though, I had to reboot about a hundred times and it magically fixed itself.  I'm serious, after running Window's Recovery, I booted, it would start to boot but reboot half way in.  It eventually booted just like normal.  It was doing that before, though.

---


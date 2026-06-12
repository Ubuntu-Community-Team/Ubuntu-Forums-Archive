---
title: "Palimpsest and RAID"
date: 2009-12-13
forum: General Help
---

### Post by Joshua on 2009-12-13
I just noticed the Palimpsest Disk Utility has an option for supporting RAID array manipulation.  Does anyone know how it does it?  Is the software built in or does it use a different package?

I'm mostly just wondering if it is stable.  I used to use mdadm and didn't know there were any other options for software RAID.  I flipped through the packages and it looks like it's the GNOME Disk Utility, but I couldn't find a dependency for mdadm.

I'm using 9.10.

---

### Post by Joshua on 2009-12-14
Wow.  I'm suprised I didn't get a response to that today.  I have a more general question that might help me figure this out myself.

Does anyone know who develops the Palimpsest Disk Utility or what the package name is?  As I said in my first post, there is a GNOME Disk Utility in my package list, but I can find any web references to Palimpsest from a GDU site.  I also can't really find ANY info on a disk utility called Palimpsest (other than the completely unrelated Wikipedia pages).  It seems strange that a relatively undocumented package would be included in a default Ubuntu distro.  So I feel like I must be missing something pretty obvious.

---

### Post by kubug on 2009-12-19
All I could find out about it is that it is a Fedora/Red Hat sponsored project, part of their DeviceKit package. 

[http://fedoraproject.org/wiki/Features/DeviceKit]("http://fedoraproject.org/wiki/Features/DeviceKit")

I would wait with using their RAID feature unless it's data you don't mind loosing. Mdadm has been around for long enough and has proven itself.

---

### Post by Joshua on 2009-12-19
That sounds like good advice.

I'm still really surprised it's so hard to find detailed info on a package that is installed by default.

---

### Post by srf21c on 2009-12-21
> **Joshua said:**
> I'm still really surprised it's so hard to find detailed info on a package that is installed by default.

Agreed.  Reminds me of how hard it was to dig up any decent documentation for the Gnome Vino VNC server a few years back.

---

### Post by crysys on 2010-04-18
If anyone is still curious Palimpsest seems to use mdadm.  I found this out because I did not have mdadm installed and the creation of a software RAID 5 failed for that reason.  Of course, now that mdadm is installed the creation of the RAID 5 is just quietly failing. :confused:

This is on karmic.  I'll probably do a clean install of lucid soon and try again.

---

### Post by kubug on 2010-04-19
It's probably not creating the /etc/mdadm/mdadm.conf file properly.

Did you try creating/starting the RAID 5 manually first, to see if it works?

---


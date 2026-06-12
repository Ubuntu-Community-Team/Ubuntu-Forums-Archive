---
title: "Is there a Linux solution to fixing the mbralign problem on existing (in use) drives"
date: 2012-03-21
forum: General Help
---

### Post by greavette on 2012-03-21
Hello,

We use Virtual Machines in our small office to host some Ubuntu and Windows (2003) servers and some XP desktops.  I've recently learned of the performance issue that can be had if the mbr is not aligned properly when the VM was created.  

Is there a Linux solution to this problem on moving the offset of an existing VM without losing data.  I don't want to rebuild my VM's unless I have too.

I know of utilites such as NetApp's mbralign tool and an ESX solution (we don't use ESX, Still using VMware Server at the moment).  I don't know if I can use NetApp's solution since we don't use NetApp in our office for Storage.

Just curuios if there is a Linux Live CD we can use to fix this for us on our existing VM's?  Any links to how to do this would be greatly appreciated.

Thank you.

---

### Post by greavette on 2012-03-25
Hello,

I've found this post (a few years old now) that details how to use GParted to clone from disk to SSD and fix the mbralign:
[http://www.ocztechnologyforum.com/forum/showthread.php?60340-cloning-HDD-gt-SSD-*with-alignment*-quickly-with-GParted](http://www.ocztechnologyforum.com/forum/showthread.php?60340-cloning-HDD-gt-SSD-*with-alignment*-quickly-with-GParted)

Can anyone give details on how I would do this for my VM's (I'm using VMware Server 2.0).

Thank you.

---

### Post by greavette on 2012-03-25
Okay...here's a few thoughts I'll look further into...

Since the drives I'm trying to fix are virtuals anyway, I may as well think of doing a V2V where before I move the virtuals over, I fix the mbralign first.

Ideally I would like script this solution and make it as automatic as I can.

There are two products that come to mind initially from a Windows solution (since my VM's are hosted on Windows PC's):

[Driveimagexml]("http://www.runtime.org/driveimage-xml.htm")
[http://odin-win.sourceforge.net/]("http://odin-win.sourceforge.net/")

Both of these tools let me create scripts for backup and restore.

What does the community think of using these?

---


---
title: "Need a bit of help in vboxusers group please!"
date: 2011-09-23
forum: General Help
---

### Post by hcforde on 2011-09-23
[B][SIZE=2][SIZE=1]I am quite proficient in Windows but here I am totally lost.  I have been able to set up UBUNTU 11.04 and added the 4 Windows 7 guest I need.  I now need to enable USB capability.  I found the instructions (see below) but havent a clue as to what they are talking about when they say "add yourself to the vboxusers group"  I got to that area and was lost.  Do I add the names of each Virtual Machine as it is seen in the VirtualBox manager?  OR, Do I add the login name of each windows VM? OR is it something else?  The last thing at this point I want to do is break this and not know how to go about fixing it.    [/SIZE]    [/SIZE]
[/B]

**For Natty Narwhal**

 Add yourself to the user group vboxusers, then log out and back in, to make use of available USB devices. To do this via the graphical interface, click System Settings/Users and Groups/Manage Groups.

---

### Post by magic8ball on 2011-09-23
I did this awhile back and was initially confused also.  I'm going from memory because I'm not at my Ubuntu machine right now, but I think that I double-clicked on the vboxusers group (in Users and Groups) and then selected the check-box next to my username to add myself (or did whatever it took to put my username in the member list).  I haven't done much with VirtualBox since, but I believe that you only need to do this one time to cover everything.  Hopefully that gets you closer.  Good luck.

Edit:  When I say username, I mean your Ubuntu login username.

---

### Post by hcforde on 2011-09-23
OK, I think I got it.  The usb devices do show up now and I can select them.  The next issue is assigning different sound devices to each virtual machine.

---


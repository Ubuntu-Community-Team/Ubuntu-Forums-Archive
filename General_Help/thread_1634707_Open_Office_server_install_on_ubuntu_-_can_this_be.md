---
title: "Open Office server install on ubuntu - can this be accessed by windows PC's too?"
date: 2010-11-30
forum: General Help
---

### Post by greavette on 2010-11-30
Hello,

I'm wondering if someone can confirm if this is even possible:

Install OpenOffice network installation on Ubuntu (server or desktop).
Run OpenOffice from our Windows PC's connected to our network.

I've read of a way to install OpenOffice on linus as a server install.  Then from each workstation, run the command:

/usr/local/openoffice60/program/setup 

and I think this will allow each workstation to use OO.  

So what I'm looking to do is to use OO from Ubuntu and share it with my windows PC's.

I know I could install it on a Windows server and probably use Terminal Services, but I'd much rather use Ubuntu/Linux.  Can applications be shared from Ubuntu to Windows through something like Terminal Services.

Thanks in advance for any help you may provide.

---

### Post by efflandt on 2010-11-30
Just one problem.  Linux binaries (programs) do not run in Windows.

Although, if there is a way to set that up with Windows binaries on a Windows server, there is likely a way to set that up somewhere in Linux using samba.  That might be easiest if the computer can dual boot Windows and you could do the OO Windows server install on that drive.  Then mount and share it from Linux.  Although, it may not be very fast loading from a network unless your network is fast.

---


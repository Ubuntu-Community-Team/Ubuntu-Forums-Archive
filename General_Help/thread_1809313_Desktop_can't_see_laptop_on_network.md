---
title: "Desktop can't see laptop on network"
date: 2011-07-21
forum: General Help
---

### Post by country0129 on 2011-07-21
I have samba running on Ubuntu 11.04 Laptop box. I can see and access all the Win7 x64 Professional desktop shared folders from the Ubuntu box. When I try to browse the network from the Windows 7 Professional X64 Desktop file browser, the Ubuntu Laptop doesn't even show up. Both are in the same work group. Mapping the network brings similar results.  Both have shared folders and drives.  I can ping the Ubuntu box from the command line from Win7. I typed \\192.168.1.45 (the laptop's router address) from the RUN command. It said the laptop wouldn't allow connection. Samba shares are set for "visible" & "writable." The user name is set for my access; yet no joy.  I ran the Win7 trouble shooter, and it said that my $Print share folder wouldn't accept connection. I deleted that share; yet still no joy. 

 HOMEGROUP is the name of the Home Network on both machines. User names and passwords the same. Windows firewall disabled. Norton firewall set to allow the laptop.  I don't think the firewall on Ubuntu is causing it. I installed UFW and GUFW to Ubuntu for graphical interface  with networks. Opened GUFW and the "ENABLED" check box isn't. So it  isn't running, is it? Everything about the firewall is default. I've  never enabled it.   Firewall on router  disabled.   Both machines access the internet. Both machines can ping the other. But Windows 7 does not see my Ubuntu laptop on my network. 

Also, if this may have something to do with it, when I boot up or reboot, I had a message, "Can't update .iceauthority."  I've googled this to try to find a fix, and am “THINK” I fixed it. Somehow, Ubuntu changed the name of the owner of “HOME/USER”  to "root/user.   I repaired that.  Still no joy.  Can this have any coincidental effect by being related to one another?

 BTW, Ubuntu 11.04 is 32 bit on a Gateway laptop. Win7ProX64 on an HP desktop. Desktop LAN to Linksys DSL router supplied by ISP (wireless capable). Laptop to router via wireless. 

Realize this isn't a Windoze forum, but perhaps someone has solved this problem and can help?

 I solicit all suggestions!
 
 Thanks,
 

 Baldheadedbecauseofpullingoutmyhairforaweek!

---

### Post by galvatron408 on 2011-07-22
if you want to browse your ubuntu laptop, you need to have some sort of server. :|

Here's the ubuntu help page for it.

[https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

---


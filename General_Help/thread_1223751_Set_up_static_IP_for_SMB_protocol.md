---
title: "Set up static IP for SMB protocol?"
date: 2009-07-26
forum: General Help
---

### Post by gksudo on 2009-07-26
Hello,
I need help on assigning static IP addresse(s) for  SMB[samba] network..
Because, if the power goes out and the computers reboot, the smb addresses change based on boot order(Or which machines connect to the network first.) in the network. 
Any help would be much appreciated. Thanks:D

---

### Post by DaithiF on 2009-07-26
what OSs are these machines running -- windows, ubuntu, other?  The steps to assign static IP addresses rather than dynamic will vary across these.

In ubuntu, goto to network manager, edit your connection, and in the IPv4 tab, rather than Automatic DHCP, choose manual and enter the relevant details.

For windows I can't tell you the exact steps as I'm not at a windows pc ( thankfully! :) )
but its something like Network connections -> TCP/IP settings, and somewhere in there is a tab with option buttons to toggle between DHCP / dynamic IP and Static.

cheers

---

### Post by gksudo on 2009-07-26
Thanks, However I already figured out not long before you posted that,
I still appreciate it anyway.(But now that you have posted that, I know I done it correctly :) )
God Bless.

---


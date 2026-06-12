---
title: "VmWare shared folders(both host and guest are Ubuntu)"
date: 2006-05-31
forum: General Help
---

### Post by seth0x2b on 2006-05-31
Hey guys.
I have Dapper on my box, and I installed a version of Hoary as a VmWare guest(it migh look pointless, but it's not :) )
My question is this: is the VmWare "Shared folders" option possible between Ubuntu host and Ubuntu guest?!, and, if so, how would I achieve this kind of setup?
I know samba is probably the best way to go, but I tried for about 4 hours to set it up, and I couldn't find a solution. I use "Shared Folders" with the WindowsXP guest and it works just fine. Plus, I'll have no open ports on the host, so that's even better

Thanks in advance.
Cheers

---

### Post by mbeierl on 2006-06-01
I have shared folders working on my unix vmwares and it is better (faster) than smb for certain operations.  The best thing about it is that is does not actually use the network.

'Nough said: how to get it to work?

Install the vmware tools rpm.  There's a menu item for that "VM->Install VMware Tools"  All this really does is mount the vmware ISO image as your CD rom.

Mount the CD (if not automounted).

[FONT="Courier New"]mount /media/cdrom[/FONT]

Use alien to install it:

[FONT="Courier New"]alien -i /media/crom/VMwareTools-5.5.1-19175.i386.rpm[/FONT]

Next, start the vmware tools:

[FONT="Courier New"]/etc/init.d/vmware-tools start[/FONT]

Check to make sure the shared filesystem module is loaded:

[FONT="Courier New"]lsmod | grep vmhgfs[/FONT]

If not, load it:

[FONT="Courier New"]modprobe vmhgfs[/FONT]

Then you should have a new filesystem under /mnt/hgfs, which contains your shared folders.

Hope this helps!

---


---
title: "PXE boot server &amp; client"
date: 2011-08-06
forum: General Help
---

### Post by Al Grant on 2011-08-06
Hi All,

I want to use my full Ubuntu install as a PXE boot server for other computers.

The aim is to get the client computers into a basic Linux/Ubuntu shell with access to various util commands such as sfdisk, fdisk, ntfsclone and probably a few others (sshfs comes to mind as I type this)

The client computers do not need Xwindows of any sort. Just shell and preferably boot as fast a possible without user intervention until a command prompt.

I have seen guides on setting up Ubuntu as a PXE server, but not sure;

a) what variant of Ubuntu/Linux is best for the clients
b) how to make the pxe server, serve up whatever variant is suggested in (a).

Please help,

Thanks

-AL

---

### Post by paulmaidment on 2011-08-18
Hi Al,

I run my PXE server via a virtual machine, and use /etc/fstab entries to make some smbfs mounts to the NAS where the installers are stored. This obviously has two benefits

1) I can play around as much as possible as I can merely roll back if I break something.
2) For safety I can store the VM image on my NAS (which has RAID) 

I followed this guide, it's awesome :)
[http://www.howtoforge.com/ubuntu_pxe_install_server](http://www.howtoforge.com/ubuntu_pxe_install_server)

All the versions of ubuntu I have seen have a netboot method, so a lot of this is down to preference. You should be aware that sometimes your NIC may not be supported once the kernel is up. If this happens, the netboot installer will not be able to connect to the ubuntu servers.

An alternative method is to boot from netboot initially and then supply the location of a samba or nfs share where you have the installation files, I am a little sketchy on this, so any community advice on this would be useful.

I hope this helps

---


---
title: "Synaptic package manager???"
date: 2010-07-05
forum: General Help
---

### Post by koldphlame on 2010-07-05
When i press reload this happens 

Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

How do i fix this?

I was messing around and now this 

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/Release](http://download.tuxfamily.org/3v1deb/dists/feisty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2010-07-05
> Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

How do i fix this?

Open **System > Administration > Software Sources** and un-tick the box that says CD-Rom in the first window and then reload.

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org)  feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9


Go to the second page with the tag **Other Software** and un-tick the box with **TuxFamily** and **Feisty** in it and then reload.
If that doesn't work,open a terminal and post output of ```
cat /etc/apt/sources.list
```

Good Luck

---


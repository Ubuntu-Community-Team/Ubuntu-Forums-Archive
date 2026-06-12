---
title: "Applications Menu not getting updated"
date: 2010-10-01
forum: General Help
---

### Post by Gaf the Horse on 2010-10-01
I've installed Ubuntu 10.04 on my laptop using WUBI to preserve my Windows XP installation. I plan to use it for work so have installed our VPN client and a desktop sharing application through a .sh script and a .deb package respectively.
The Applications Menu was updated with the submenu and icons for the new applications and I copied thm to the desktop as well. However when I log out and log back in again my menus and desktop have reverted back to what they were before, and my icons have disappeared.

Any ideas? Have I got a read only file somewhere?

---

### Post by Gaf the Horse on 2010-10-03
I've reinstalled Ubuntu using WUBI, but still getting the same problem.

To restate my problem;
Open a terminal, cd to Downloads and sudo -s to work as root.
Run my install shell script ./vpnsetup.sh.
VPN client is installed correctly, a new icon is now available in the Applications Menu, Internet submenu.
Log off and log back on again, and the icon has disappeared.

---

### Post by wojox on 2010-10-03
Why are you switching to root to run this script? Won't *sudo* work?

Where did you get the shell script from?

---

### Post by Gaf the Horse on 2010-10-03
Hi,

Got the vpnsetup.sh file from my employer (Oracle). I'm planning to use Ubuntu on my work laptop, (finally get away from Windows). We use Oracle Enterprise Linux on the servers at work, but that's not really user friendly enough for me, hence the plan to use Ubuntu. Oracle provide this .sh script for any flavour of Linux.

I was using sudo -s as that's what I've got into the habit of using on  the Linux servers. However I also tried sudo ./vpnsetup.sh, which  installed the vpn client and added the icon to the Applications Menu,  however again when I restarted the icon disappeared.

However I was also getting the same issue with other non-Software Centre installs. One called NoMachine NX ([http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)), does the same. Anything installed via the Software Centre works correctly.

I'm also using a DELL docking station for my DELL D620 laptop. Could this have any impact?

I found this link that seems to describe similar behaviour. Do you think they might be linked?

[http://www.google.com/support/forum/p/Chrome/thread?tid=0314b8bf7294b589&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=0314b8bf7294b589&hl=en)

Thanks.

---

### Post by Gaf the Horse on 2010-10-03
OK, getting weird now. I've just tried installing the NX client again, and have restarted twice, and the icons are all now staying out between reboots. No idea what is going on here, but I guess my problem is no longer a problem :-)

If it happens again I'll restart the thread.

---


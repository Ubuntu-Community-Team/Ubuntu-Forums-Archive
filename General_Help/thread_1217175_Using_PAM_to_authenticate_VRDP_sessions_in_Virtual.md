---
title: "Using PAM to authenticate VRDP sessions in VirtualBox"
date: 2009-07-19
forum: General Help
---

### Post by metacell on 2009-07-19
Hi,

I'm running SUN VirtualBox v3 (non-free) on Ubuntu Server v9, and am trying to use the virtual machines remotely in a secure manner.

I have followed the instructions at <https://help.ubuntu.com/community/VirtualBox/RDP> and enabled the External authentication method on the virtual machine, but I still can't connect to it.

Using the Windows remote desktop client (mstsc.exe) tells me that the remote desktop session has been terminated.

Using the command

[FONT=Lucida Console]rdesktop vboxhost -u myusername -p -[/FONT]

in Linux opens up the rdesktop window, but it is completely black.

Any ideas of where the problem might lie?

EDIT: Subsequent attempts to connect time out, both from Windows and Linux.

EDIT 2: When I started the virtual machines using VBoxHeadless, I was able to connect without even supplying a password.

---


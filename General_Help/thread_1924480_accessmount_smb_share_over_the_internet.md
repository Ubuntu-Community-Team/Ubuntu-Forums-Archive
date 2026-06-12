---
title: "access/mount smb share over the internet"
date: 2012-02-12
forum: General Help
---

### Post by hg088 on 2012-02-12
im aware of the security issues

i can access shared folders on my main ubuntu rig from other computers in my private lan

i tried to forward some port to the computer with the shared folder but that didnt work

---

### Post by Derek Karpinski on 2012-02-12
vpn? ssh?

---

### Post by papibe on 2012-02-12
The easiest way to get access to your home network would be to set up a ssh server on the Ubuntu machine, and open and forward the ports on the router.

In order to access your files from the Internet you can use Filezilla or WinSCP from Windows. From a remote Linux host you can also use Filezilla or even Nautilus itself (using the url sftp://).

There's even a Firefox addon called FireFTP that works great in any platform.

Hope those ideas help. Tell us if you need more details on that.
Regards.

---


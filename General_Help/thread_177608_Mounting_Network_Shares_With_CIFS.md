---
title: "Mounting Network Shares With CIFS"
date: 2006-05-16
forum: General Help
---

### Post by Cadeucean on 2006-05-16
Hello All,

I am using Kubuntu breezy on one of my work computers. I have successfully mounted a drive on my other(winxp) and configured in in fstab to automatically be mounted on startup. 

Now I am trying to mount my remote shares on the server in the same way. When I boot up there is an icon on my desktop for the share but when I click on it I get an "only root can mount //server/share" error. If I open a terminal and type 'sudo mount -a' I get:

mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

the mount.cifs man page doesn't seem to tell me anything about this error or why permission would be denied to the root user.

I can access these by clicking on the "System Menu" applet in the taskbar and selecting "remote places" but this doesn't allow me to open the remote files from within an application. 

I have also tried to use smbfs but I get the "SMB signing is mandatory and we have disabled it." error and from looking around these and other forums it looks like smbfs is just not compatible with certain versions of windows and there is no way to correct that error if it happens.

Anyone have any ideas?

---

### Post by jferrando on 2006-05-17
This is the way works for me:

#!/bin/bash
#Mount samba filesystems
echo "Mount samba filesystems"
echo -n "User: "
read username
echo -n "Password: "
read -s password
mount -t cifs //server.domain.com/data /home/jferrando/data -o username=$username,password=$password,uid=jferrando,gid=jferrando

The uid and gid overrides are necessary if you are using a Samba server with unix extensions enabled.

---


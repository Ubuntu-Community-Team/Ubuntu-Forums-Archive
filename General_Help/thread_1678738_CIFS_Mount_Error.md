---
title: "CIFS Mount Error"
date: 2011-01-30
forum: General Help
---

### Post by ViperX883 on 2011-01-30
Hi All,

I'm running Ubuntu 10.04 on a VM and I'm trying to automatically mount two shares from the Windows Vista SP2 host.  Currently this is failing with the message "mount error(112): Host is down".

I recently upgraded VMWare Server.  Before the upgrade I was able to mount shares without a problem.  I can still mount shares on the host using the builtin "Connect to server" feature in Gnome.  The problem I'm running into is mounting shares via the command line or via fstab.  The relevant lines from my fstab are below.

Just a couple notes: the IP address of the host is static on the virtual network, so using the IP address as the server name should not be an issue.  Also, I am able to ping the host fine (which obviously must be true for me to mount using the Gnome feature).

//192.168.206.1/Chris  /home/chris/Windows/Chris  cifs credentials=/etc/samba/smbcred,uid=chris,gid=chris,file_mode=0664,dir_mode=0775 0 0

//192.168.206.1/Public /home/chris/Windows/Public cifs credentials=/etc/samba/smbcred,uid=chris,gid=chris,file_mode=0664,dir_mode=0775 0 0

I'm certain this is user error, so I apologize in advance for my ignorance.  Any ideas that could point me in the right direction would be great.  Thanks for the help!

Chris

---

### Post by ViperX883 on 2011-02-01
Anyone?  I'm at a loss.  My continued toying is yielding no results at all, and Google hasn't been much of a help.

---

### Post by ViperX883 on 2011-02-01
Never mind all, it's mysteriously working again.  I don't know what the issue was.

---


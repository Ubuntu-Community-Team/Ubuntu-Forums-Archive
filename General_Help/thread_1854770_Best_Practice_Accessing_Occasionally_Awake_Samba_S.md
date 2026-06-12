---
title: "Best Practice Accessing Occasionally Awake Samba Server"
date: 2011-10-05
forum: General Help
---

### Post by kuchera68 on 2011-10-05
I have been using Ubuntu for a little over a year now, and have really enjoyed migrating my main operating system on two PC's to Ubuntu 11.04. I also have built my own NAS server using Ubuntu Server and Samba. One thing I have incorporated into my NAS is the ability to check the network for activity and put itself to sleep in order to save on the electricity. 

While my previous Windows operating systems (and current VirtualBox VM's) deal quite well with mapped network drives that are no longer available, I am at a loss to understand what the best practice is for mounting these Samba shares in Ubuntu. I have tested both mount.cifs and gvfs-mount (using the instructions from [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)) which both provide the necessary access to the files. 

My question is, how are the mounted drives handled when my desktop pc goes into standby, and comes back out? What if the NAS is no longer awake, and the drives cannot be accessed?

I have noticed at least one problem with the gvfs-mount method when the NAS server is suspended. When I attempt to open the file manager through the launcher it just blinks and does not start. The only way I can get into the file manager is to either wake the NAS or issue the gvfs-mount -u command for all drives.

A share mounted through the mount.cifs command does not seem to make the file manager unresponsive. Is this a bug, or is this just the natural affects of using gvfs-mount? Could anyone lend any insight on perhaps the best practice for mounting Samba drives that are not always accessible?

Thanks!

---


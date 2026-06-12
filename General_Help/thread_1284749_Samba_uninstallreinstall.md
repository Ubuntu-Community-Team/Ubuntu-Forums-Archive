---
title: "Samba uninstall/reinstall"
date: 2009-10-06
forum: General Help
---

### Post by JimiGoth on 2009-10-06
I have a printer off my Ubuntu 9.04 box that I was sharing with other Windows boxes in the house via Samba.  However, I deleted the one entry in the Samba configuration GUI for sharing the printer, and could not figure out how to get it back.  After hunting for a few hours, I gave up, uninstalled Samba, then attempted to re-install (when I had first installed it, it set up the printer with no problem.)

Unfortunately, when I try to reinstall, I get an error.  Now I've dipped into the command line, read the man pages on apt, apt-get, ran "sudo apt-get purge samba", but still if I so 'find / -name "*smb*"' I still see a lot of samba looking stuff.  Tried various varieties of this (after trying it with Synaptic and rebooting), but after a few hours I have about given up.

The error is: (there is no smbd running when I try this)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5071kB of archives.
After this operation, 13.7MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 109386 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.3.2-1ubuntu3.2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up samba (2:3.3.2-1ubuntu3.2) ...
Generating /etc/default/samba...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'd appreciate any ideas here... thanks.

---


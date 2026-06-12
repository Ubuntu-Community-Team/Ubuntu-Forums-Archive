---
title: "Proto Not found error and exit status 127"
date: 2010-05-04
forum: General Help
---

### Post by toscal on 2010-05-04
I'm running Ubuntu 9.10 Karmic and XBMC Live.
I get error messages which seem to relate to openvpn.
So I tried to remove it with the remove command. This is what I get
> 
@XBMCLive:/home$ sudo apt-get remove openvpn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  openssl-blacklist libpkcs11-helper1 openvpn-blacklist
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  openvpn
0 upgraded, 0 newly installed, 1 to remove and 26 not upgraded.
1 not fully installed or removed.
After this operation, 1,204kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 54358 files and directories currently installed.)
Removing openvpn ...
/etc/default/openvpn: 1: proto: not found
invoke-rc.d: initscript openvpn, action "stop" failed.
dpkg: error processing openvpn (--remove):
 subprocess installed pre-removal script returned error exit status 127
/etc/default/openvpn: 1: proto: not found
invoke-rc.d: initscript openvpn, action "cond-restart" failed.
/etc/default/openvpn: 1: proto: not found
invoke-rc.d: initscript openvpn, action "restart" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 openvpn
E: Sub-process /usr/bin/dpkg returned an error code (1)
@XBMCLive:/home$ 

Any clues
I have installed firefox, which went ok, and the synaptic package manager, and the current asobe flash plugin for firefox.
Any ideas.

---

### Post by toscal on 2010-05-08
I ended up doing a fresh install. And everything now works fine.
Odd since I didn't do anything differently the second time.

---


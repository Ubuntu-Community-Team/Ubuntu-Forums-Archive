---
title: "Please help with samba"
date: 2011-01-22
forum: General Help
---

### Post by JeffElkins on 2011-01-22
Please help. I'm using 10.04 and samba **will not install**.

Is samba4 now the default? 

This is driving me nuts. Any help appreciated.


```

$ samba
The program 'samba' is currently not installed.  You can install it by typing: sudo apt-get install samba4

```

```

sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: libwbclient0 (= 2:3.4.7~dfsg-1ubuntu3) but 2:3.4.7~dfsg-1ubuntu3.2 is to be installed
E: Broken packages

```

---

### Post by Smart Viking on 2011-01-22
try
```
sudo apt-get install samba4
```

---

### Post by garvinrick4 on 2011-01-22
#Using desktop I have these 2 packages installed to create samba shares:  Version Natty 11.04
```
rick@rick-HP:~$ aptitude show samba
Package: samba                           
New: yes
State: installed
Automatically installed: no
Version: 2:3.5.6~dfsg-3ubuntu3
Priority: optional
Section: net
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 23.7 M
Depends: samba-common (= 2:3.5.6~dfsg-3ubuntu3), libwbclient0 (=
         2:3.5.6~dfsg-3ubuntu3), libacl1 (>= 2.2.11-1), libattr1 (>= 2.4.41-1),
         libc6 (>= 2.8), libcap2 (>= 2.10), libcomerr2 (>= 1.01), libcups2 (>=
         1.4.0), libgssapi-krb5-2 (>= 1.8+dfsg), libk5crypto3 (>= 1.6.dfsg.2),
         libkrb5-3 (>= 1.8+dfsg), libldap-2.4-2 (>= 2.4.7), libpam0g (>=
         0.99.7.1), libpopt0 (>= 1.16), libtalloc2 (>= 2.0.4~git20101213),
         zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0, upstart-job,
         libpam-runtime (>= 1.0.1-11), libpam-modules, lsb-base (>= 3.2-13),
         procps, update-inetd, adduser, samba-common-bin
Recommends: logrotate
Suggests: openbsd-inetd | inet-superserver, smbldap-tools, ldb-tools, ufw
Conflicts: samba4 (< 4.0.0~alpha6-2)
Breaks: cups (= 1.4.4-4)
Replaces: samba-common (<= 2.0.5a-2)
Description: SMB/CIFS file, print, and login server for Unix
 Samba is an implementation of the SMB/CIFS protocol for Unix systems, providing
 support for cross-platform file and printer sharing with Microsoft Windows, OS
 X, and other Unix systems.  Samba can also function as an NT4-style domain
 controller, and can integrate with both NT4 domains and Active Directory realms
 as a member server. 
 
 This package provides the components necessary to use Samba as a stand-alone
 file and print server.  For use in an NT4 domain or Active Directory realm, you
 will also need the winbind package. 
 
 This package is not required for connecting to existing SMB/CIFS servers (see
 smbclient) or for mounting remote filesystems (see cifs-utils).
Homepage: http://www.samba.org

rick@rick-HP:~$ aptitude show samba-common
Package: samba-common                    
State: installed
Automatically installed: no
Version: 2:3.5.6~dfsg-3ubuntu3
Priority: optional
Section: net
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 721 k
Depends: ucf, debconf (>= 0.5) | debconf-2.0
Recommends: samba-common-bin
Conflicts: samba4-common (< 4.0.0~alpha7-1)
Replaces: samba (< 3.0.20b-1), samba4-common (< 4.0.0~alpha7-1)
Description: common files used by both the Samba server and client
 Samba is an implementation of the SMB/CIFS protocol for Unix systems, providing
 support for cross-platform file and printer sharing with Microsoft Windows, OS
 X, and other Unix systems. 
 
 This package contains common files used by both Samba 3 and Samba 4.
Homepage: http://www.samba.org

rick@rick-HP:~$ 

```

---

### Post by JeffElkins on 2011-01-22
> **Smart Viking said:**
> try
```
sudo apt-get install samba4
```

Samba4 is not what I want. I want to install samba 3.4.7

How to fix the broken package?

---

### Post by dandnsmith on 2011-01-22
What I did (and I have it installed and working) was to get to Synaptic Package Manager (thru System|Admin), and key samba into the search - everything else, including needed other items can then be selected and intalled.

---

### Post by JeffElkins on 2011-01-22
> **dandnsmith said:**
> What I did (and I have it installed and working) was to get to Synaptic Package Manager (thru System|Admin), and key samba into the search - everything else, including needed other items can then be selected and intalled.

Thanks for the reply. Synaptic basically gives be the same error as apt:

```

samba:
  Depends: libwbclient0 (=2:3.4.7~dfsg-1ubuntu3) but 2:3.4.7~dfsg-1ubuntu3.2 is to be installed

```

---

### Post by JeffElkins on 2011-01-22
Removing libwbclient0 then apt-get samba worked. Thanks for the replies.

---


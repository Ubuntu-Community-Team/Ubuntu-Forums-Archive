---
title: "dpkg: error processing ... (--unpack)"
date: 2012-08-10
forum: General Help
---

### Post by mizery on 2012-08-10
Hi everyone! I'm having some trouble on Ubuntu 10.04 - I've been trying to install ircd-hybrid, and somewhere along the way I wanted to reinstall the package. I ran apt-get remove and afterwards tried to rerun apt-get install - but I'm getting an "dpkg: error processing"-error, see below:

```

$ sudo apt-get install ircd-hybrid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot openafs-modules-dkms linux-headers-generic linux-headers-2.6.32-21 lsof bison manpages-dev libc-dev-bin m4 libgomp1 linux-libc-dev gcc-4.4
  linux-headers-2.6.32-21-generic gcc dkms manpages flex libc6-dev patch binutils
Use 'apt-get autoremove' to remove them.
Suggested packages:
  hybserv
The following NEW packages will be installed:
  ircd-hybrid
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/590kB of archives.
After this operation, 2,609kB of additional disk space will be used.
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75, <> line 1.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
(Reading database ... 43478 files and directories currently installed.)
Unpacking ircd-hybrid (from .../ircd-hybrid_1%3a7.2.2.dfsg.2-6ubuntu3_i386.deb) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75.)
debconf: falling back to frontend: Readline
dpkg: error processing /var/cache/apt/archives/ircd-hybrid_1%3a7.2.2.dfsg.2-6ubuntu3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ircd-hybrid_1%3a7.2.2.dfsg.2-6ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Here's some OS info if thats relevant:
```

$ uname -r
2.6.18-308.el5.028stab099.3
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

```

I've tried "apt-get clean", update, upgrade, purge, and "sudo dpkg -i --force-overwrite ..." as I've seen others have used to fix the issue, but the same result:
```

$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/ircd-hybrid_1%3a7.2.2.dfsg.2-6ubuntu3_i386.deb
(Reading database ... 43105 files and directories currently installed.)
Unpacking ircd-hybrid (from .../ircd-hybrid_1%3a7.2.2.dfsg.2-6ubuntu3_i386.deb) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75.)
debconf: falling back to frontend: Readline
dpkg: error processing /var/cache/apt/archives/ircd-hybrid_1%3a7.2.2.dfsg.2-6ubuntu3_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ircd-hybrid_1%3a7.2.2.dfsg.2-6ubuntu3_i386.deb

```

Any idea how to fix this issue? Thanks in advance!

---

### Post by dcstar on 2012-08-10
> **mizery said:**
> Hi everyone! I'm having some trouble on Ubuntu 10.04 - I've been trying to install ircd-hybrid, and somewhere along the way I wanted to reinstall the package.
.........
Any idea how to fix this issue? Thanks in advance!

[LIST=1]
[*]Stop using the command line for package management and use the provided GUI tools like Synaptic.
[*]Fix the debconf (select Gnome):
```
sudo dpkg-reconfigure debconf
```
[*]Install and run Synaptic to install the package.
[/LIST]

---

### Post by mizery on 2012-08-12
Hi dcstar, and thank you very much for your reply.

I only have SSH access to the machine, and as an ubuntu rookie I'm trying to get a better understanding of what happens behind the GUI. 
I did, however, install synaptic and used ssh -X to get the GUI up, then chose "mark for complete removal", and then reinstalled ircd-hybrid. This worked - but I thought "complete removal" was equivalent to "apt-get --purge remove ..." - is this not true?

Thanks for the dpkg-reconfigure debconf, that fixed my "unable to initialize frontend: Dialog"-warnings.

---


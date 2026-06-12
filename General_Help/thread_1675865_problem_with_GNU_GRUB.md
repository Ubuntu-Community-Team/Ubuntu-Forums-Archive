---
title: "problem with GNU GRUB?"
date: 2011-01-26
forum: General Help
---

### Post by mr.peeters@gmail.com on 2011-01-26
Hi, 

I used to be running Ubuntu 10.04LTS - in dual boot with win7.
Just upgraded to Ubuntu 11.04, and everything seems to be working fine.

Except:
I'm using GNU GRUBversion1.98+20100804-5ubuntu3
If this starts up and I have to choose which system to booth first lines are:
- Ubuntu, with Linux 2.6.35-24-generic
- Ubuntu, with Linux 2.6.35-24-generic (recovery)
- Ubuntu, with Linux 2.6.32-27-generic
- Ubuntu, with Linux 2.6.32-27-generic (recovery)

However, if I choose the first option (which is also the default) I get an error-message:
MODPROBE: FATAL: Could not load /lib/modules/2.6.35-24-generic/modules.dep No such file or directory

So I guess there's a problem there. My computer fixes it as he goes along, but takes a long time to startup of course. If I choose 2.6.32-27 he does load.

What is the difference between these two - and could I get rid of 2.6.35-24 in GNU GRUB, or at least make 2.6.32-27 my default?

Any help welcome!

Thanks, 
d.

---

### Post by ajgreeny on 2011-01-26
2.6.32-27-generic is the kernel from Lucid, which does not get removed when you updated to 11.04.  I don't think you should remove the new kernel, as that is the default for natty, so hang on for now.  It may be that an update will fix your problem, but don't forget that natty is still in alpha, so breakages must be expected.

Perhaps you should install startup manager in natty to set the default booted kernel for the moment, and occasionally test the natty kernel to see if things have improved.

---

### Post by oldfred on 2011-01-26
I do not think you upgraded to 11.04. There is a bug on what version is used in some tools like System,About Ubuntu . 

Kernel 2.6.35 is Maverick 10.10.

To see correct version:
Version or DISTRIB:
cat /etc/*release
cat /etc/lsb-release

If you are booting Lucid you may want to rerun the update as it sounds like it did not run to completition.

These are my suggested commands to update from a chroot, use sudo if you can boot.
Commands once in chroot:
if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---


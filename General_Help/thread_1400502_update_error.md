---
title: "update error"
date: 2010-02-07
forum: General Help
---

### Post by jackechanprime on 2010-02-07
no idea what went wrong. computer was apparently shutdown halfway through installing major system updates. now booting into terminal(gnome?), and displaying error messages:

one or more of the mounts listed in fstab cannot yet be mounted:
(esc for recovery shell)
/: waiting for /dev/disk/by-uuid/[loooooong string of aplha-numeric(a/#) babble]
/tmp: waiting for (null)
swap: waiting for uuid-[another (diffrent-but-similar) string of A/# babble]


~~user input: esc (the phrase: '^] pops up)

Mountall: canceled
init: mountall main process (1141) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try
root@(none):~# sudo aptitude update
sudo: unable to resolve host (none)
E: /root/.aptiture is readable but not writable; unable to write configuration file.
W: Not locking for read only lock file /var/lib/dpkg/lock
Edpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
err [http://ca.archive.ubunty.com](http://ca.archive.ubunty.com) karmic release.gpg
    cound not resolve 'ca.archive.ubuntu.com'
~~ similar error repeats 4-5 times
W: Not using locking for read only lock fire /var/lib/apt/lists/lock
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
E: couln't rebuild package cache
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

root@(none):~# sudo dpkg --configure -a
sudo: unable to resolve host (none)
dpkg: unable to access dpkg status area: read-only file system
root@(none):~# login (correct user/pass)
--login successful
root@(none):~# sudo dpkg --configure -a
~~ same errors






soooo... i'm over my head. i tried everything from chmod on 'lock' to gethost (which turned out to not be installed.) nothing is working yet. pleeeeeease tell me that this is an easy fix. I'm a hardy n00b, I'm surprised i even got that far. for anyone that helps, i have cookies!! (:: ) (:: )
 (:: )

---

### Post by plucky on 2010-02-07
Don't use sudo as you are already using the root login shell.

> root@(none):~#

---

### Post by jackechanprime on 2010-02-07
hmm. i don't know if i tried that, but something else entirely worked.

i ran dpkg man, and sorted through all the options, and came across -resolve -trigger, which i tried. after about 15 minutes of the computer babbling about what it was updating, i restarted and the system booted up... sort of... normally.

however, several new problems have popped up;
drivers seem to be broken, and update manager comes back with errors about broken packages and something about being incompatible with some type of upgrade. apparently something on the order of upgrading from hardy to (i forget the name, some other bird).

bottom line is, i got the system functioning again, but something went screwloose, and things arn't quite the same. so... what the HECK did i do?

please and thank you.

---


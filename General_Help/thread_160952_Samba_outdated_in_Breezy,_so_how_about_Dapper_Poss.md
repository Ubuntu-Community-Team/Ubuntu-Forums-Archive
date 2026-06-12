---
title: "Samba outdated in Breezy, so how about Dapper? Possible?"
date: 2006-04-16
forum: General Help
---

### Post by motionsiren on 2006-04-16
Im trying to figure out best practice for when this happens to not just this package, but any.

A good working example of this is my current problem. Im running 5.10 which ships with Samba 3.0.14a and I have an office full of OS X 10.4 users... big problem ([https://launchpad.net/distros/ubuntu/+source/samba/+bug/23679](https://launchpad.net/distros/ubuntu/+source/samba/+bug/23679)) so I need to upgrade but no one seems interested in updating the samba package in breezy's repositories....

Dapper has 3.0.20, which I would love to upgrade to to fix this problem, but I don't want to risk my apt-get system if this means I will have problems upgrading to Dapper when the time comes.

Assuming this is possible without breaking a clean full upgrade to Dapper, what would I need to do? Just copy the dapper source.list file and use that? Download the samba.deb for dapper?

Additionally, why isn't samba for breezy updated? That'd seem to be the easiest solution.

---

### Post by SadaraX on 2006-04-16
There is samba version 3.0.22 in Dapper, but if its such a problem for you, why not just download the source and compile it yourself? Its cannot be that hard...

---

### Post by Boondoggle on 2006-04-18
[QUOTE=motionsiren]Im trying to figure out best practice for when this happens to not just this package, but any.

A good working example of this is my current problem. Im running 5.10 which ships with Samba 3.0.14a and I have an office full of OS X 10.4 users... big problem ([https://launchpad.net/distros/ubuntu/+source/samba/+bug/23679](https://launchpad.net/distros/ubuntu/+source/samba/+bug/23679)) so I need to upgrade but no one seems interested in updating the samba package in breezy's repositories....

Additionally, why isn't samba for breezy updated? That'd seem to be the easiest solution.[/QUOTE]

This explains why I can't get smb to work... but I'm also having trouble with NFS.  Anyone know how to access a NFS share on Ubuntu from OS 10.4?

thnks,  bd

---


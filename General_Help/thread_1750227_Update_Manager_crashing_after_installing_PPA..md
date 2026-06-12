---
title: "Update Manager crashing after installing PPA."
date: 2011-05-05
forum: General Help
---

### Post by tokintmash on 2011-05-05
Hi,

I am running Ubuntu 10.10. I wanted to install a Cinelerra video editor and followed instructions giver here: [https://launchpad.net/~cinelerra-ppa/+archive/ppa](https://launchpad.net/~cinelerra-ppa/+archive/ppa)

Under the "read about installing"

But doing so, ubuntu software center does not launch and update manager gives the following error:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/gwibber-daily-ppa-maverick.list'

How to fix this?

---

### Post by gmargo on 2011-05-05
Those PPA installation instructions are misleading.  You are supposed to substitute "cinelerra-ppa/ppa" for "gwibber-daily/ppa".

Here's the proper command you should run to add the Cinelerra PPA:
```

sudo add-apt-repository ppa:cinelerra-ppa/ppa

```And here's the command to remove the "gwibber" error:
```

sudo add-apt-repository --remove ppa:gwibber-daily/ppa

# Actually, this does not seem to work properly. (deb-src line left behind.)
# This will definitely nuke the entries:
sudo rm /etc/apt/sources.list.d/gwibber-daily-ppa-maverick.list*

```

Update: There is a bug report for the failure of the --remove option: 
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/680203](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/680203)

---

### Post by tokintmash on 2011-05-06
Thank you!

---


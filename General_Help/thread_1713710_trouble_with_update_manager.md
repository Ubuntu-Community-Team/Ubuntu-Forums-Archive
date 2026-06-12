---
title: "trouble with update manager"
date: 2011-03-24
forum: General Help
---

### Post by larry7 on 2011-03-24
hi,

recently my update manager gave me this error:


An unresolvable problem occurred while initializing the package information.

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

I tried looking at the offending file but have no real idea what i am looking at. 

Any help is much appreciate!

Larry

---

### Post by plucky on 2011-03-24
> **larry7 said:**
> hi,

recently my update manager gave me this error:


An unresolvable problem occurred while initializing the package information.

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

I tried looking at the offending file but have no real idea what i am looking at. 

Any help is much appreciate!

Larry

You can delete the list file and reload it again using ```
sudo apt-get update
``` to see if it is the problem.

To delete it use ```
cd /var/lib/apt/lists/
sudo rm archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages
```

Good Luck

---

### Post by larry7 on 2011-03-24
thanks! that fixed the problem.

---


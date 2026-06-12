---
title: "Duplicate code sources"
date: 2011-06-13
forum: General Help
---

### Post by sofasurfer on 2011-06-13
The following messages were shown when I updated. I could not find the problem so I made a new source.list at "source code generater" at [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/).
I still get the errors. Why?



W: Duplicate sources.list entry [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_stebbins_handbrake-releases_ubuntu_dists_lucid_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_lucid_free_binary-amd64_Packages)

---

### Post by wildmanne39 on 2011-06-13
> **sofasurfer said:**
> The following messages were shown when I updated. I could not find the problem so I made a new source.list at "source code generater" at [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/).
I still get the errors. Why?



W: Duplicate sources.list entry [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_stebbins_handbrake-releases_ubuntu_dists_lucid_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_lucid_free_binary-amd64_Packages)
Hi, go into synaptic, settings,repositories,other software and uncheck or remove the duplicate repository.

---

### Post by Elfy on 2011-06-13
PPA's and other 'extra' repos are in /etc/apt/sources.list.d

You can just remove the duplicate source files in there.

Alternatively you can do so in Software Sources

---

### Post by sofasurfer on 2011-06-13
Thanks.
So, sources.list is not the only file that is read? Can you explain what sources.list.d does? I see that many of the sources that I put into sources.list (with the generated file) are also in sources.list.d.

---

### Post by Elfy on 2011-06-13
I'm not sure when it happened but I noticed a few releases ago that sources.list had only the 'ubuntu' repos and anything else went to sources.list.d/[repo].list. 

From the apt-get man page

/etc/apt/sources.list
           Locations to fetch packages from. Configuration Item:
           Dir::Etc::SourceList.

/etc/apt/sources.list.d/
           File fragments for locations to fetch packages from. Configuration
           Item: Dir::Etc::SourceParts.

---

### Post by sofasurfer on 2011-06-13
I think I understand. Thanks.

---


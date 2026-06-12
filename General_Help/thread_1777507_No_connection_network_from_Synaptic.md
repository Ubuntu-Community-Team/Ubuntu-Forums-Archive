---
title: "No connection network from Synaptic"
date: 2011-06-07
forum: General Help
---

### Post by Ulm on 2011-06-07
Hi everybody,

This is my first post in this Forum.

I've a problem when run the Synaptic or Update Manager, it appears the following debug:

"W:Duplicate sources.list entry [http://sunsite.rediris.es/mirror/ubuntu-archive/](http://sunsite.rediris.es/mirror/ubuntu-archive/) natty/restricted i386 Packages (/var/lib/apt/lists/sunsite.rediris.es_mirror_ubuntu-archive_dists_natty_restricted_binary-i386_Packages), E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/sunsite.rediris.es_mirror_ubuntu-archive_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened."

What can i do?

Thanks¡¡

PS. I've Ubuntu 11.04 and I can access without problems to internet by manual (no DHCP) wired router connection

---

### Post by jerrrys on 2011-06-08
this should fix it

[http://ubuntuforums.org/showthread.php?t=1777289](http://ubuntuforums.org/showthread.php?t=1777289)

---

### Post by Ulm on 2011-06-09
Thanks a lot for your reply¡

Researching that link, i find out this post: [http://ubuntuforums.org/showpost.php?p=10780755&postcount=8](http://ubuntuforums.org/showpost.php?p=10780755&postcount=8) :

- sudo rm /var/lib/apt/lists/* -vf (To delete all package listings)
- sudo apt-get update (To rebuilt them)

Then i could fix the problem changing the settings options of Synaptic

---


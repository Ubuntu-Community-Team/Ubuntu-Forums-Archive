---
title: "Update error... Network problem?"
date: 2009-09-21
forum: General Help
---

### Post by mac666 on 2009-09-21
Hey
I get an Angry "!" notification in my top panel.
It says: (translated with google translate from swedish)
```
Could not download all repositories index  

 Repository may no longer be available or could not be contacted because of network problems. 
An earlier version of the index will be used if available. If not, the repository will be ignored. Check your network connection and make sure that the address of the repository of the settings are correct.
[code]Failed to fetch cdrom: / / Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) / dists/jaunty/main/binary-amd64/Packages use apt-cdrom to APT to recognize this CD. apt-get update can not be used to add records 
 Failed to fetch cdrom: / / Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) / dists/jaunty/restricted/binary-amd64/Packages use apt-cdrom to APT to recognize this CD. apt-get update can not be used to add records 
 Some index files could not be retrieved, they have been ignored or they have old used instead.

```[/code]Whats up with this? My network seems fine, im here?

---

### Post by nikhilk on 2009-09-21
> **mac666 said:**
> ```
Failed to fetch cdrom: / / Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) / dists/jaunty/main/binary-amd64/Packages use apt-cdrom to APT to recognize this CD. apt-get update can not be used to add records 
 Failed to fetch cdrom: / / Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) / dists/jaunty/restricted/binary-amd64/Packages use apt-cdrom to APT to recognize this CD. apt-get update can not be used to add records 
 Some index files could not be retrieved, they have been ignored or they have old used instead.

```Whats up with this? My network seems fine, im here?

Seems that the installation CD has been added as a repository for apt-get and the CD is not present in the optical drive.
Disable the CDROM repository and see if that error goes away.

---

### Post by mac666 on 2009-09-21
Yeah... Thanks... Of course it was that. :)

---

### Post by nikhilk on 2009-09-21
> **mac666 said:**
> Yeah... Thanks... Of course it was that. :)

Happy to help :)

---


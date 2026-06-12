---
title: "Using the Ubuntu Repository as a backup to a Personal Repository"
date: 2010-04-07
forum: General Help
---

### Post by jeemeekay on 2010-04-07
Hi everyone,
I would like to find out if this is possible. My scenario is, I have a  repository which i setup using reprepro. I have some packages on there  but it seems that the Ubuntu repositories have a more recent version of  those packages. What I want to do is when someone does an apt-get  install package-name, it downloads the packages from my repository (in  respect of any updated versions in other ubuntu repositories).  I would  like to achieve this with zero configuration on the client. Ideally what  I would want is to be able to just point the sources.list to my  repository for all packages, and if the package does not exist in my  repository, it then goes to look in the ubuntu repos. I have heard of  things like apt-mirror etc but I am not sure if this would help me  achieve what I want. Any help would be appreciated.

Regards,
Kayode.

---

### Post by dcstar on 2010-04-07
> **jeemeekay said:**
> Hi everyone,
I would like to find out if this is possible. My scenario is, I have a  repository which i setup using reprepro. I have some packages on there  but it seems that the Ubuntu repositories have a more recent version of  those packages. What I want to do is when someone does an apt-get  install package-name, it downloads the packages from my repository (in  respect of any updated versions in other ubuntu repositories).  I would  like to achieve this with zero configuration on the client. Ideally what  I would want is to be able to just point the sources.list to my  repository for all packages, and if the package does not exist in my  repository, it then goes to look in the ubuntu repos. I have heard of  things like apt-mirror etc but I am not sure if this would help me  achieve what I want. Any help would be appreciated.


All repository tools will install the latest version if that is set in the tool (Synaptic has a setting for that).

If you want your packages to be installed, then they need to have later version designations than other available packages in other repositories.

---


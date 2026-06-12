---
title: "Changing Ubuntu 10.10 default package installer"
date: 2011-01-20
forum: General Help
---

### Post by metallica1973 on 2011-01-20
I am using Ubuntu 10.10. I have a situation to where I need to use synaptic package instead of Ubuntu Software Center. How do I change the default *deb package manager from "Ubuntu Software Center" to "Synaptic Package Manager".

---

### Post by ajgreeny on 2011-01-20
I am not sure you can do that in any of the versions of Ubuntu.  In the past double clicking a .deb file would open gdebi, but it is not in 10.10 by default, though you can add it if needed.

Why is it so important to use synaptic rather than software centre?  As far as I can see they do exactly the same job.

---

### Post by metallica1973 on 2011-01-24
We have developed a software package that is designed to use the default package installer "synaptic package manager" on Ubuntu 10.04. We have various packages for basically all flavors of Unix and Linux. If you do a tar.gz install then the first thing that is seen by the user is the "license agreement" and you answer "yes" and proceed with the installation. The most common method of installing this package for linux users that are nott "CLI" savvy is by using the DEB package that we have and using the default package installer of the past "synaptic package manager". In Ubuntu 10.10 they switched it to "Ubuntu Software Center". The problem with this is that is doesnt display the terminal windows like "synaptic package manager" does and therefor just hangs (license agreement) when the users choose this method. help?

---

### Post by frogotronic on 2011-05-13
> **metallica1973 said:**
> We have developed a software package that is designed to use the default package installer "synaptic package manager" on Ubuntu 10.04. We have various packages for basically all flavors of Unix and Linux. If you do a tar.gz install then the first thing that is seen by the user is the "license agreement" and you answer "yes" and proceed with the installation. The most common method of installing this package for linux users that are nott "CLI" savvy is by using the DEB package that we have and using the default package installer of the past "synaptic package manager". In Ubuntu 10.10 they switched it to "Ubuntu Software Center". The problem with this is that is doesnt display the terminal windows like "synaptic package manager" does and therefor just hangs (license agreement) when the users choose this method. help?

Yeah, stupid change in 10.10.

```
sudo apt-get install gdebi
```

go to a deb file; right-click; go to properties; choose GDebi Installer as the default.


- CH   :guitar:

---


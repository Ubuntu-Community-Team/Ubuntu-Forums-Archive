---
title: "shared-mime-info - unkown media type errors"
date: 2012-05-14
forum: General Help
---

### Post by maverickaddicted on 2012-05-14
Hello,

I am trying to install the virtual box in my kubuntu machine, but getting following errors -

```

rahul@thinki05:~/Shared$ sudo dpkg -i virtualbox-4.1_4.1.14-77440~Ubuntu~oneiric_i386.deb 
(Reading database ... 153438 files and directories currently installed.)
Preparing to replace virtualbox-4.1 4.1.14-77440~Ubuntu~oneiric (using virtualbox-4.1_4.1.14-77440~Ubuntu~oneiric_i386.deb) ...
 * Stopping VirtualBox kernel modules                                           [ OK ] 
Unpacking replacement virtualbox-4.1 ...
Setting up virtualbox-4.1 (4.1.14-77440~Ubuntu~oneiric) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
 * Stopping VirtualBox kernel modules                                           [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                              [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  [ OK ] 
 * Starting VirtualBox kernel modules                                           [ OK ] 
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...

```

---

### Post by matt_symes on 2012-05-14
Hi

Are you sure they are errors ? 


I thought they were just warnings when updating the mime types database with unknown mime types from the xml files.


Are they causing problems ?


Kind regards

---

### Post by maverickaddicted on 2012-05-15
No, they haven't cause any problems, but is it OK to leave the warning?

---

### Post by matt_symes on 2012-05-15
Hi

> **maverickaddicted said:**
> No, they haven't cause any problems, but is it OK to leave the warning?

Yes. It's OK to leave the warnings.

If you really want to get rid of them you can remove the entries from the mime files causing the problem. I believe it's this file according to bug reports on launchpad; such as this bug report [https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/193325](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/193325)

```
/usr/share/mime/packages/kde.xml
```

and then rebuild the mime database with 

```
update-mime-database
```

(It's actually this command causing the warnings when it gets called as a post install trigger).

If it's not causing you problems though then.....

Kind regards

---

### Post by maverickaddicted on 2012-05-15
> **matt_symes said:**
> Hi



Yes. It's OK to leave the warnings.

If you really want to get rid of them you can remove the entries from the mime files causing the problem. I believe it's this file according to bug reports on launchpad; such as this bug report [https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/193325](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/193325)

```
/usr/share/mime/packages/kde.xml
```

and then rebuild the mime database with 

```
update-mime-database
```

(It's actually this command causing the warnings when it gets called as a post install trigger).

If it's not causing you problems though then.....

Kind regards

Thanks for the update, I am keeping it as it is.

---


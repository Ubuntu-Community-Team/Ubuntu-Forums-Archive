---
title: "Update Manager gives error NO_PUBKEY 412E6F44D24E86AB"
date: 2012-01-06
forum: General Help
---

### Post by rakesh.swapna on 2012-01-06
On update I get this error 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 412E6F44D24E86AB

please help

---

### Post by Shazaam on 2012-01-06
Try this...
```
sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 412E6F44D24E86AB
```

---

### Post by rakesh.swapna on 2012-01-07
> **Shazaam said:**
> Try this...
```
sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 412E6F44D24E86AB
```


That gave me another error BADSIG 40976EAF437D05B5. I was able to solve this by 

```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```

Ref : [http://ubuntuforums.org/showthread.php?t=802156](http://ubuntuforums.org/showthread.php?t=802156) Reply #5 by Alexfish.

Thanks both Shazaam and Alexfish.

---


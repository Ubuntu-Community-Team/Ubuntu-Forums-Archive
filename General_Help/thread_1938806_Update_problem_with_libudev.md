---
title: "Update problem with libudev"
date: 2012-03-10
forum: General Help
---

### Post by BobvanderPoel on 2012-03-10
I keep getting an error with a proposed update. The update manager wants t upgrade libudev0. I _think_ this upgrade is in medibuntu 11.10 repository.

When I try to update I a "check your internet connection" error and the expanded message:

Failed to fetch [http://mirror.peer1.net/ubuntu/pool/main/u/udev/libudev0_173-0ubuntu4.2_i386.deb](http://mirror.peer1.net/ubuntu/pool/main/u/udev/libudev0_173-0ubuntu4.2_i386.deb) Hash Sum mismatch

Since my connection is fine and the computer seems to be running fine, I though the easy solution would be to remove the repository. Did that from synaptic and redid the config. But after a few minutes the upgrade available message comes back. Did a "sudo apt-get update -m" and ".. -f" ... no differences.

This is driving me nuts. I assume that the package has been partially downloaded and is now sitting waiting to be installed? Can I delete that and get a normal system back?

Thanks.

---

### Post by raja.genupula on 2012-03-10
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

and try again ,all the best .

---

### Post by BobvanderPoel on 2012-03-10
Thanks (and that was quick!). I removed the lists as you say and  apt-get update. All worked fine.

The medibuntu repository is still there (I can remove it and try again if you think that is the problem). But, after the "rm" and "update" I do an upgrade and get an error.

apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libudev0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) oneiric-proposed/main libudev0 i386 173-0ubuntu4.2 [35.2 kB]
Fetched 35.2 kB in 0s (2,715 kB/s)
Failed to fetch [http://mirror.peer1.net/ubuntu/pool/main/u/udev/libudev0_173-0ubuntu4.2_i386.deb](http://mirror.peer1.net/ubuntu/pool/main/u/udev/libudev0_173-0ubuntu4.2_i386.deb) Hash Sum mismatch
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

Any idea what's wrong?

Best,

---

### Post by raja.genupula on 2012-03-10
```
http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3
```

---

### Post by BobvanderPoel on 2012-03-10
> **raja.genupula said:**
> ```
http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3
```

Well, not exactly :)

But, I did manage to sort of clean things up by removing the orieric-proposed updates via synaptic. (not medibuntu, which wasn't the problem).

I'm afraid to re-enable this for now. I'll leave it for a week or so and hopefully the hash-codes will be correct :)

---


---
title: "Problems updating ubuntu"
date: 2012-05-28
forum: General Help
---

### Post by shresthanator on 2012-05-28
Hey everyone, I am having some problems updating Ubuntu 11.10. My update manager is showing that my "package information was last updated 42 days ago". But when I try to update it, by first hitting check for updates, it wont show any. I have tried updating through the command line sudo apt-get update. However it still does not show the latest updates. Can you guys please help me out? thanks

---

### Post by MG&amp;TL on 2012-05-28
Can you post output of:

```
sudo apt-get update && sudo apt-get upgrade
```

please?

I think the update manager (X days since packages were last updated) thing's a bug, it's on my (fully updated) system too.

---

### Post by shresthanator on 2012-05-28
yea, but I wanted to upgrade to 12.04 (and I have the option for the new distributions enabled in the settings)....so shouldn't it give me that option? Anyways here is the output: 


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by shresthanator on 2012-05-28
yea, but I wanted to upgrade to 12.04 (and I have the option for the new distributions enabled in the settings)....so shouldn't it give me that option? Anyways here is the output: 


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by MG&amp;TL on 2012-05-28
Okay, if update manager's not working, we can try manually upgrading:

```
sudo do-release-upgrade
```

---

### Post by shresthanator on 2012-05-28
> **MG&TL said:**
> Okay, if update manager's not working, we can try manually upgrading:

```
sudo do-release-upgrade
```
yes, thank you very much. I guess I will just let the update run for the next several hours

---


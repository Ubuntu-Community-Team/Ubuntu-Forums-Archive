---
title: "Update error"
date: 2011-02-05
forum: General Help
---

### Post by AquaRegis on 2011-02-05
While I am trying to install updates following error is displayed

W:Failed to fetch [http://ppa.launchpad.net/ubuntu/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

My internet conection is good, I've installed some updates months ago.
How can I fix this error?

---

### Post by [Snc] on 2011-02-05
> **AquaRegis said:**
> While I am trying to install updates following error is displayed

W:Failed to fetch [http://ppa.launchpad.net/ubuntu/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

My internet conection is good, I've installed some updates months ago.
How can I fix this error?

Hello!
Go to 
```
System -> Administration -> Synaptic Package Manager
```or run 

```
gksu synaptic
```Then in the menu, go to "Settings" -> "Repositories", browse to the tab "Other Software". This is where you can manage your PPA-s, you can edit/add/remove them...

---

### Post by [Snc] on 2011-02-05
I just noticed, that this thread is marked "Edubuntu" and your OS version is marked as Ubuntu Maverick ... which one is correct? 

My reply is for Maverick, but maybe with smaller changes should work for Edubuntu too, I don't know how Edubuntu is set up....

---


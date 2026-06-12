---
title: "Ubuntu Fails To Retrieve Packages"
date: 2010-07-19
forum: General Help
---

### Post by giddyup306 on 2010-07-19
Hello everyone.  I tried to upgrade VLC to 1.1.0 (according to VLCs site 1.0.6 is outdated).  What's funny is I didn't see a download for 1.1.0 on there site.  Anyways I ran    ```
sudo add-apt-repository ppa:c-korn/vlc && sudo apt-get  update
```  then  ```
sudo apt-get install vlc mozilla-plugin-vlc
```  When it was trying to install it gave me the following error:  ```
W: Duplicate sources.list entry http://www.geekconnection.org/remastersys/repository/ karmic/ Packages (/var/lib/apt/lists/www.geekconnection.org_remastersys_repository_karmic_Packages) W: You may want to run apt-get update to correct these problems 
```   I ran apt-get update and it told me.  ```
W: Failed to fetch http://deb.torproject.org/torproject.org/dists//main/binary-i386/Packages.gz  404  Not Found [IP: 86.59.30.36 80]  E: Some index files failed to download, they have been ignored, or old ones used instead. 
```  What gives?  I noticed that it has karmic in this code.  I am running Lucid if that means anything.

---


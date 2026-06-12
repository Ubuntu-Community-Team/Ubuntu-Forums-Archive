---
title: "Problems with installing ubuntu one"
date: 2012-08-30
forum: General Help
---

### Post by EthioJOB on 2012-08-30
Hi,

I tried to install Ubuntu One but it keeps bring the following message:

*> W:Failed to fetch [http://www.remastersys.com/ubuntu/dists/precise/InRelease](http://www.remastersys.com/ubuntu/dists/precise/InRelease)  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file), E:Some index files failed to download. They have been ignored, or old ones used instead.*

For additional info, some time ago I did try to install remastersys from somewhere (outside the software centre, because I couldn't find it) and after it didn't work as I though I just forgot about it. and now I think this is the one causing the probelm (from what I can understand from the error message above).

I'd appreciate any help.

Thanks in advance.

---

### Post by oldos2er on 2012-08-30
Remove the remastersys repo from your sources. You can edit /etc/apt/sources.list directly (with root privileges) or from Software Sources: ```
gksu software-properties-gtk
```

---

### Post by EthioJOB on 2012-09-06
It helped. Thanks a lot!

---


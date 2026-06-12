---
title: "Cannot download updates"
date: 2010-10-16
forum: General Help
---

### Post by simontepper on 2010-10-16
When I tried to update 10.10 this morning, I got the message 'Failed to depository information', which when expanded gave the following details:

W:Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

My internet connection is good and I've had no previous problems with this.

I've looked at previous threads on this subject and have tried some of the remedies people have suggested, such as 'sudo apt-get clean' and 'sudo apt-get update', but to no avail.

All help gratefully accepted!

---

### Post by yetiman64 on 2010-10-16
That entry is a ppa and it can be disabled via System > Administration > Software Sources > Other Software tab, and deticking the gdm2setup entries there. This will not uninstall the actual software from the ppa but only stop any automatic updating of it. In fact some people advise disabling ppas after initial install if the software is working well.

Try doing an update after doing the above.

---

### Post by simontepper on 2010-10-17
Thanks, yetiman64. It seems to work; I had to hunt around for the Software Sources menu (it had been disabled in the list of Administration entries but I found out how to edit that). I was then asked to 'Reload' or 'Close' the Software Sources window. I chose 'Reload' and I appear to be able to do an update (it shows that I am up-to-date). It looks like this has worked. Thanks again.

:)

---


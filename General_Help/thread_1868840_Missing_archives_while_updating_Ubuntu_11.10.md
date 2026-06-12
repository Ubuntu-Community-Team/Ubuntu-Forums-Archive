---
title: "Missing archives while updating Ubuntu 11.10"
date: 2011-10-24
forum: General Help
---

### Post by Thelinuxgeek on 2011-10-24
When I try to update via sudo apt-get update, I get this error:

W:Failed to fetch [http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Since it's a 404 error I'm assuming the issue is server problems, and not my Ubuntu installation, but you never know. Anyone know what's going on?

---

### Post by tom.swartz07 on 2011-10-24
> **Thelinuxgeek said:**
> When I try to update via sudo apt-get update, I get this error:

W:Failed to fetch [http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Since it's a 404 error I'm assuming the issue is server problems, and not my Ubuntu installation, but you never know. Anyone know what's going on?

I googled the packager name, and I found that he has an icon set on launchpad. 

You likely added his ppa for the icons, and he didnt get around to updating the branch for Oneiric. 

It likely wont cause any problems, and once he updates it you should be good to go.

---

### Post by Thelinuxgeek on 2011-10-24
> **tom.swartz07 said:**
> I googled the packager name, and I found that he has an icon set on launchpad. 

You likely added his ppa for the icons, and he didnt get around to updating the branch for Oneiric. 

It likely wont cause any problems, and once he updates it you should be good to go.

Yep! I'm using the Awoken icon theme.
[http://gnome-look.org/content/show.php/AwOken?content=126344](http://gnome-look.org/content/show.php/AwOken?content=126344)

---


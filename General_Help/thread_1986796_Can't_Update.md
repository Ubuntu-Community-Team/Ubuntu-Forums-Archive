---
title: "Can't Update"
date: 2012-05-25
forum: General Help
---

### Post by Watchlord on 2012-05-25
I'm using Ubuntu 11.04 and 11.04 Server. I can't update. I got on one day and both systems say they can't download updates. I didn't make any changes. I've tried different things an gotten back new  error messages.

I will take screenshots and post them in this forum when I get the machines up, but is this a common problem?

---

### Post by Enigmapond on 2012-05-25
Need to see the error messages. It's only common of you have a bad internet connection or your sources are incorrect.

---

### Post by Watchlord on 2012-05-25
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_11.1.102.63-0natty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_11.1.102.63-0natty1_i386.deb) 404  Not Found [IP: 91.189.92.150 80]

Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.63-0natty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.63-0natty1_i386.deb) 404  Not Found [IP: 91.189.92.150 80]

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-partner/app-install-data-partner_12.11.04.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-partner/app-install-data-partner_12.11.04.3_all.deb) 404  Not Found [IP: 91.189.92.190 80]

This is from the server. My connection is fine.

---

### Post by Enigmapond on 2012-05-25
These sources are bad. Just remove these lines from your sources.list and it should be fine.

---

### Post by Watchlord on 2012-05-25
> **Enigmapond said:**
> These sources are bad. Just remove these lines from your sources.list and it should be fine.

They aren't in the list at all.

---

### Post by Watchlord on 2012-05-25
```
W:Failed to fetch http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://www.sourceslist.eu/repo/ubuntu/dists/maverick/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://www.sourceslist.eu/repo/ubuntu/dists/maverick/non-free/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```That's what my netbook says.

---

### Post by Enigmapond on 2012-05-25
You have two systems correct? Looks like the server has the previous bad sources and your netbook as the ones you just posted.  You need to remove all of them....you can still upgrade BTW...with:

```
sudo apt-get upgrade
```

It just won't get anything from these sources. The other option is to uncheck all third party PPA's when you do the update but these sources ARE there and need to be removed.

---

### Post by Watchlord on 2012-05-25
That seemed to work, thanks.

---

### Post by Enigmapond on 2012-05-25
> **Watchlord said:**
> That seemed to work, thanks.

Cheers!:)

---


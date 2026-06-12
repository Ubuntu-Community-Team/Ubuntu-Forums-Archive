---
title: "Error appears when checking for updates"
date: 2009-08-05
forum: General Help
---

### Post by user 123 on 2009-08-05
When I check for updates I get the following error:

> An error occurred

The following details are provided:


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_GB.bz2)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.

I have all my repositories enabled. Anybody know what this could be? Thanks.

---

### Post by wojox on 2009-08-05
You may want to try going to System > Administration > Software Sources
and on the Ubuntu Software tab choose a different Server to download from.

---

### Post by nikhilk on 2009-08-05
> **user 123 said:**
> I have all my repositories enabled. Anybody know what this could be? Thanks.

I was able to ping archive.canonical.com, the server is up and running. From a browser I was able to access [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg) but got 404 for [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_GB.bz2)

Maybe you have some repositories wrong. See if you can access these files via browser or else use another server as wojox has already suggested.

---


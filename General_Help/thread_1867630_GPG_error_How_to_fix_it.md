---
title: "GPG error: How to fix it?"
date: 2011-10-23
forum: General Help
---

### Post by fantab on 2011-10-23
I wanted to update Oneiric Ocelot_64 today and I get the following **GPG ERROR**:

> [SIZE=1]W: GPG error: **[http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release**: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: **[http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release**: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [/SIZE] [SIZE=1]**[http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release**: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: **[http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release**: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: **GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release**: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch **[http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)**[/SIZE]  [SIZE=1]

W: Some index files failed to download. They have been ignored, or old ones used instead.[/SIZE] Please HELP me FIX this.

Thanks.

---

### Post by fantab on 2011-10-23
Ok... I fixed it.
[INDENT]```
$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```[/INDENT]

---

### Post by GadsdenMedia on 2011-10-23
Thanks Fantab - I'm dealing with the worst upgrade with Ubuntu I've ever had, and I think your post helped me clear up the last of the issues.

Now to update the remaining 500 or so packages that for some reason didn't get installed with I did the dist-upgrade.

---

### Post by talking Llama on 2012-02-23
THANK YOU! I've had this problem for a while now and this fixed it nicely. Thanks very much!

---


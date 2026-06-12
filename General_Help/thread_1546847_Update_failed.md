---
title: "Update failed"
date: 2010-08-05
forum: General Help
---

### Post by kabel_kabel on 2010-08-05
Dear all,

I'm getting the following message when i try to do update:

> 
An error occurred

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>

W: Failed to fetch [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg)  Something wicked happened resolving 'www.openprinting.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release](http://packages.medibuntu.org/dists/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


Do you know what is the problem and how can be fixed?

Thank you in advance,
Kabel

---

### Post by PeEllAvaj on 2010-08-06
Was Medibuntu set up successfully in the past?  If so, something probably broke temporarily on their side.  You could wait or ask over there for support.

If it never worked, I would manually go in and edit your /etc/apt/sources.list and /etc/apt/sources.list.d/* files to remove everything and start from scratch following the Medibuntu instructions again.

---

### Post by kabel_kabel on 2010-08-06
Medibuntu repository was working in the past. However, when i tried to do the update today, i got the following message:

> 
Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

and when i re-run the update utility i got the following message:

> 
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Something wicked happened resolving 'archive.getdeb.net:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

It seem like the error message is changing every time i run the update utility, kind of weird.

I guess i should do the medibuntu repository from scratch to see what will happen.

Thanks,
Kabel

---


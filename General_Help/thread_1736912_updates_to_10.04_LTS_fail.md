---
title: "updates to 10.04 LTS fail"
date: 2011-04-22
forum: General Help
---

### Post by Shobuz99 on 2011-04-22
I'm getting this error message when I run update manager
in 10.04 LTS. It just started happening today:
```


[B]Could not download all repository indexes

The repository may no longer be available or could not be contacted 
because of network problems.
If available an older version of the failed index will be used. Otherwise the repository will be ignored. 
Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch http://volatile.debian.org/debian-volatile/dists/etch/volatile/Release.gpg  
Something wicked happened resolving 'volatile.debian.org:http'
 (-5 - No address associated with hostname)
Failed to fetch http://volatile.debian.org/debian-volatile/dists/etch/volatile/main/binary-i386/Packages.gz  
404  Not Found [IP: 130.89.149.227 80]
Failed to fetch http://volatile.debian.org/debian-volatile/dists/etch/volatile/contrib/binary-i386/Packages.gz  
404  Not Found [IP: 130.89.149.227 80]
Failed to fetch http://volatile.debian.org/debian-volatile/dists/etch/volatile/non-free/binary-i386/Packages.gz
404  Not Found [IP: 130.89.149.227 80]
Some index files failed to download, they have been ignored, or old ones used instead.[/B]

```

Is there anything I can do to figure out why this just began today? I am totally baffled.
I'm using a Dell Inspiron 1300 and a HDD that is partitioned
for Ubuntu, Windows 2000 and the Dell Diagnostics.
I'm running wireless, connected to my Linksys network.
I've been running this config, on this laptop for about a month,
with no major issues until today.
My desktop is also running a dual boot between two HDD's
One with Ubuntu 10.04 LTS and the other with Windows XP SP3. 
No issues there, so far.

Thank you for any help or advice
Rick (shobuz99)

---

### Post by Shobuz99 on 2011-04-22
> **Shobuz99 said:**
> I'm getting this error message when I run update manager
in 10.04 LTS. It just started happening today:
```


[B]Could not download all repository indexes

The repository may no longer be available or could not be contacted 
because of network problems.
If available an older version of the failed index will be used. Otherwise the repository will be ignored. 
Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch http://volatile.debian.org/debian-volatile/dists/etch/volatile/Release.gpg  
Something wicked happened resolving 'volatile.debian.org:http'
 (-5 - No address associated with hostname)
Failed to fetch http://volatile.debian.org/debian-volatile/dists/etch/volatile/main/binary-i386/Packages.gz  
404  Not Found [IP: 130.89.149.227 80]
Failed to fetch http://volatile.debian.org/debian-volatile/dists/etch/volatile/contrib/binary-i386/Packages.gz  
404  Not Found [IP: 130.89.149.227 80]
Failed to fetch http://volatile.debian.org/debian-volatile/dists/etch/volatile/non-free/binary-i386/Packages.gz
404  Not Found [IP: 130.89.149.227 80]
Some index files failed to download, they have been ignored, or old ones used instead.[/B]

```

Is there anything I can do to figure out why this just began today? I am totally baffled.
I'm using a Dell Inspiron 1300 and a HDD that is partitioned
for Ubuntu, Windows 2000 and the Dell Diagnostics.
I'm running wireless, connected to my Linksys network.
I've been running this config, on this laptop for about a month,
with no major issues until today.
My desktop is also running a dual boot between two HDD's
One with Ubuntu 10.04 LTS and the other with Windows XP SP3. 
No issues there, so far.

Thank you for any help or advice
Rick (shobuz99)
Never mind. I fixed it. I must have checked that software source without realizing it. I'm dumb. Sorry for the trouble.
SOLVED

---


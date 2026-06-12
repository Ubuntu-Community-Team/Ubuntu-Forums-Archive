---
title: "Thunderbird repositary error"
date: 2009-11-10
forum: General Help
---

### Post by anator on 2009-11-10
Hi,

I have been facing a trouble in downloading the Thunderbird package from the Ubuntu repositary. I use Ubuntu 9.10. When I try to install the package the following message.

```

Need to get 12.1MB/12.2MB of archives.
After this operation, 36.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://in.archive.ubuntu.com karmic/main thunderbird 2.0.0.23+build1+nobinonly-0ubuntu1 [12.1MB]
Fetched 329B in 0s (384B/s)
[B]Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.23+build1+nobinonly-0ubuntu1_i386.deb  
Size mismatch[/B]

```

The problem seems to be the thunderbird_2.0.0.23+build1+nobinonly-0ubuntu1_i386.deb package. I would appreciate if you could help me in this. I cannot download the deb package directly from mozilla site because of download restrictions.

---

### Post by DougieFresh4U on 2009-11-10
Add the [Mozilla ppa]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=https%3A%2F%2Flaunchpad.net%2F~ubuntu-mozilla-daily%2F%2Barchive%2Fppa&ei=hln5Sq_CEI_knAfh98SFDQ&usg=AFQjCNEyIj2BpWpi2iMNEdzDHONVFg2xIg&sig2=XAUCQD5nYGhRnOGMYSKKXQ") then go to Synaptic and install Thunderbird from there. It will also have Thunderbird 3

---

### Post by zvacet on 2009-11-10
If you in future get to the similar problem go to the system>admin>software sources>and change server.

---


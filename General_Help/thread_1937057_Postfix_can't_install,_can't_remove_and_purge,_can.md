---
title: "Postfix can't install, can't remove and purge, can't reconfigure?"
date: 2012-03-07
forum: General Help
---

### Post by blaxbb on 2012-03-07
I messed up the configuration of postfix while installing it.  I removed it to set it up again, but I cannot as it fails with this error

```
Preconfiguring packages ...
Unmatched ( in regex; marked by <-- HERE in m/(^|[\.])ubuntu.( <-- HERE mail$/ at /tmp/postfix.config.15931 line 236, <STDIN> line 14.
postfix failed to preconfigure, with exit status 255
(Reading database ... 85462 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.8.5-2~build1_i386.deb) ...
Unmatched ( in regex; marked by <-- HERE in m/(^|[\.])ubuntu.( <-- HERE mail$/ at /var/lib/dpkg/tmp.ci/config line 236, <STDIN> line 14.
dpkg: error processing /var/cache/apt/archives/postfix_2.8.5-2~build1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 255
No apport report written because MaxReports is reached already

```

I have already tried to remove --purge it and dpkg-reconfigure it, but both of those fail as postfix isn't installed.

Any ideas on how I can get postfix installed or it's broken configuration cleared?

---

### Post by dcstar on 2012-03-08
> **blaxbb said:**
> I messed up the configuration of postfix while installing it.  I removed it to set it up again, but I cannot as it fails with this error

```
Preconfiguring packages ...
Unmatched ( in regex; marked by <-- HERE in m/(^|[\.])ubuntu.( <-- HERE mail$/ at /tmp/postfix.config.15931 line 236, <STDIN> line 14.
postfix failed to preconfigure, with exit status 255
(Reading database ... 85462 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.8.5-2~build1_i386.deb) ...
Unmatched ( in regex; marked by <-- HERE in m/(^|[\.])ubuntu.( <-- HERE mail$/ at /var/lib/dpkg/tmp.ci/config line 236, <STDIN> line 14.
dpkg: error processing /var/cache/apt/archives/postfix_2.8.5-2~build1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 255
No apport report written because MaxReports is reached already

```

I have already tried to remove --purge it and dpkg-reconfigure it, but both of those fail as postfix isn't installed.

Any ideas on how I can get postfix installed or it's broken configuration cleared?

Delete the /etc/postfix folder, delete the download .deb from the APT cache and use the correct tools to download and install it again.

---


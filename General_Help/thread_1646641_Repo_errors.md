---
title: "Repo errors"
date: 2010-12-16
forum: General Help
---

### Post by sefs on 2010-12-16
Hi,

Has anyone been experiencing troubles with the repos lately (I have also tried alternative ones) like in the last 2-3 days.

I am getting authentication errors, have they recently changed keys? Other types of errors as well.  Today's errors are...

```

Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Bad header line [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg  Bad header line [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.45 80]
Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/i18n/Translation-en_US.bz2  Bad header line
Failed to fetch http://ppa.launchpad.net/directhex/ubuntu/dists/lucid/Release.gpg  Bad header line
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/lucid/Release.gpg  Bad header line
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Bad header line
Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/lucid/Release.gpg  Bad header line
Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/Release.gpg  Bad header line
Failed to fetch http://ppa.launchpad.net/mail-notification-ssl/ppa/ubuntu/dists/lucid/Release.gpg  Bad header line
Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2  Bad header line [IP: 74.125.45.136 80]
Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz  0  Not Found
Failed to fetch http://deb.torproject.org/torproject.org/dists/lucid/main/binary-i386/Packages.gz  Bad header line [IP: 86.59.30.36 80]
Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz  Bad header line
Some index files failed to download, they have been ignored, or old ones used instead.

```

```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: BADSIG 7FB8BEE0A1F196A8 Launchpad PPA for Pidgin Developers

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Bad header line [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg  Bad header line [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2  Bad header line [IP: 91.189.88.40 80]

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/i18n/Translation-en_US.bz2  Bad header line

W: Failed to fetch http://ppa.launchpad.net/paul-climbing/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Bad header line

W: Failed to fetch http://ppa.launchpad.net/directhex/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Bad header line

W: Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/lucid/Release.gpg  Bad header line

W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/lucid/Release.gpg  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_pidgin-developers_ppa_ubuntu_dists_lucid_Release.gpg).

W: Failed to fetch http://ppa.launchpad.net/mail-notification-ssl/ppa/ubuntu/dists/lucid/Release.gpg  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_mail-notification-ssl_ppa_ubuntu_dists_lucid_Release.gpg).

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2  Bad header line [IP: 74.125.45.190 80]

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz  0  Not Found

W: Failed to fetch http://ppa.launchpad.net/pcf/miro-releases/ubuntu/dists/lucid/Release  

W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/lucid/Release  

W: Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/Release  

W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz  Bad header line

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by ajgreeny on 2010-12-16
No problem here in UK using UK servers.  What do you mean by alternative ones; different servers?

Try a change of the servers you use if you have not already done so, on the System->Administration->Software Sources dialog, temporarily, at least, or just wait a while and try again.

---

### Post by sefs on 2010-12-16
> **ajgreeny said:**
> No problem here in UK using UK servers.  What do you mean by alternative ones; different servers?

Try a change of the servers you use if you have not already done so, on the System->Administration->Software Sources dialog, temporarily, at least, or just wait a while and try again.

Is there a way to fully clean up apt, the cache etc.

Thanks.

---

### Post by ajgreeny on 2010-12-16
```
sudo apt-get clean
```
or
```
sudo apt-get autoclean
```depending on exactly what you want to clean up.
See ```
man apt-get
``` for all the info on using apt-get.

---


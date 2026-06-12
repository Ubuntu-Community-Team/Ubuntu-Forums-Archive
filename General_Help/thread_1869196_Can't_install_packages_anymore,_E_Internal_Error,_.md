---
title: "Can't install packages anymore, E: Internal Error, No file name for libxt6"
date: 2011-10-25
forum: General Help
---

### Post by pewpewaliens on 2011-10-25
After a failed update attempt with the built in update management program in oneiric, I can't install any package no more. When I try sudo apt-get install elementary-icon-theme for example, the response is

(Database inlezen ... dpkg: onherstelbare fatale fout, afbreken:
 kan bestandenlijst-bestand niet openen voor pakket `libxt6': Invoer-/uitvoerfout
E: Sub-process /usr/bin/dpkg returned an error code (2)

(Reading database ... dpkg: irrecoverable fatal error, aborting, can't open filelist-file for package 'libxt6': input-/output error
E: Sub-process /usr/bin/dpkg returned an error code (2))

When I try sudo apt-get install --reinstall libxt6 the response is:
E: Internal Error, No file name for libxt6

Could someone help me please?

---

### Post by Ghost|BTFH on 2011-10-25
Did you install Multiarch by chance?

If so, you may want to take a look [Here.]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/859188")

---

### Post by pewpewaliens on 2011-10-25
> **Ghost|BTFH said:**
> Did you install Multiarch by chance?

If so, you may want to take a look [Here.]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/859188")

No I've not, but thanks for the effort.

---

### Post by matt_symes on 2011-10-25
Hi

Open a terminal and type

```
sudo mv /var/lib/dpkg/info/libxt6 /var/lib/dpkg/info/libxt6.old
```

Then remove and purge the package.

Then try to install something using the terminal.

Kind regards

---


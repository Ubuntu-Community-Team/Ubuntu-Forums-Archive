---
title: "Trouble installing maven software"
date: 2012-04-01
forum: General Help
---

### Post by SwaroopKunduru on 2012-04-01
I am trying to install maven 3.0.4 but I am getting following error. Please let me know how to overcome and install maven3.0.4

Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-software-properties is already the newest version.
The following package was automatically installed and is no longer required:
  flashplugin-downloader
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 qmail
 qmail-run
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zvacet on 2012-04-02
```
sudo dpkg --configure -a
```

---


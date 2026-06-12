---
title: "rkhunter installation problem"
date: 2010-02-14
forum: General Help
---

### Post by uncle-c on 2010-02-14
Hi,
I want to install rkhunter but the proviso for installation is that I also install exim and other related packages :

```

uncle-c:~$ sudo apt-get install rkhunter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx
Suggested packages:
  eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl swaks
The following NEW packages will be installed
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx rkhunter
0 upgraded, 7 newly installed, 0 to remove and 23 not upgraded.
Need to get 2074kB of archives.
After this operation, 4829kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

Is there any means of installing rkhunter without having to install the associated packages as I do not want to have a mail system running on my desktop.

cheers
c

---


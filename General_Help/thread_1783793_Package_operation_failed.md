---
title: "Package operation failed"
date: 2011-06-16
forum: General Help
---

### Post by redale716 on 2011-06-16
I have been trying to remove samba. When I use Ubuntu Software Centre, I search for samba and select "remove". But that produces the following:

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 533784 files and directories currently installed.)

Removing samba-common-bin ...

update-alternatives: error: /var/lib/dpkg/alternatives/nmblookup corrupt: invalid status

dpkg: error processing samba-common-bin (--remove):

 subprocess installed pre-removal script returned error exit status 2

No apport report written because MaxReports is reached already
update-alternatives: error: /var/lib/dpkg/alternatives/nmblookup corrupt: invalid status

dpkg: error while cleaning up:

 subprocess installed post-installation script returned error exit status 2

Removing samba-common ...

update-alternatives: error: /var/lib/dpkg/alternatives/nmblookup corrupt: invalid status

dpkg: error processing samba-common (--remove):

 subprocess installed pre-removal script returned error exit status 2

No apport report written because MaxReports is reached already
Errors were encountered while processing:

 samba-common-bin

 samba-common


I have tried sudo apt-get update & upgrade & clean & install samba: all being suggestions on other websites (but all without success).

Can anyone help please?

---


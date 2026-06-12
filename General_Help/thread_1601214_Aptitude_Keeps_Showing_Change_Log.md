---
title: "Aptitude Keeps Showing Change Log??"
date: 2010-10-19
forum: General Help
---

### Post by EvilTchnlgy on 2010-10-19
I have a server that just recently started doing something that I have never seen before.
I am running 10.04 and connecting over ssh.

```
root@www:~# aptitude full-upgrade
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following NEW packages will be installed:
  linux-image-2.6.32-25-generic 
The following packages will be upgraded:
  apache2 apache2-doc apache2-mpm-prefork apache2-suexec apache2-utils apache2.2-bin apache2.2-common apt apt-transport-https apt-utils bzip2 clamav clamav-base clamav-daemon clamav-docs coreutils dmsetup dpkg dpkg-dev gzip lftp 
  libapache2-mod-php5 libavahi-client3 libavahi-common-data libavahi-common3 libbz2-1.0 libbz2-dev libc-bin libc-dev-bin libc6 libc6-dev libc6-i686 libclamav6 libdevmapper-event1.02.1 libdevmapper1.02.1 libgssapi-krb5-2 libk5crypto3 
  libkrb5-3 libkrb5support0 libpq5 libssl-dev libssl0.9.8 linux-image-2.6.32-24-generic linux-image-generic linux-libc-dev lvm2 man-db mountall openssl php-pear php5 php5-cgi php5-cli php5-common php5-curl php5-dev php5-gd 
  php5-mysql python-lazr.restfulclient screen sudo tar tzdata ureadahead 
64 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/117MB of archives. After unpacking 99.4MB will be used.
Writing extended state information... Done
Reading changelogs... Done
apache2 (2.2.15-1) unstable; urgency=low

  * This release adds and enables mod_reqtimeout, which limits the time
    Apache waits for a client to send a complete request. This helps to
    mitigate against certain denial of service attacks. In case of problems
    with slow clients, the timeout values can be adjusted in
    /etc/apache2/mods-available/reqtimeout.conf , or the module can be
    disabled with "a2dismod reqtimeout".

 -- Chuck Short <zulcss@ubuntu.com> Tue, 13 Apr 2010 09:09:34 -0400

(END) 
```
I have no idea why it is showing me that change log and can't figure out how to skip it...
Thanks in advance for the help!

---

### Post by EvilTchnlgy on 2010-10-29
bump
Still can't figure this out..

---


---
title: "'ls' command disconnects users on SFTP."
date: 2010-06-17
forum: General Help
---

### Post by ricessig on 2010-06-17
I'm using Ubuntu Server 10.04 and I'm also using OpenSSH 5.3. I have SFTP-only users in a chrooted environment. Users are able to login, change directories, upload and download files, but as soon they attempt to give the 'ls' or any list directory...the server disconnects. Any one that has a fix or has dealt with this before, let me know. Thanks!

---

### Post by ricessig on 2010-06-18
Help please? This issue is still bugging me.

---

### Post by mpz on 2012-06-26
I've been struggling with this for couple hours. Upgrading sssd to 1.5.x seems to work, unfortunately our production environment runs RHEL5.6 and I cannot upgrade. Hope this tip helps someone.

---

### Post by mpz on 2012-06-27
Just to confirm, after upgrading to sssd to v1.5.1 problem went away.

---


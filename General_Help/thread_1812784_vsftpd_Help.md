---
title: "vsftpd Help"
date: 2011-07-26
forum: General Help
---

### Post by chaos_efphect on 2011-07-26
I am trying to use a very very basic ftp server setup, as it stands there will be only 1 user. Right now its set to default to the home directory which i like a lot but i was wondering if there was a way i could create a folder in my home directory so when i connect on a remote computer it takes me there by default?

for example the folder would be on /home/ftp/FTP DIR or something like that and when i ftp in to my box it opens directly to there and if possible limits access to just that directory.

---

### Post by galvatron408 on 2011-07-26
yes you can! you have to create a chroot environment.

from the man page of vsftpd conf

**chroot_local_user** If set to YES, local users will be (by default) placed in a chroot() jail in their home directory after login. **Warning:**  This option has security implications, especially if the users have upload permission, or shell  access. Only enable if you know what you are doing. Note that these  security implications are not vsftpd specific. They apply to all FTP daemons  which offer to put local users in chroot() jails.

---

### Post by chaos_efphect on 2011-07-30
galvatron408 thank you very much, i will give it a try as soon as i get home. I had a feeling it would be that simple but the whoe chroot threw me.

---


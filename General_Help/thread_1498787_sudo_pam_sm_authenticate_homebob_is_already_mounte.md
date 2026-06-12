---
title: "sudo: pam_sm_authenticate: /home/bob is already mounted"
date: 2010-06-01
forum: General Help
---

### Post by sisyphus1978 on 2010-06-01
> 
Jun  1 12:15:42 desktop sudo: pam_sm_authenticate: Called
Jun  1 12:15:42 desktop sudo: pam_sm_authenticate: username = [bob]
Jun  1 12:15:42 desktop sudo: pam_sm_authenticate: /home/bob is already mounted

Any idea what's causing (at the root?) of this?

Maybe this is related:
> desktop gdm-session-worker[1396]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "bob"
Jun  1 09:25:46 desktop gdm-session-worker[1396]: pam_unix(gdm:session): session opened for user bob by (uid=0)
Jun  1 09:25:46 desktop gdm-session-worker[1396]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0

---

### Post by sisyphus1978 on 2010-06-01
Actually. I think this is to do with the fact that I installed Lucid over my Karmic install (but kept the /home). I had an encrypted home and swap with Karmic but don't with Lucid.

---

### Post by sisyphus1978 on 2010-06-01
So I found out what not to do:

> sudo mv /ecryptfs/ ecryptfs.old/That took me a few good hours to rectify. Thanks to my clonezilla img! D'oh.

---


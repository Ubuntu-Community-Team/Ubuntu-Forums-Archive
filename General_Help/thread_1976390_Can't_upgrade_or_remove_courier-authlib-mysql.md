---
title: "Can't upgrade or remove courier-authlib-mysql"
date: 2012-05-08
forum: General Help
---

### Post by galoisring on 2012-05-08
I upgraded to Xubuntu 12.04.

Whenever I check for updates, courier-authlib-mysql is listed as upgradeable. However when I try, I get the error message below. I get the same message when I try to delete the package.

How can I resolve this issue? I don't need the package anymore, so either a way to delete or upgrade would be fine.

Thanks!


Error code below:



Preparing to replace courier-authlib-mysql 0.63.0-3.1ubuntu1 (using .../courier-authlib-mysql_0.63.0-4build1_amd64.deb) ...
/var/run/courier/authdaemon/pid.lock: No such file or directory
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/run/courier/authdaemon/pid.lock: No such file or directory
dpkg: error processing /var/cache/apt/archives/courier-authlib-mysql_0.63.0-4build1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1

---

### Post by galoisring on 2012-05-11
Bump. Any suggestions? I'm sick of being reminded that I have 1 update available when it won't allow me to update.

---


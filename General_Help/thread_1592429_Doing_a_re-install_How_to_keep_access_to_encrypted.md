---
title: "Doing a re-install: How to keep access to encrypted home folder?"
date: 2010-10-10
forum: General Help
---

### Post by tbraun on 2010-10-10
Hello!

I'm still running 9.10, but now would like to install 10.10.
Now I'm wondering about how to keep access to my encrypted
home folder.

Usually, I don't do an 'upgrade', but a fresh re-install. I have
a separate /home partition, so normally this works just fine.
However, my home directory is encrypted (a feature that was
introduced with 9.10, I believe).

So, if I whack the system partition and do a fresh reinstall
there, will the new install still be able to read my home
directory? Or do I need to save a key file from somewhere?

Thank you very much...

Tom

---

### Post by mike2357 on 2010-10-10
I've never done a clean install with my entire home directory encrypted, but I've done several clean installs with encrypted folders in my home directory using "ecryptfs-utils" and related packages.

I always followed two practices.  First, I always assumed there would be a problem, so I made a temporary, unencrypted copy of my home directory and stored it on the device where I store backups.  Second, I chose the exact same logins and passwords as I had before the install.

Things have worked without any problems, except that I've had  to install the "ecryptfs-utils" package, reboot the machine, and then replace my home directory with the encrypted version from before the install.  That shouldn't be an issue for you since you would be selecting encryption as you install the new version.

---


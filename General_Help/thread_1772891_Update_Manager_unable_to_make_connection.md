---
title: "Update Manager: unable to make connection"
date: 2011-06-01
forum: General Help
---

### Post by strange_cathect on 2011-06-01
For the past two days, I have been unable to get a software update through the Update Manager.

I have several security updates waiting to be downloaded. However, upon attempt, I get the following:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-4ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-4ubuntu2.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-4ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-4ubuntu2.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-4ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-4ubuntu2.2_all.deb) 404  Not Found [IP: 91.189.92.166 80]

What's up with that?

---

### Post by philinux on 2011-06-01
> **strange_cathect said:**
> For the past two days, I have been unable to get a software update through the Update Manager.

I have several security updates waiting to be downloaded. However, upon attempt, I get the following:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-4ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-4ubuntu2.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-4ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-4ubuntu2.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-4ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-4ubuntu2.2_all.deb) 404  Not Found [IP: 91.189.92.166 80]

What's up with that?

Open update manager. Click on settings. Click the ubuntu software tab.

Change to a different server. Try Main.

---

### Post by strange_cathect on 2011-06-01
I just tried to update through terminal with sudo apt-get update and then sudo apt-get upgrade.

The update worked through that method.

---


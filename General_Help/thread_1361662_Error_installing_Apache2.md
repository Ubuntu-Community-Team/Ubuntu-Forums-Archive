---
title: "Error installing Apache2"
date: 2009-12-22
forum: General Help
---

### Post by eddiedoey on 2009-12-22
i am getting the error on ubuntu server 8.04.1 

sudo apt-get install apache2



Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main apache2-utils 2.2.11-2ubuntu2.3
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main apache2-utils 2.2.11-2ubuntu2.3
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main apache2.2-common 2.2.11-2ubuntu2.3
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main apache2-mpm-worker 2.2.11-2ubuntu2.3
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main apache2 2.2.11-2ubuntu2.3
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.2.11-2ubuntu2.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.2.11-2ubuntu2.3_amd64.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.11-2ubuntu2.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.11-2ubuntu2.3_amd64.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-worker_2.2.11-2ubuntu2.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-worker_2.2.11-2ubuntu2.3_amd64.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.11-2ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.11-2ubuntu2.3_all.deb)  404 Not Found

---

### Post by lewisforlife on 2009-12-22
I assume you are connected to the internet right?  Try first running:

```
sudo apt-get update
```

Then try again to install Apache.

---


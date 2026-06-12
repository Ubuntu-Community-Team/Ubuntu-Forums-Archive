---
title: "GPG error - No PUBKEY available"
date: 2010-11-27
forum: General Help
---

### Post by geovino on 2010-11-27
If been getting this error:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

is this a temporary situation?

---

### Post by plucky on 2010-11-29
> **geovino said:**
> If been getting this error:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

is this a temporary situation?

No you should add the GPG key,

From a terminal,copy and paste each command
 ```
gpg –keyserver keyserver.ubuntu.com –recv 02FDF932
gpg –export –armor 02FDF932 | sudo apt-key add -
sudo apt-get update
```

Post any errors

Good Luck

---

### Post by geovino on 2010-11-29
this solved the problem:

Originally Posted by sikander3786  
Add the missing GPG key by

Code:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
And then,

Code:
sudo apt-get update
Good Luck!
That fixed the problem. Thanks.

---


---
title: "apt-get update servers problem"
date: 2011-09-13
forum: General Help
---

### Post by appz on 2011-09-13
Hello!

When I run the commands 
```
apt-get update
apt-get upgrade
``` , the server give to me this response:

```
root@ubuntu:~# apt-get update
Err http://security.ubuntu.com natty-security InRelease

Err http://ro.archive.ubuntu.com natty InRelease

Err http://ro.archive.ubuntu.com natty-updates InRelease

Err http://security.ubuntu.com natty-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://ro.archive.ubuntu.com natty Release.gpg
  Temporary failure resolving 'ro.archive.ubuntu.com'
Err http://ro.archive.ubuntu.com natty-updates Release.gpg
  Temporary failure resolving 'ro.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/natty/InRelease

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Temporary failure resolving 'ro.archive.ubuntu.com'

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Temporary failure resolving 'ro.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

How can I fix this error, and how can I change address from [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) to [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

:)

---

### Post by raja.genupula on 2011-09-13
open update manager --> settings--> ubuntu software --> change your ubuntu server and then try again

---


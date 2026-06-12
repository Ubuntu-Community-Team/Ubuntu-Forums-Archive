---
title: "Error updating packages"
date: 2011-01-13
forum: General Help
---

### Post by John Long on 2011-01-13
I'm having an error when I try and update any of my packages.

The main part of the error reads:

E: Sub-process /usr/bin/dpkg returned an error code (2)
dpkg: parse error, in file '/var/lib/dpkg/status' near line 26112 package 'libgnomekbui4' field name.

I receive this same error for every package I try and reinstall or install or anything. I have three broken packages that seemed to originate the same time I began receiving the update error but I cannot reinstall the broken packages.

Any ideas? Thank you!!

---

### Post by wojox on 2011-01-13
Try copying you old one into your new one:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by cipherboy_loc on 2011-01-13
After that run:

```

sudo apt-get update && sudo apt-get upgrade -y

```

To update apt and then upgrade all packages.



Cipherboy

---

### Post by John Long on 2011-01-14
This worked great! Thank you! All is updated.

---


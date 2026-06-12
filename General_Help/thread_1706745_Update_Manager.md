---
title: "Update Manager"
date: 2011-03-14
forum: General Help
---

### Post by Wilbeer on 2011-03-14
Greetings All.......
My Update Manager is reporting "operation failed" with the Details drop box indicating the following information

[B]configuring packages ... 
Preconfiguring packages ... 
dpkg: parse error, in file '/var/lib/dpkg/available' near line 8991 package 'xserver-xorg-video-fbdev': 
 `Replaces' field, invalid package name ` 
dpkg: parse error, in file '/var/lib/dpkg/available' near line 8991 package 'xserver-xorg-video-fbdev':[/B]

Can anyone direct me how best to solve the computer malady?

Thanks All
Wilbeer

---

### Post by cipherboy_loc on 2011-03-14
Does running the update from the terminal (Applications -> Accessories -> Terminal) work? 

```

sudo apt-get update && sudo apt-get uprgrade

```If that doesn't work, post the output of:

```

head -n 8992 /var/lib/dpkg/available | tail -n 3

```
Thanks

Cipherboy

---


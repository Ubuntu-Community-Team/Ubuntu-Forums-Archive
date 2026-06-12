---
title: "Error Updating"
date: 2011-10-01
forum: General Help
---

### Post by DEdesign57 on 2011-10-01
I am new to Ubuntu and this is what I get when I try to check for updates:

Failed to download repository information

Check your Internet connection.

Details:
W:Failed to fetch [http://ppa.launchpad.net/unbuntu-wine/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/unbuntu-wine/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/unbuntu-wine/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/unbuntu-wine/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Krytarik on 2011-10-01
> **DEdesign57 said:**
> ```
W:Failed to fetch http://ppa.launchpad.net/**unbuntu**-wine/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
W:Failed to fetch http://ppa.launchpad.net/**unbuntu**-wine/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
E:Some index files failed to download. They have been ignored, or old ones used instead.
```
You made a typo when you added those PPA. ;-)

Remove it in "Software Sources -> Other Software" (under "System -> Administration" in classic Gnome), and if you haven't done so already, add the correct URL.

Greetings.

---


---
title: "Can't install Thunderbird"
date: 2010-09-19
forum: General Help
---

### Post by ESL on 2010-09-19
Is there a problem with the server where the packages are stored? Tried to install TBird using both the Software Centre and Synaptics Package Manager, but get this error message:

W: Failed to fetch URL [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_3.0.7+build1+nobinonly-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_3.0.7+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) /url
  404  Not Found [IP: 91.189.92.167 80]

George

---

### Post by WorMzy on 2010-09-19
Your package lists are out of date. Refresh them with ```
sudo apt-get update
```
Or open synaptic (System -> Administration -> Synaptic Package Manager) and click the refresh button.

If you still have no luck, then download the package manually from [here]("http://packages.ubuntu.com/lucid/thunderbird"), and install it by double clicking the deb file.

---

### Post by ESL on 2010-09-19
Many thanks. That solved it.

:)

---


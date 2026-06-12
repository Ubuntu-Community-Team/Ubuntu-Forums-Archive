---
title: "Failed to download package files"
date: 2011-10-16
forum: General Help
---

### Post by futralistic on 2011-10-16
I did a fresh install of 11.10 and now when I try to install some of my software by adding a PPA I get this error:

Failed to download package files
Check your internet connection

When I try to install the software through the terminal I get this message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1670495EDF629112

I guess my question is where do I get the public keys. The specific software I need the keys for are Openlp and Lyricue.

Thank you

---

### Post by oldos2er on 2011-10-16
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```
where KEYID is number shown in the error message.

---

### Post by futralistic on 2011-10-16
Thank you!! Works great!

---


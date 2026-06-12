---
title: "update manager help"
date: 2011-02-27
forum: General Help
---

### Post by JesMFN on 2011-02-27
i posted this before but im a new to ubuntu so the solution was like reading greek. so here it goes. i do an update check on my update manager. it loads all the way up to 79 out of 80. ib t just sits there. when i press cancel the following message comes up it says: (quick side note i have eebuntu 3.0 kernel 2.6.29-1-netbook and once again im new to ubuntu!! make it simple if you can. please :D)

 an error accrued: W: GPG error: [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81D820A9BB7A1A83
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Failed to fetch [http://www.statux.org/ubuntu/dists/jaunty/Release](http://www.statux.org/ubuntu/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by geoffmcc on 2011-02-27
[http://niechwiej.pl/2011/01/no_pubkey-a2019ea84e7532c8-ubuntu-opera-linux-linuks-2/?lang=en]("http://niechwiej.pl/2011/01/no_pubkey-a2019ea84e7532c8-ubuntu-opera-linux-linuks-2/?lang=en")

```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

---

### Post by JesMFN on 2011-03-01
tried entering it in the terminal it didnt do anything.

downloaded it and it said: couldnt import keys from file: archive.key Launch helper exited with unknown return code 0

---


---
title: "why i am getting this message"
date: 2010-11-11
forum: General Help
---

### Post by freefixkorma on 2010-11-11
hey guys i trying to reload synaptic and i am getting this message anyone please i will appreciate that 
thanks in advance

W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A

---

### Post by WorMzy on 2010-11-11
Open a terminal and run
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

(from the download page: [http://wicd.net/download.php](http://wicd.net/download.php))

---

### Post by Mark Phelps on 2010-11-11
Even if that works, you're still likely to encounter problems because I believe that Hardy (8.04) reached end of life some time ago and is no longer supported.

---

### Post by plucky on 2010-11-11
> **Mark Phelps said:**
> Even if that works, you're still likely to encounter problems because I believe that Hardy (8.04) reached end of life some time ago and is no longer supported.

Hardy is a LTS and is supported until April 2011

See [Here](https://wiki.ubuntu.com/Releases)

Good Luck

---


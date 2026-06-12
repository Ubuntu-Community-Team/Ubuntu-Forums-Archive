---
title: "Update failure"
date: 2010-06-16
forum: General Help
---

### Post by Deedlit on 2010-06-16
Haven't used our laptop in a few months (running Hardy), and it needed some updates. When we tried to update got the following error:

"signature verification failed gpg error tux family key expired failed to fetch [http://download.tuxfamily.org./blueman/dists/hardy/Release](http://download.tuxfamily.org./blueman/dists/hardy/Release)

Any suggestions would be greatly appreciated.

---

### Post by mörgæs on 2010-06-17
What happens if you try

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

---


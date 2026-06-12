---
title: "Pidgin PPA key help"
date: 2009-09-02
forum: General Help
---

### Post by mister_playboy on 2009-09-02
If you visit [[COLOR="Purple"]pidgin's site[/COLOR]](http://www.pidgin.im/download/ubuntu/) looking to obtain pidgin 2.6.1, you'll find the following command to add their PPA key to your list:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \ 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a
```

that command fails with:

```
gpg: "67265eb522bdd6b1c69e66ed7fb8bee0a1f196a" not a key ID: skipping

```

The correct command should be:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
```

---


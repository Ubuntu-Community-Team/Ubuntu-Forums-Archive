---
title: "can never get keys from keyserver. Why? o_O"
date: 2010-02-05
forum: General Help
---

### Post by quixote on 2010-02-05
Whenever I try to import a key from a keyserver when I add a repository to software sources, it just tries forever and times out.  For instance, following the instructions here: [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable) to add the key "CE49EC21" for the ppa:mozillateam/firefox-stable.  Whether I do it in the terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
``` or by clicking the link on their page, I get nowhere.  I've had this problem with other keys from keyserver.ubuntu.com too.

It suddenly occurred to me today that maybe my router is the problem.  It has a draconian firewall built in. (For instance, it won't allow incoming bittorrent traffic without me explicitly opening ports.)  So maybe, since I'm trying to receive a key, it's preventing the key from coming in??

Does anyone know why I'm having this problem getting keys?

If it could be a port problem, does anyone know which port(s) need to be open?

---

### Post by Vaphell on 2010-02-05
[https://bugs.launchpad.net/ubuntu-website/+bug/435193](https://bugs.launchpad.net/ubuntu-website/+bug/435193)

alternative servers:
keyserver hkp://subkeys.pgp.net
keyserver hkp://pgp.mit.edu
keyserver hkp://pool.sks-keyservers.net (random server)
keyserver hkp://keys.nayr.net
keyserver [http://keys.gnupg.net](http://keys.gnupg.net)
keyserver [http://wwwkeys.xx.pgp.net](http://wwwkeys.xx.pgp.net) where xx is a two-letter country code.

---

### Post by howefield on 2010-02-05
> **quixote said:**
> It suddenly occurred to me today that maybe my router is the problem.

It could be, but doesn't it use port 80, if you can browse you should be able to get the keys, if available.

More likely that it is the key servers letting you down, they often have issues.

---

### Post by wojox on 2010-02-05
I installed mine like this

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

```
sudo apt-get update
```

```
sudo apt-get install firefox-3.6
```

---

### Post by quixote on 2010-02-06
Thanks, all, for the replies.  I didn't even know you could use other keyservers, or that they had issues.  I just assumed they were all rock-stable and it was my fault....

And that looks like a nice simple install routine. I was planning on doing something unnecessarily complicated.  Thanks for the tip.

---


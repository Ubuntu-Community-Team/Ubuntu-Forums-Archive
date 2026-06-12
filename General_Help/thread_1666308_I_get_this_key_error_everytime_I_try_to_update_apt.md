---
title: "I get this key error everytime I try to update apt-get"
date: 2011-01-13
forum: General Help
---

### Post by ninjaaron on 2011-01-13
This is the message:
```
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA

```

This also keeps the Update manager from running. It doesn't effect synaptic for some reason, so I have been doing all my package stuff there.

What to do?

---

### Post by TeoBigusGeekus on 2011-01-13
See [this]("http://ubuntuforums.org/showthread.php?p=10322805").

---

### Post by ninjaaron on 2011-01-13
> **TeoBigusGeekus said:**
> See [this]("http://ubuntuforums.org/showthread.php?p=10322805").

This x5, so I stopped it. 
```
--2011-01-13 21:38:35--  http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg
Resolving packages.freecontrib.org... 34.52.53.34
Connecting to packages.freecontrib.org|34.52.53.34|:80... failed: Connection timed out.
Retrying.

```Just try again at another time, or is the http dead?



In other news, I'm completely in love with your avatar, and I have fantasies about using it in place of the Ubuntu icon in my GDM screen... I think I'll actually do that now...

---

### Post by TeoBigusGeekus on 2011-01-13
Trolling is a art...

PS: Pic or it didn't happen!

---

### Post by Zorael on 2011-01-13
Try this;
```
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 464AD83D
```

---

### Post by ninjaaron on 2011-01-13
Tried Zorael's command. BOOM! (of failure)
```
gpg: requesting key 464AD83D from hkp server keyserver.ubuntu.com
gpgkeys: key 464AD83D not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

---

### Post by Zorael on 2011-01-13
Hmm, indeed.

Any idea which PPA it's not finding the key to? Could it have been outright deleted?

---

### Post by ninjaaron on 2011-01-13
> **TeoBigusGeekus said:**
> Trolling is a art...

PS: Pic or it didn't happen!

[IMG]http://i4.photobucket.com/albums/y124/ninjaaron_0/Screenshot-1.png[/IMG]

no screenshots in gdm :(

---

### Post by TeoBigusGeekus on 2011-01-13
Awesome...!!!!

---

### Post by plucky on 2011-01-13
> **Zorael said:**
> Hmm, indeed.

Any idea which PPA it's not finding the key to? Could it have been outright deleted?

Try the right key ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4631BBEA
``` the last 8 numbers, not the first eight.

Good Luck

---

### Post by ninjaaron on 2011-01-14
> **plucky said:**
> Try the right key ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4631BBEA
``` the last 8 numbers, not the first eight.

Good Luck

There it is! Thanks!

---

### Post by Zorael on 2011-01-14
> **plucky said:**
> the last 8 numbers, not the first eight.
Augh, mea culpa.

---


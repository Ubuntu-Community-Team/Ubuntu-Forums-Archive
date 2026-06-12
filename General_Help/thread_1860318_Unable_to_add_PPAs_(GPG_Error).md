---
title: "Unable to add PPAs (GPG Error)"
date: 2011-10-14
forum: General Help
---

### Post by TheCosmicFrog on 2011-10-14
Ever since installing 11.10 Oneiric (64-bit), I haven't been able to add any PPAs. I've tried adding Spotify, Ubuntu Tweak and other PPAs. When I run *apt-get update* afterwards, I always get something along the lines of:

```

W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY XYZ123ABC

```

This is really frustrating. Any idea what's going on? I don't think I've changed any settings since installing...

---

### Post by ubupirate on 2011-10-14
In terminal:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key ID here>
sudo apt-get update
```Replace <key ID here> with the specific key ID.

---

### Post by TheCosmicFrog on 2011-10-14
> **ubupirate said:**
> In terminal:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key ID here>
sudo apt-get update
```Replace <key ID here> with the specific key ID.

Sorry, I should have been more specific. I've been adding PPAs using the "Add Source" button in Software Sources. I've been adding them in the form *ppa:example/application*

This doesn't normally require me to add keys like the way you posted. It's supposed to be automatic, isn't it?

---

### Post by ubupirate on 2011-10-14
> **TheCosmicFrog said:**
> Sorry, I should have been more specific. I've been adding PPAs using the "Add Source" button in Software Sources. I've been adding them in the form *ppa://example/application*

This doesn't normally require me to add keys like the way you posted. It's supposed to be automatic, isn't it?

So have I, and I still have to run those commands to get the public keys. I've had to run it for both Wine PPA and Zeitgeist PPA so far.

---

### Post by TheCosmicFrog on 2011-10-14
> **ubupirate said:**
> So have I, and I still have to run those commands to get the public keys. I've 
had to run it for both Wine PPA and Zeitgeist PPA so far.

Cheers, thanks. Oneiric bug I'm assuming?

---


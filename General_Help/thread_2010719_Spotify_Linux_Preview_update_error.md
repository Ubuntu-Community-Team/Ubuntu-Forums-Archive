---
title: "Spotify Linux Preview update error"
date: 2012-06-25
forum: General Help
---

### Post by Gargon0 on 2012-06-25
Hi. I installed spotify linux preview [http://www.spotify.com/us/download/previews/]("http://www.spotify.com/us/download/previews/") (scroll all the way down)last week and had no issue updating software manager until now. I am getting this error:

W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59

Anyone using spotify has this particular issue? I'd also like to understand why an issue like this has occured. Thank you.

---

### Post by dubbe on 2012-06-26
Spotify seems to have changed their public key. I got it to work by removing the old key and adding a new with:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
```

---

### Post by Lord Finga on 2012-06-26
> **dubbe said:**
> Spotify seems to have changed their public key. I got it to work by removing the old key and adding a new with:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
```

Works like a charm, thank you! :)

---

### Post by Gargon0 on 2012-06-26
thank you it worked like a charm!

---


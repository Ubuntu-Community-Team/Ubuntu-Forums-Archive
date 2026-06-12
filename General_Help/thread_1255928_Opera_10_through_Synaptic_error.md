---
title: "Opera 10 through Synaptic error"
date: 2009-09-02
forum: General Help
---

### Post by jamesisin on 2009-09-02
I have been using Synaptic to update Opera for some time now (see my [post]("http://www.soundunreason.com/InkWell/?p=197")). However, with the release of Opera 10 I am getting the following error using the setup described in my post when I ask Update Manager to fetch the new updates list:

"
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/etch/Release](http://deb.opera.com/opera/dists/etch/Release)

W: Some index files failed to download, they have been ignored, or old ones used instead.
"

How can I correct this and get Synaptic to run my Opera updates again?

---

### Post by filip007 on 2009-09-02
uninstall with Ubuntu Tweak and do fresh install from Opera.com

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Pitel on 2009-09-02
From [http://deb.opera.com](http://deb.opera.com):
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

Solved the problem for me.

---

### Post by gonzo.d on 2009-09-02
I found this [http://www.luchox.cl/blog/?m=200909](http://www.luchox.cl/blog/?m=200909) where
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F9A2F76A9D1A0061
``` and ```
gpg --armor --export F9A2F76A9D1A0061 | sudo apt-key add -
``` worked for me!

Good luck!

---

### Post by jamesisin on 2009-09-02
I see.  The old key expired and the same page ( [http://deb.opera.com/](http://deb.opera.com/) ) contains a new key.

---

### Post by bosvark on 2009-09-03
Thanks, this solved the problem for me too.

---

### Post by jamesisin on 2009-09-03
bosvark - Glad to be of service.

If anybody is interested, you can find my complete blog post here:

[http://www.soundunreason.com/InkWell/?p=1195](http://www.soundunreason.com/InkWell/?p=1195)

---

### Post by itsjareds on 2009-09-11
Fixed it for me too.

---


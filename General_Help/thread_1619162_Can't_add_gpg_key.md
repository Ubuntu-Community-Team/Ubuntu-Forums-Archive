---
title: "Can't add gpg key"
date: 2010-11-11
forum: General Help
---

### Post by abexs on 2010-11-11
Hi,

I have a problem adding the dd the gpg key for the Tor client using the Ubuntu 10.10
I followed every instruction at
[http://www.torproject.org/docs/tor-doc-unix.html.en#polipo](http://www.torproject.org/docs/tor-doc-unix.html.en#polipo)

I get this error when I try to reload in the synaptic manager
```
 W: GPG error: http://deb.torproject.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810 
```

Who can help?

---

### Post by plucky on 2010-11-11
> **abexs said:**
> Hi,

I have a problem adding the dd the gpg key for the Tor client using the Ubuntu 10.10
I followed every instruction at
[http://www.torproject.org/docs/tor-doc-unix.html.en#polipo](http://www.torproject.org/docs/tor-doc-unix.html.en#polipo)

I get this error when I try to reload in the synaptic manager
```
 W: GPG error: http://deb.torproject.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810 
```

Who can help?

From [Here](http://www.torproject.org/docs/debian.html.en#ubuntu)

From a terminal ```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```

The last line will reply OK if it works.

Good Luck


Post any errors.

---

### Post by abexs on 2010-11-11
I get:
```

gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpg: key 886DDD89: "deb.torproject.org archive signing key" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

and then OK

```

When I reload no errors anymore, thanks plucky

---


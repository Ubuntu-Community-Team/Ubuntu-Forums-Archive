---
title: "Why is rTorrent such a PITA to compile?"
date: 2009-08-27
forum: General Help
---

### Post by Phixion on 2009-08-27
It never used to be SO hard to compile rTorrent, what's changed?

I'm on Ubuntu server 9.04 and am getting this error:

```

checking for OPENSSL... configure: error: in `/tmp/libtorrent-0.12.5':
configure: error: The pkg-config script could not be found or is too old.  Make sure it
is in your PATH or set the PKG_CONFIG environment variable to the full
path to pkg-config.

Alternatively, you may set the environment variables OPENSSL_CFLAGS
and OPENSSL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I've followed all the guides I've found online but still, they aren't working, I can see it's a problem with openssl, but what should I be installing exactly?

Thanks.

---

### Post by cariboo on 2009-08-27
Is there a really compelling reason why you are compiling rtorrent from source, when it is available in the repositories?

---

### Post by Phixion on 2009-08-27
The version in the repositories is 0.8.2 as far as I recall, I'm installing the latest (0.8.5). I've had issues in the past with old versions of rTorrent not reporting to the tracker and eventually timing out, so I prefer to use the latest version.

I've managed to do it now after much messing about trying to find dependencies needed.

Every tutorial out there atm just doesn't work on Jaunty.

Those having issues, follow the ubuntugeek tutorial but you also need to install these: sudo apt-get install libssl0.9.7 libncurses5-dev libcurl4-openssl-dev libsigc++-2.0-dev

---


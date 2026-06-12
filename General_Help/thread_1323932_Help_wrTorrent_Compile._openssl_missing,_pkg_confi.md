---
title: "Help w/rTorrent Compile. openssl missing, pkg_config_path"
date: 2009-11-12
forum: General Help
---

### Post by clevertomato on 2009-11-12
I'm trying to compile the latest libTorrent and rTorrent. I started with libTorrent first. The result of ./configure tells me openssl is missing, but it isn't. It's installed in /usr/bin/openssl . So ./configure tells me that I may want to consider adjusting PKG_CONFIG_PATH. I tried adding /usr/bin/ to that variable by setting it and then using the export command, but still ./configure tells me the same thing. When I go to Karmic's Software Center, OpenSSL doesn't even show up in "get software" or "installed software", but like I said, it has been installed for some time now since I had Jaunty on here (before updating to Karmic).

What gives? I'm very new to compiling stuff in Linux, but still, this has me scratching my head. Last portion of ./configure is below:

```
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for OPENSSL... configure: error: Package requirements (openssl) were not met:

No package 'openssl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OPENSSL_CFLAGS
and OPENSSL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by iMisspell on 2009-11-12
Best of luck getting it going, three nights ago i installed it on my 8.04 server and like it alot... except for a hash-check problem on single file downloads.

Sorry i cant be of help to you here, but rtorrent is fun.

_

---

### Post by hal10000 on 2009-11-12
> When I go to Karmic's Software Center, OpenSSL doesn't even show up in "get software" or "installed software", but like I said, it has been installed for some time now since I had Jaunty on here (before updating to Karmic).

I'm pretty sure that openssl is in the repositories. Think about using synaptic instead of software-center.
But anyway, maybe during your karmic upgrade something went wrong with openssl.
You should just (re)install it:
```
sudo apt-get update
sudo apt-get install openssl
```

---

### Post by clevertomato on 2009-11-12
Tried it. Same problem.

Results of trying to reinstall openssl:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```and I received same results after trying ./configure again. It told me openssl is missing and that I may want to consider adjusting PKG_CONFIG_PATH.

I hope someone can help me solve this.

---

### Post by clevertomato on 2009-11-12
Turns out the missing package was NOT OpenSSL but libcurl4-openssl-dev. It would've been helpful for the error message to list that instead of simply listing that openssl was missing. UGH.

---


---
title: "Has anyone got.."
date: 2006-02-06
forum: General Help
---

### Post by cbudden on 2006-02-06
A .deb of Banshee 0.10.4 ?

Thanks.  I've tried to compile from source but it fails on
 ```

checking for AVAHISHARP... configure: error: Package requirements (avahi-sharp) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the AVAHISHARP_CFLAGS and AVAHISHARP_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

Thanks for your help.

---

### Post by kaamos on 2006-02-06
Avahi is available from [http://avahi.org/wiki/DownloadAvahi](http://avahi.org/wiki/DownloadAvahi) (check ./configure --help for mono bindings), but I think banshee relies on the newest mono so you have to get that as well.

I have newest banshee (but dbus doesn't work :( ) and newest beagle, but the installation was quite a hassle with a lot of packages installed outside the repos.

---

### Post by cbudden on 2006-02-06
Ok, I had tried with another repo, which worked but the program was unstable.  I used it to install the mono stuff and have now managed to install banshee, but I couldn't install  using checkinstall so I installed using make install.  Thanks.

---


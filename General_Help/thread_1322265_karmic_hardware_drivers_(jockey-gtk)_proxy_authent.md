---
title: "karmic hardware drivers (jockey-gtk) proxy authentication fails"
date: 2009-11-10
forum: General Help
---

### Post by jaythespacehound on 2009-11-10
Hi Folks,
I'm at a loss here.

Trying to install restricted drivers in 64 bit Ubuntu 9.10 through jockey-gtk.

I'm behind a university proxy that requires authentication.
The proxy settings are set in Synaptic as well as system -> prefernces -> network proxy.

It finds the drivers fine, but fails with:

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-185_185.18.36-0ubuntu9_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-185_185.18.36-0ubuntu9_amd64.deb) 407  Proxy Authentication Required 

This seems to be the same bug as in 9.04 here: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/373795](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/373795)

However in this case setting the http_proxy by doing
```
export http_proxy=http://username:password@proxy.bla.bla:port
```
then running gtk-jockey from command line results in the same error.

Any ideas anyone?
(Should I bug report this?)
Thanks!
Jay

---

### Post by jaythespacehound on 2009-11-10
Never mind. Turns out it does read the /etc/apt/apt.conf file which apparently seems to set the proxy server when you either set it in synaptic or through the system->pref->network proxy gui, but without the authentication details. Added them and all is well. Still should be fixed though!
Jay

---


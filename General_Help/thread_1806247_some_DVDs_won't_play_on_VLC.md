---
title: "some DVDs won't play on VLC"
date: 2011-07-17
forum: General Help
---

### Post by geovino on 2011-07-17
I'm running 10.04 64bit on an Acer Extensa 4420 laptop.

Lately when I try to play a music video off a DVD, VLC or Movie player will open and close and not play the video. But I tried a copied DVD music video and it opened and played just fine. Why would a copied video play and a regular store bought DVD not play? I've played many of these before so I wonder what has changed. 

any ideas?

---

### Post by thefasterblueone on 2011-07-17
You probably need to install "ubuntu-restricted-extras". Here is a link to help you install.

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by coffeecat on 2011-07-17
> **geovino said:**
> Why would a copied video play and a regular store bought DVD not play?

If the copied DVD has had the css encryption removed, if the store-bought DVD is encrypted and if you don't have libdvdcss2 installed, then that would be one explanation.

Install libdvdcss2 either by enabling the [Medibuntu repository](http://www.medibuntu.org/) and then using Synaptic or Software Centre (or apt-get).

Or...

Make sure you have libdvdread4 installed, and then:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by geovino on 2011-07-17
Thanks, I needed to install Medibuntu and then install libdvdcss2. 

Now it all works well. :)

---


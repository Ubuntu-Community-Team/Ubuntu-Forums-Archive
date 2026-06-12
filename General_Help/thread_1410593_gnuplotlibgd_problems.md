---
title: "gnuplot/libgd problems"
date: 2010-02-18
forum: General Help
---

### Post by queenofbabes on 2010-02-18
Hello, I hope this is the correct place to post this problem.

I originally had gnuplot installed (v4.2, patchlevel3) and was able to give png outputs just fine. I then downloaded the latest gnuplot from its website and installed it (using ./configure -> make -> make install), but now it said I had no png/jpg support.

I then googled and downloaded and installed libgd, libjpeg, libpng from their respective websites, reinstalled gnuplot, but now it doesn't work! When I set terminal to either jpg/png, it says it cannot find/open the font 'arial', then when I try to print output anyway, it says version of libgd and libpng/libjpeg is not compatible, resulting in segmentation fault.

Any ideas on what might have gone wrong here?

---

### Post by winglifter on 2011-02-27
I'm by no means a Ubuntu power user, but I think I finally worked through this problem myself.  

Ubuntu (at least for lucid) has the package libgd-dev under the name libgd2-noxpm-dev.  You can simply install it using synaptic, then do the ./configure (make sure here in the configuration summary section it says "yes" to png jpeg, etc), make, make install.

Here's the reference to the package.
[http://packages.ubuntu.com/lucid/libgd-dev]("http://packages.ubuntu.com/lucid/libgd-dev")

You might want to also consider installing the cairo and pango dev packages before configuring so you have access to the terminal pngcairo (it apparently does transparency).

---


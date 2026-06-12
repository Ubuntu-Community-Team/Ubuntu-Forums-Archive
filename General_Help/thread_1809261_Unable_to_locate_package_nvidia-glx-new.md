---
title: "Unable to locate package nvidia-glx-new"
date: 2011-07-21
forum: General Help
---

### Post by sepia.latimanus on 2011-07-21
Hi all,

I'm running Ubuntu 10.10 and trying to install CUDA. Everything is working fine except it looks like some openGL components are missing; when compiling the CUDA code samples I get the error 

/usr/bin/ld: cannot find -lGL

I went online and it looked like

'sudo apt-get install nvidia-glx-new'

would take care of this but then I get the error from the title of this post, that it can't be found. I'm afraid I'm a poor hand at installing components with Linux so if someone could help me out with this I'd be very appreciative.

Thanks!

S

---

### Post by CatKiller on 2011-07-21
*nvidia-glx-new* hasn't been used since Hardy. *nvidia-current* might give you better luck.

---


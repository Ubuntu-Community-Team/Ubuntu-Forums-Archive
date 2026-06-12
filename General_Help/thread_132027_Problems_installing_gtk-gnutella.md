---
title: "Problems installing gtk-gnutella"
date: 2006-02-17
forum: General Help
---

### Post by ingriffiths on 2006-02-17
ok, i think i've decompressed it correctly, but then i try to sudo ./Configure and it tells me that it can't find make and its life depends on it
any thoughts?

---

### Post by souteneur3190 on 2006-02-17
wait your trying to install limewire?

---

### Post by kaamos on 2006-02-17
Why are you trying to compile it? gtk-gnutella is in the repositories and can be installed with synaptic.

To enable universe: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
Synaptic: [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

### Post by souteneur3190 on 2006-02-17
if you are just do the following

sudo apt-get install alien (if you havent already)
Download limewire rpm from limewire.com
open terminal
sudo alein "drag the downloaded rpm to the teminil window"
it should say "limwirebla_blah.deb generated"
copy and that and type
sudo dpkg -i limwirebla_blah.deb generated
done!

---


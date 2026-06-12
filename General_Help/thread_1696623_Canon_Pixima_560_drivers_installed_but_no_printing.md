---
title: "Canon Pixima 560 drivers installed but no printing"
date: 2011-02-27
forum: General Help
---

### Post by ransom1 on 2011-02-27
My first day as Ubuntu 9.10 user. Downloaded drivers from Canon Europe and installed .deb package using G and all seemed ok but no actual printing occurs. System says all installed ok and indicates printing occurring but no physical printing happens. Checked printer on another PC and all ok. Has anybody got any ideas?

---

### Post by quixote on 2011-02-28
I'm not going to be any actual help just yet, but I had that exact model of printer and it did work.  I'll dig around and see if I can come up with any useful hints.

---

### Post by Deevad on 2012-01-03
I post here the solution, just to not let the thread without element of answer. 
For the Canon Pixma MP560 driver on ubuntu based system , the best is to install it via this ppa : [https://launchpad.net/~michael-gruz/+archive/canon](https://launchpad.net/~michael-gruz/+archive/canon)

```

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update

```

then open Synaptic or Muon ( your package manager ) , and search for 'canon'
You will see a long list of the driver. Install the one  "cnijfilter-mp560series"

To finish , add a new printer on your system setting / configuration panel ; you will be able to set up till the end with a proper driver.

sources : [http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

---


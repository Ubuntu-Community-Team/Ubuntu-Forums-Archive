---
title: "java"
date: 2010-05-08
forum: General Help
---

### Post by papaphil4 on 2010-05-08
is there a deb. file for java that I can get?  because I cannot get java bin file to do anything

---

### Post by linuxman94 on 2010-05-08
You can easily install it using this line of code.  Just open a terminal and copy&paste it into the window.  Make sure the Universe and Multiverse repos are enable in Software Sources in the system -> administration menu before you do.

```
sudo apt-get install ubuntu-restricted-extras
```

This will also install the codecs for playing restricted media formats.

---

### Post by Naitsirhc Hsem on 2010-05-08
use the software center under the applications menu.  search java

---

### Post by lmarmisa on 2010-05-08
If you wish to install the Sun Java VM, open Sypantic and select the package **sun-java6-plugin**. Other packages needed for the Sun Java Runtime Environment will be automatically selected. Verify that the universe, restricted and multiverse options of Synaptic are selected.

Best regards,

Luis

---

### Post by CoreyB. on 2010-05-08
> **lmarmisa said:**
> If you wish to install the Sun Java VM, open Sypantic and select the package **sun-java6-plugin**. Other packages needed for the Sun Java Runtime Environment will be automatically selected. Verify that the universe, restricted and multiverse options of Synaptic are selected.

Best regards,

Luis

And most importantly the partner repo, that is where sun-java6-plugin is located.

---

### Post by _0R10N on 2010-05-08
To get the bin working, you should move the file into the directory you want your java to be installed and then run
```
sudo sh java_bin_fyle
```
That's all!

---

### Post by papaphil4 on 2010-05-08
> **linuxman94 said:**
> You can easily install it using this line of code.  Just open a terminal and copy&paste it into the window.  Make sure the Universe and Multiverse repos are enable in Software Sources in the system -> administration menu before you do.

```
sudo apt-get install ubuntu-restricted-extras
```This will also install the codecs for playing restricted media formats.


thanks it worked

---


---
title: "Kde-minimal on 10.10 won't install"
date: 2011-01-11
forum: General Help
---

### Post by psycho5 on 2011-01-11
I'm trying to install the KDE desktop minimal on ubuntu 10.10 but it gives me an error to check my repositories saying that kdm is required but won't be installed, even though I have kdm in synaptic. 

How can I install KDE desktop? minimal applications version only. Thanks for the help.

should i disable 3rd party repos before installing? I don't think that should be necessary.

```

kde-minimal:
 Depends: kdebase-runtime but it is not going to be installed
 Depends: kdebase-workspace but it is not going to be installed
 Depends: kdebase-apps but it is not going to be installed
 Recommends: kdm but it is not going to be installed

```

---


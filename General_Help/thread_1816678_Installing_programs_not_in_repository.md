---
title: "Installing programs not in repository"
date: 2011-08-02
forum: General Help
---

### Post by tim.hoeffel on 2011-08-02
Hey All,
I'm trying to install Adobe Air written for Ubuntu 11.04 ([http://ubuntu-tweak.com/source/dajhorn-adobeair/](http://ubuntu-tweak.com/source/dajhorn-adobeair/)). I downloaded it and have it saved in "downloads". I tried opening it with Synaptic, but it won't recognize it. My hope is to use Air to run a Windows program. Air drives the database. I'm new to Ubuntu, so less tech is better. Thanks!

Tim

---

### Post by raja.genupula on 2011-08-02
> **tim.hoeffel said:**
> Hey All,
I'm trying to install Adobe Air written for Ubuntu 11.04 ([http://ubuntu-tweak.com/source/dajhorn-adobeair/](http://ubuntu-tweak.com/source/dajhorn-adobeair/)). I downloaded it and have it saved in "downloads". I tried opening it with Synaptic, but it won't recognize it. My hope is to use Air to run a Windows program. Air drives the database. I'm new to Ubuntu, so less tech is better. Thanks!

Tim


have you downloaded the .deb pkg or something else ?

---

### Post by aeiah on 2011-08-02
there are several ways, but in this instance, you'll be adding the developers own launchpad repository to the list of repositories that apt (and thus, synaptic) looks at. you can do this in a terminal with ```

sudo add-apt-repository ppa:dajhorn/adobeair

```

you'll then need to refresh your repository lists
```

sudo apt-get update
```

or you could do it in synaptic. you should see it in there once its been added and refreshed

---

### Post by gandaran on 2011-08-02
adobe air is in the package manager, I don't know if it's the latest version but still should work the same.
what type of package did you download, you can only install .deb packages with ubuntu software center any other package type have different ways to install.

---


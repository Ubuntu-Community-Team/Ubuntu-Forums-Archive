---
title: "Help with installing new software."
date: 2010-01-01
forum: General Help
---

### Post by mwade on 2010-01-01
Hello,

I am trying to install various new applications from different locations.  I just installed Ubuntu so this is a fresh install.  How do I search for new apps and then install them?  I thought that the Synaptic package manager did that but I don't get any results.  Is this now done in the Ubuntu software Center?  I don't want to have to deal with dependencies.

Thanks

---

### Post by zenxi on 2010-01-01
> **mwade said:**
> Hello,

I am trying to install various new applications from different locations.  I just installed Ubuntu so this is a fresh install.  How do I search for new apps and then install them?  I thought that the Synaptic package manager did that but I don't get any results.  Is this now done in the Ubuntu software Center?  I don't want to have to deal with dependencies.

Thanks
 
it depends if the software you want is in the ubuntu repos or not. if not you can find pre packaged .deb files on the web from places like getdeb.net or you can build software for source.

---

### Post by mwade on 2010-01-01
Hello,

Thanks for the info.  If I load other repositories software sources that should feed the Synaptic Manager correct?  For instance I am searching for software that was not found in the Synaptic manager, and that is what I use to download.

Thanks

---

### Post by oldos2er on 2010-01-01
Once you add a repository, you need to run **sudo apt-get update** or hit Reload in Synaptic.

---

### Post by kyle2595 on 2010-01-01
Another way to download software is through a PPA.  Some software will have a PPA to install them by, for example, Openshot has a PPA that you add to your software sources.

---


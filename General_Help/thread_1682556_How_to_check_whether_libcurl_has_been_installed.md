---
title: "How to check whether libcurl has been installed?"
date: 2011-02-06
forum: General Help
---

### Post by michaelkamms on 2011-02-06
Hi,

I am very new to ubuntu, I would like to ask whether it is possible to check whether libcurl has been installed?

Thanks

---

### Post by opensource10 on 2011-02-06
If Libcurl is an application...how about using this tutorial
[http://ubuntuforums.org/showthread.php?t=182201]("http://ubuntuforums.org/showthread.php?t=182201")

---

### Post by fabricator4 on 2011-02-06
> **michaelkamms said:**
> Hi,

I am very new to ubuntu, I would like to ask whether it is possible to check whether libcurl has been installed?


Yes, open synaptic package manager:

```

->System
    ->Administration
        ->Synaptic Package Manager

```

In the quicksearch box type "libcurl"

A green square next to the package means that it is already installed.  You should see this for python-pycurl, libcurl3 and libcurl3-gnutils.  You can select other packages if you want, and/or you can select the existing ones for re-installation.  When you select a package it may also add other packages if they are dependencies.

Click "apply" once you are done selecting, or just exit if you don't want to make any changes.

Chris

---


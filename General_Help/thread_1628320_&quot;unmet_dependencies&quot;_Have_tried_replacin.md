---
title: "&quot;unmet dependencies&quot; Have tried replacing to no avail"
date: 2010-11-22
forum: General Help
---

### Post by OxentroT on 2010-11-22
I have the following unmet dependencies:
```

The following packages have unmet dependencies:
  virtualbox-3.2: Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
                  Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
                  Depends: libssl0.9.8 (>= 0.9.8m-1) but 0.9.8k-7ubuntu8.4 is to be installed

```

I have tried re-installing these packages as well as "Edit > Fix Broken Packages" and "Edit > Apply Marked Changes" is not possible because Apply Marked Changes is not selectable.

Any Suggestions?

---

### Post by snowpine on 2010-11-22
Which Ubuntu release are you running? Make sure you follow the VirtualBox instructions for your *specific* Ubuntu release:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by OxentroT on 2010-11-22
I am using Maverick Meerkat and I have found that some of the repositories are not yet ready for the release or something. I have uninstalled and then reinstalled Vidalia by using Lucid repository entries and all seems to work well so far. However, the GUI still does not open when booting my system as it does when using Windows.

---


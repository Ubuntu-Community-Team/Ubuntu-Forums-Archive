---
title: "Purpose and restoration of /usr/share/app-install/desktop"
date: 2010-04-24
forum: General Help
---

### Post by veggen on 2010-04-24
Ok, so I managed to accidentally delete a number of files under /usr/share/app-install/desktop (stupid, yes). Could someone tell me what is the purpose of these files i.e. how bad is what I did? Also, is there a way to restore the files (i.e. regenerate them as undeleting under ReiserFS isn't really an option)?

Thanks for any insight.

---

### Post by veggen on 2010-04-24
These .desktop files seem to be related to launchers, but is that all?

---

### Post by veggen on 2010-04-25
No one knows what these files are for?

---

### Post by ks07 on 2010-04-25
No idea what they're for, but it seems to contain a .desktop (as you said, a launcher) for every program you have installed. Try installing a new program from synaptic and see if that adds a new one to the folder.

I don't think there's going to be an easy way to regenerate them. I can't see anywhere that they are used, so I wouldn't worry about it if everything is working as it did previously. If you're really concerned, and installing new programs adds a launcher, you could reinstall anything missing from there.

---

### Post by veggen on 2010-04-25
Ok, thanks for the advice :)

---

### Post by gmargo on 2010-04-25
It's a very simple fix to restore these files, especially since they all come from one (or two) package(s).

You can figure out the affected packages with just a little knowledge of the apt system.  A list of installed files for each package is kept in a **/var/lib/dpkg/info/<packagename>.list** file, so search these.

```

$ cd /var/lib/dpkg/info/
$ grep -l /usr/share/app-install *.list
app-install-data-partner.list
app-install-data.list

```So all the files under **/usr/share/app-install/**, on my 9.10 Karmic system, came from two packages: **app-install-data** and **app-install-data-partner**.  (My 8.04 Hardy system only has the non-partner one.)  So just reinstall these packages.
```

$ sudo aptitude reinstall app-install-data-partner app-install-data

```

---

### Post by veggen on 2010-04-25
Fantastic! Thanks you so very much for this explanation! Greately appreciated!

---


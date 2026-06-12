---
title: "Can't install libgtk2.0-dev on new Maverick install"
date: 2011-02-28
forum: General Help
---

### Post by NoJobyDesert on 2011-02-28
I can't install libgtk2.0-dev, or many of its dependencies, on a new-ish install of 10.10. Synaptic returns:
```

libgtk2.0-dev:
 Depends: libglib2.0-dev but it is not going to be installed
 Depends: libgdk-pixbuf2.0-dev but it is not going to be installed
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libatk1.0-dev but it is not going to be installed
 Depends: libcairo2-dev but it is not going to be installed
```

When I try libglib2.0-dev I get:
```
libglib2.0-dev:
  Depends: libglib2.0-0 (=2.26.1-0ubuntu1) but 2.27.2-0ubuntu1~build1 is to be installed
 Depends: libglib2.0-bin but it is not going to be installed
```

The only thing that could have possibly caused this is that I did use Synaptic's "Generate Package Download Script" to download many .debs offsite as this computer has dialup (things like GIMP, VLC, Kdenlive...)

I just don't get how I could be in such dependency hell with a brand new install, any ideas?

---

### Post by NoJobyDesert on 2011-03-02
Found out I obtained libglib2.0-0 version 2.27.2-0ubuntu1~build1 and not 2.26.0-0ubuntu1 because I have the Gnome3-builds PPA:
[http://www.ubuntuupdates.org/packages/show/255325]("http://www.ubuntuupdates.org/packages/show/255325")

Now I can't force version 2.26.0-0ubuntu1 without uninstalling half of my computer (GNOME 3 is not installed and the PPA is disabled now).

Help? :confused:

---


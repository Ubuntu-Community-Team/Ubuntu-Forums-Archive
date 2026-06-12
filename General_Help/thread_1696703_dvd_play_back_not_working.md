---
title: "dvd play back not working"
date: 2011-02-27
forum: General Help
---

### Post by walrus50 on 2011-02-27
can you help  no video playback:confused:

---

### Post by Dans564 on 2011-02-27
Legal Warning: Check with your local laws to make sure usage of libdvdcss2 would be legal in your area.

Ubuntu 9.04, 9.10, 10.04 (i386, amd64) and 10.10
Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line:

 ```
sudo apt-get install libdvdread4
```

Then open a terminal window and execute:

 ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Rebooting may be necessary.

---

### Post by Sef on 2011-02-27
Read [Restricted Formats Playing DVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").

---


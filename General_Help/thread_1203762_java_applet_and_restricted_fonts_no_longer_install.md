---
title: "java applet and restricted fonts no longer installed with ubuntu restricted extras"
date: 2009-07-03
forum: General Help
---

### Post by hurtstotalktoyou on 2009-07-03
Hey, all.

I just did a fresh install of 9.04 over 8.10, and ubuntu-restricted-extras didn't install java or msttcorefonts like it did before.  The fonts thing is no big deal, but I really need to be able to use java applets in firefox.

Is there a known solution for this?

Thanks!

---

### Post by Yvan300 on 2009-07-03
Last i heard, there wasn't a restricted extra's package for jaunty. But java and the fonts can be easily installed using synaptics, there is really no need for the restricted extras. All it does is just bundle everything to save time.

---

### Post by oldos2er on 2009-07-03
Yes, there is an ubuntu-restricted-extras package for 9.04 (xubuntu- and kubuntu-restricted-extras as well).

---

### Post by techstop on 2009-07-03
According to the ubuntu package search here;

[http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras)

ubuntu-restricted-extras does have Sun JRE and icedtea plugin. No msttcorefonts though, but that's hardly surprising.

---

### Post by michy99 on 2009-07-03
```
mike@ubuntumike:~$ apt-cache showpkg ubuntu-restricted-extras
Package: ubuntu-restricted-extras
Versions: 
31 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages
                  MD5: 422f580c10ca18603c1264963ae5252b


Reverse Depends: 
  non-free-codecs,ubuntu-restricted-extras
  winff,ubuntu-restricted-extras
Dependencies: 
31 - gstreamer0.10-plugins-ugly (0 (null)) gstreamer0.10-plugins-ugly-multiverse (0 (null)) ttf-mscorefonts-installer (0 (null)) adobe-flashplugin (16 (null)) flashplugin-nonfree (0 (null)) unrar (0 (null)) gstreamer0.10-plugins-bad (0 (null)) gstreamer0.10-plugins-bad-multiverse (0 (null)) gstreamer0.10-ffmpeg (0 (null)) libavcodec-unstripped-52 (0 (null)) gstreamer0.10-pitfdll (0 (null)) 
Provides: 
31 - 
Reverse Provides: 
```

No java, despite what the above link says.
```
apt-get install sun-java6-jre sun-java6-plugin
```

---


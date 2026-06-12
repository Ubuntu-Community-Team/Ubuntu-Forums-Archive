---
title: "How to install VLC source code tar.bz2?"
date: 2011-10-05
forum: General Help
---

### Post by cyberpunky2j on 2011-10-05
Hi,I am new to Linux.Currently I am using
Ubuntu 11.04 64-bit on my desktop.I do not have
an Internet connection.So I decided to download
the source code of the VLC media player and
install it offline.Can anyone suggest how to install
tar.bz2 files or .deb files on Ubuntu?

---

### Post by 4llf0rn0t on 2011-10-05
Usually, if it's a source package you would do the following from a shell
```

to extract tarball, tar xjvf vlc-1.1.11.tar.bz2
1. ./configure
2. make
3. sudo make install
```

But note that step 1 looks for dependencies e.g. compiler like GCC to be installed. If not found on your system you cannot build VLC for your system.
If your going online to install the dependencies, might as well install VLC from the repositories. Use Ubuntu Software Center or Synaptic Package Manager to search for vlc.

To install deb files:
```
sudo dpkg -i packagename.deb
```

---


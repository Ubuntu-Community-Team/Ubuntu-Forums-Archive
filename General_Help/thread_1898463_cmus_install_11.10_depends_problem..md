---
title: "cmus install 11.10 depends problem."
date: 2011-12-21
forum: General Help
---

### Post by casbahdk on 2011-12-21
I have tried to install the latest version of cmus from ppa, but have run into a dependency problem. cmus depends on libmp4v2-0, which has for some reason been deleted from the repositories. Any ideas for a solution?

---

### Post by 2F4U on 2011-12-21
As far as I can see, cmus is in the official repositories. Is there any special reason to install it from a ppa?

---

### Post by casbahdk on 2011-12-21
> **2F4U said:**
> As far as I can see, cmus is in the official repositories. Is there any special reason to install it from a ppa?

I have experienced some issues with sound in past versions of cmus, with both Debian and in Ubuntu, so I wanted to get the latest stable version of the program, hoping to avoid the problems.

---

### Post by casbahdk on 2011-12-22
I have tried removing the ppa and installing from the official repositories. I get prompted to configure a decnet node that would change the MAC addresses of my network cards. I chose not to configure a decnet node as I don't know what it is, but cmus doesn't appear to run without it being configured. What do I need to do and how do I do it?

---

### Post by casbahdk on 2011-12-22
Now I have tried to purge and reinstall, plus chosing for the decnet node to be configured. I get the following errors and cmus refuses to run:```
Setting up dnet-common (2.56ubuntu1) ...
dnet-common: Skipping configure of DECnet
update-rc.d: warning: decnet start runlevel arguments (S) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: decnet stop runlevel arguments (1) do not match LSB Default-Stop values (0 1 6)
Starting DECnet...done.
```

---

### Post by Toz on 2011-12-22
There seems to be some sort of issue with cmus dependencies. A decision was made to include Roaraudio support (see: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=609202]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=609202")) which in turn brought in a number of dependencies including decnet (see: [http://lists.alioth.debian.org/pipermail/pkg-multimedia-maintainers/2011-February/016089.html]("http://lists.alioth.debian.org/pipermail/pkg-multimedia-maintainers/2011-February/016089.html")). However, there seem to be problems with this (as you can see).

I was able to install and run cmus by not installing any of the dependencies via:```
sudo apt-get --no-install-recommends install cmus
```
...thus avoiding the whole decnet issue that you are experiencing. It seems to work fine, but I haven't tested all of its functionality.

---

### Post by casbahdk on 2011-12-23
Wow, thanks. I would probably have never sorted that out. I have run the following and cmus seems to be working```
sudo apt-get --no-install-recommends install cmus

sudo apt-get --no-install-recommends install cmus-plugin-ffmpeg
```

---


---
title: "dpkg was interrupted (cannot configure)"
date: 2009-08-22
forum: General Help
---

### Post by Pataforce8 on 2009-08-22
Hello, I was trying to install internal network drivers for an HP ze4900, and ended up interrupting the installing package with the drivers. (bad link to the file). I fixed my internet problem by switching to an external wifi card. Now my Synaptic won't open, telling me to configure the package and that 'dpkg' was interrupted. I ran the 'sudo dpkg --configure -a' command and it can't finish installing the package. Since I don't need that package anymore, is there anyway to make the 'interuppted dpkg install' message go away with out using the 'sudo dpkg --configure -a' command?

Thanks in advance!
-Patrick

---

### Post by wojox on 2009-08-22
Try:
```
sudo apt-get -f install
```

You may have to run this a couple of times:
```
sudo dpkg --configure -a
```

[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html#s-erros-comuns](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html#s-erros-comuns)

---

### Post by michy99 on 2009-08-22
If none of the above works, try```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by Pataforce8 on 2009-08-22
Thanks for the fast replies!

Output for 'sudo apt-get -f install'
      "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

Running 'sudo dpkg --configure -a' results in b43-fwcutter trying to connect to 'downloads.
openwrt.org|195.46.146.238|' but it never connects (tried up to seven times).

Running 'sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status' results in no output, but I suspect an action. I tried opening Synaptic after running said command, and was told that Synaptic could not get an exclusive lock. I looked for other programmes such as apt-get and aptitude but could not find them running so I am reboting now. I'll post a result soon.

---

### Post by Pataforce8 on 2009-08-22
Ah, to no avail.
After rebooting and trying to open Synaptic, I still get the error message 'E:_cache->open()failed, please report'.

---


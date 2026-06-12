---
title: "apt-get errors"
date: 2009-12-20
forum: General Help
---

### Post by Akalic on 2009-12-20
I have been working on a remote server on a dedicated host in order to run a game server. I managed to make the game server run after messing with the libraries and links. Since my laptop had all the libraries needed to run it, I used it as a template and basically copied and pasted the files the game server said wasn't there. I ran 'ldconfig' after each change to correct the links. Now when I try to run 'apt-get', 'apt-cache', etc, I get this error ```
apt-get: error while loading shared libraries: libstdc++.so.6: wrong ELF class: ELFCLASS32
```  I can't figure out how to correct this at all. I know my technique of just throwing the files together an praying it will work was crude. Any help is much appreciated.

---

### Post by Skidbladniir on 2009-12-20
Please post your /etc/apt/sources.list file here.

---

### Post by Akalic on 2009-12-20
# main repository    deb [http://ubuntu.mirror.server4you.net/ubuntu](http://ubuntu.mirror.server4you.net/ubuntu) hardy main universe multiverse re stricted  deb-src [http://ubuntu.mirror.server4you.net/ubuntu](http://ubuntu.mirror.server4you.net/ubuntu) hardy main universe multivers e restricted     # updates    deb [http://ubuntu.mirror.server4you.net/ubuntu](http://ubuntu.mirror.server4you.net/ubuntu) hardy-updates main universe multi verse restricted  deb-src [http://ubuntu.mirror.server4you.net/ubuntu](http://ubuntu.mirror.server4you.net/ubuntu) hardy-updates main universe m ultiverse restricted     # security updates    deb [http://ubuntu.mirror.server4you.net/ubuntu](http://ubuntu.mirror.server4you.net/ubuntu) hardy-security main universe mult iverse restricted  deb-src [http://ubuntu.mirror.server4you.net/ubuntu](http://ubuntu.mirror.server4you.net/ubuntu) hardy-security main universe multiverse restricted    # plesk autoinstall    deb [http://plesk-autoinstall.mirror.server4you.net/ubuntu/PSA_8.6.0/](http://plesk-autoinstall.mirror.server4you.net/ubuntu/PSA_8.6.0/) hardy all   deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe

---


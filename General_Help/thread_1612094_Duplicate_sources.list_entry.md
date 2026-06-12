---
title: "Duplicate sources.list entry"
date: 2010-11-02
forum: General Help
---

### Post by Punkristo on 2010-11-02
Everytime I update or install a program I get this message:

> W: Duplicate sources.list entry [http://deb.torproject.org/torproject.org/](http://deb.torproject.org/torproject.org/) lucid/main Packages (/var/lib/apt/lists/deb.torproject.org_torproject.org_dists_lucid_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

Even if I run apt-get update it wont fix it.

---

### Post by Barriehie on 2010-11-02
So comment out the duplicate line, or use uniq!  The file is /etc/apt/sources.list  You have to edit as root.

Using uniq:
```

# > su
password
cd /etc/apt    # Go to the directory
mv ./sources.list ./sources.list.bak     # Make a backup !!!
uniq -i sources.list.bak > ./sources.list  # Remove the dup. case insensitive
```

Using gedit:
```

gksu gedit /etc/apt/sources.list
```
Comment, with a # at the front, the offending duplicate line and then ctrl-s to save, ctrl-w to close, and ctrl-q to quit.

HTH

---


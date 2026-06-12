---
title: "error in Software Sources"
date: 2011-02-25
forum: General Help
---

### Post by alpetjr on 2011-02-25
In LinuxMint I am getting a error message   "Failed to fetch [http://packages.linuxmint.com/dists/julia/Release](http://packages.linuxmint.com/dists/julia/Release)  Unable to find expected entry  universe/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead." 
       Could someone help me with this? Thanks

---

### Post by dino99 on 2011-02-25
first browse these url (maybe some have changed)

clean the sources:

sudo rm /var/cache/apt/archives/*

then update upgrade again

---

### Post by alpetjr on 2011-02-25
rm: cannot remove '/var/cache/apt/archives/partial': Is a directory

---


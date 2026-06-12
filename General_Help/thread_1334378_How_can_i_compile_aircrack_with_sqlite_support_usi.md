---
title: "How can i compile aircrack with sqlite support using dpkg-buildpackage"
date: 2009-11-22
forum: General Help
---

### Post by sefs on 2009-11-22
To install regularly with sqlite support I would go ...

$ make sqlite=true

But I am building a deb so I am using dpkg-buildpackage 

debian/rules already has sqlite set to true, but it must also be specified on the command line.


These are the commands I am running so far ...

```

apt-get source aircrack-ng
sudo apt-get build-dep aircrack-ng
dpkg-buildpackage -b -us -uc -tc

```


How do i specify sqlite=true with dpkg buildpackage.

Thanks.

---


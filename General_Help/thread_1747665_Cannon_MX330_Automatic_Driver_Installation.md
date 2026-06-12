---
title: "Cannon MX330 Automatic Driver Installation"
date: 2011-05-02
forum: General Help
---

### Post by salemboot on 2011-05-02
Script below

```

#!/bin/sh
#MX330 driver hompage
#http://software.canon-europe.com/products/0010698.asp

cd ~/
mkdir tmp
cd tmp

echo -n "Installing Cannon MX330 printer drivers"

wget http://files.canon-europe.com/files/soft33558/software/cnijfilter-mx330series-3.10-1-i386-deb.tar.gz

wget http://files.canon-europe.com/files/soft33574/software/scangearmp-mx330series-1.30-1-i386-deb.tar.gz

tar vxf scangearmp-mx330series-1.30-1-i386-deb.tar.gz
tar vxf cnijfilter-mx330series-3.10-1-i386-deb.tar.gz

mkdir ~/mx330
find ./ -name \*.deb -exec cp {} ~/mx330 \;
cd ~/mx330
for i in *; do sudo dpkg -i --force-architecture $i; done

cd ~/


```

---


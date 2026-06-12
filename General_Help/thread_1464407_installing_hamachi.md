---
title: "installing hamachi"
date: 2010-04-28
forum: General Help
---

### Post by manav.g.garg on 2010-04-28
i have a hamachi-0.9.9.9-20-lnx.tar.gz file... how do install it from the terminal

---

### Post by klemes on 2010-04-28
first untar it by:

tar xzvf hamachi*.tar.gz

then cd into the resulting directory

cd hamachi*

Then :
```
./configure  #optional if it reports command not found go to the next step
make
sudo make install
```

And you are all set.:guitar:

---


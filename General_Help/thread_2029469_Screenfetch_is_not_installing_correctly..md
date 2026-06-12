---
title: "Screenfetch is not installing correctly."
date: 2012-07-19
forum: General Help
---

### Post by ThomasJazz on 2012-07-19
I am new to ubuntu and I am trying to get screenfetch to work but when I type screenfetch -s or anything to do with screenfetch, it says command not found. I have followed to directions on installing it and I was under the impression that I did it correctly. Can someone please give me a step-by-step how-to on it? Pictures would be greatly appreciated as well.

---

### Post by ThomasJazz on 2012-07-19
Bump, I am still stuck on this.

---

### Post by idoitprone on 2012-07-19
```
wget http://git.silverirc.com/cgit.cgi/screenfetch-dev.git/snapshot/screenfetch-dev-2.4.5.tar.gz

tar -zxvf screenfetch-dev-2.4.5.tar.gz

sudo mkdir /opt/bin

sudo mv screenfetch-dev /opt/bin/screenfetch

echo "export PATH=$PATH:/opt/bin" >> $HOME/.bashrc
```run these commands in order and it will work

just copy paste line by line in terminal

btw, the developer abandoned that repo

use this one, which i used in those commands above

[http://git.silverirc.com/cgit.cgi/screenfetch-dev.git/](http://git.silverirc.com/cgit.cgi/screenfetch-dev.git/)

open a new shell because the PATH have to be refreshed

---


---
title: "Nautilus-open-terminal &amp; xfce"
date: 2012-04-07
forum: General Help
---

### Post by rng on 2012-04-07
I installed nautilus and nautilus-open-terminal in xfce. It was opening xterm which I did not like. So I put following commands to try to change it to xfterm4, (which is a script in /usr/bin to open terminal with good font)
```
$ gsettings set org.gnome.desktop.default-applications.terminal exec xfterm4
$ gsettings set org.gnome.desktop.default-applications.terminal exec-arg "' -e'"
```
The problem is that the terminal now opens in home folder only and not in the folder being displayed in nautilus. How can this problem be corrected? I know it has something to do with /usr/bin/xfterm4 script. If this cannot be corrected, how can I reset all settings back to original?

---

### Post by Gremlinzzz on 2012-04-07
This might work:popcorn:
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---


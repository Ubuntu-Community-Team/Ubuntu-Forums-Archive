---
title: "How do I get ceni to setup network at boot?"
date: 2011-06-15
forum: General Help
---

### Post by Stuart O'mahony on 2011-06-15
Yep, so I use ceni to get online, and whilst ordinarily in other distros I need only configure the one time, and connection will establish itself at boot, here I have to set it up every time I enter the desktop. What do I need to do to have this happen?

---

### Post by Stuart O'mahony on 2011-06-18
A quick follow up to say that I have found this posting:

[http://crunchbanglinux.org/forums/post/78791/#p78791](http://crunchbanglinux.org/forums/post/78791/#p78791)

And have added an local.autostart file with the "(sleep 4s && sudo ceni)&" line, which init.d refers to, but as suspected, all this does is run the ceni ncurses setting program, not any kind of daemon.

Maybe the post is onto something where someone acknowledges that the driver must be installed before ceni is executed - hence the sleep, I guess. Be great to solve this issue!

---


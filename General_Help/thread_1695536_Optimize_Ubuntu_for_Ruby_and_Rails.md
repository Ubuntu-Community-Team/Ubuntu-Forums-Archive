---
title: "Optimize Ubuntu for Ruby and Rails"
date: 2011-02-26
forum: General Help
---

### Post by DJonsson2008 on 2011-02-26
We are building an Ubuntu server for an online use of a Ruby application and are shocked by the amount of CPU ruby eats
up.

One user doing a database search is enough for ruby instances to eat up 100% of the machines 2.8 ghz CPU. Memory use is slight, but ruby seems on Ubuntu to be a CPU hog.

In an attempt to correct this we recompiled ruby from source rather than use the apt-get deb packages, as we heard this should give us some improvement, but that made little if no difference.

There may be a setting in apache, ruby, rails phusion-passenger or elsewhere we are not setting or tweaking correctly.

Any tips?

---


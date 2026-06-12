---
title: "Problem redirecting serial data to file"
date: 2011-02-11
forum: General Help
---

### Post by tgu on 2011-02-11
Hi!

I'm trying to log serial data from a tty to a file, but for some reason fail to redirect the data output.

Outputing the data to the terminal I'm using is working just fine. Like this

> cat /dev/ttyACM0 | gawk '{print strftime("%y-%d-%m %T"), $0}'

If I redirect the output to a file nothing happens. The same thing happens if I pipe the output to tee.

Why doesn't this work?

Help greatly appreciated!

Thanks!

/Tobias

---


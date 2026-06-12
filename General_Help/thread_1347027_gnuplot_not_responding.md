---
title: "gnuplot not responding"
date: 2009-12-05
forum: General Help
---

### Post by andres.ordonez on 2009-12-05
Hi, thanks for reading.

(using ubuntu 9.10, gnuplot 4.2 patchlevel 5)

When I run plot the first time it works fine, but the second time it crashes (nothing happens), and when I try to close the plot window (greyed out and showing the first plot), it says:
"The window gnuplot (window id : 0) is not responding"
and I have to force quit

It seems it doesn't matter what's the plot, I mean, the same thing happens with:
gnuplot> plot sin(x)
gnuplot> plot cos(x)

or with:
gnuplot> plot "results.data" using 1:2 ....
gnuplot> plot ... (whatever)

I reinstalled the package but it didn't work.
I booted ubuntu 9.10 from a USB, installed gnuplot and it worked fine, so I guess it has to do with the configuration of X or something beyond what I know.

Any help would be appreciated.
Thanks again.

---


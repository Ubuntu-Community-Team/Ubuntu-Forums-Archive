---
title: "Octave+PlPlot?"
date: 2010-03-29
forum: General Help
---

### Post by davoudi on 2010-03-29
I just install Octave 3 and PlPlot 5.9.2-3 and it seems they are not linked well together. This is the error I take:

[COLOR=#ff0000]error: `plplot_octave' undefined near line 3533 column 1[/COLOR]
 [COLOR=#ff0000]error: called from `plsstrm'[/COLOR]
 [COLOR=#ff0000]error: evaluating if command near line 86, column 3[/COLOR]
 [COLOR=#ff0000]error: called from `figure' in file `/usr/share/plplot_octave/figure.m'[/COLOR]
 [COLOR=#ff0000]error: evaluating if command near line 19, column 3[/COLOR]
 [COLOR=#ff0000]error: called from `__pl_init' in file `/usr/share/plplot_octave/support/__pl_i[/COLOR]
 [COLOR=#ff0000]nit.m'[/COLOR]
 [COLOR=#ff0000]error: evaluating assignment expression near line 21, column 8[/COLOR]
 [COLOR=#ff0000]error: called from `__plt__' in file `/usr/share/plplot_octave/support/__plt__.[/COLOR]
 [COLOR=#ff0000]m'[/COLOR]
 [COLOR=#ff0000]error: called from `plot' in file `/usr/share/plplot_octave/plot.m'[/COLOR]
 [COLOR=#ff0000]error: near line 3 of file `/home/davoudi/Projects/test3/plplot.m'[/COLOR]

---

### Post by richardh on 2010-11-02
I am having same problem.

Octave can be quite nice and the basic plotting is OK, but not when you need to do extra things. The link to gnuplot does not work properly and gset/gshow dont work as advertised.

---


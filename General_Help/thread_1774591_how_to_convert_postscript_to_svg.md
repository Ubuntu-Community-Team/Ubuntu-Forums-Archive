---
title: "how to convert postscript to svg"
date: 2011-06-03
forum: General Help
---

### Post by engine on 2011-06-03
Both vector formats, right? but browsers will display svg and not postscript … so, when the score-writing app I use [mup] generates a postscript file as output, how can I convert it into an svg for use in an html page?

(Even better, convert an .eps so the result isn't A4 by default)

---

### Post by linuxinstalledfromhdd on 2011-06-03
[FONT=monospace]
Try:

```
gs -dBATCH -sOutputFile=myfile.jpg -sDEVICE=jpeg myfile.ps
```
[/FONT]

---

### Post by engine on 2011-10-04
```
gs -dBATCH -sOutputFile=myfile.jpg -sDEVICE=jpeg myfile.ps
```

Well, experimented with svg instead of jpg ;-} and the results, once I've mended the svg, are pretty good! it seems I need another option to handle multi-page .eps input, though &#8210; any more tips?

Thanks in advance.

---

### Post by cliddell on 2011-10-04
Be careful using Ghostscript's svg device, it is very limited, and hasn't had much attention recently. I'd hope that the layout for music scores should be fairly simple, so might be okay, but YMMV.

There's no such thing as a multi-page EPS file. To be multipage, it would have to be a PS file. I don't know the status of the GS svg device for multipage input.

Chris

---


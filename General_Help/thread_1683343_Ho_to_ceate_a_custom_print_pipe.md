---
title: "Ho to ceate a custom print pipe"
date: 2011-02-07
forum: General Help
---

### Post by bitterjug on 2011-02-07
I just installed [Graphtecprint]("http://vidar.botfu.org/graphtecprint") so I can drive our cutting plotter. graphtecprint likes to have a postscript file piped to it, so the following works, after doing print-to-file:
```

$ graphtecprint < output.ps

```Now, I want to make this as easy to use as selecting a printer. I guess I want to create a new local postscript printer that pipes the generated postscript into graphtecprint. When I went to System/Administration/Printing/Add Printer, it asked me for a URI. 

I'm happy with the command line but I don't know where to begin. Help welcome.

Mark

---


---
title: "using conky and aticonfig (fglrx) together"
date: 2011-12-17
forum: General Help
---

### Post by SnickerSnack on 2011-12-17
Hi,

I just put together a new desktop yesterday (which you can see in my sig), and I've been doing some conky tweaking today.

I can't seem to use execgraph correctly.  Basically, I want a graph that tracks gpu load much like cpugraph tracks cpu load.  I've been using variations on the following line:

```
${execgraph "aticonfig --odgc | grep load | cut -c 32-33 | tr -d \ "}
```

The command in quotes queries the proprietary ati driver for the gpu load and then snips the excess.  The result is a 2 digit number representing the percent load, but for reasons I can't discern, it doesn't work.  It results in an empty graph box.

I've done a bit of reading (starting with the conky documentation) and including this thread: [http://ubuntuforums.org/showthread.php?t=1622178&highlight=execgraph](http://ubuntuforums.org/showthread.php?t=1622178&highlight=execgraph), but I can't sort it out.

I've also tried setting the graph size manually, but that doesn't seem to help.

It's not really high priority, but given that I spent as much on my graphics card as I did on the proc, I'd like to get a shiny graph out of it.

---

### Post by SnickerSnack on 2011-12-19
I've made progress.

Thanks to this thread: [http://ubuntuforums.org/showthread.php?t=801328](http://ubuntuforums.org/showthread.php?t=801328), I changed the conky line to 

```
${execgraph ~/.conkyGPUload}
```

and put the following .conkyGPUload:

```

#!/bin/sh
aticonfig --odgc | grep load | cut -b 30-33 | tr -d \ | tr -d %

```

This works okay as long as the load isn't 0.  When the load is not 0, the graph displays, but conky crashes a lot.  When the load *is* 0, that line just diplays "0".

Any idea why conky is crashing?  Any idea how to get the graph to always display even then it's 0?

I tried changing the conky line to

```
${execigraph 5 ~/.conkyGPUload}
```

but that just gives the old result I was getting.  execigraph just doesn't seem to work.

Edit: When the output of the script is 0, the graph goes away and a "0" is displayed on that line of the conky output.  When the gpu load goes above 0, the graph returns and has the previous load also running in the graph.  execgraph just doesn't like the number 0?  Maybe I'm handing it a string instead of a number, but I don't know how to handle that.




Edit: Ooooookay.  I've found a dirty workaround:

```

#!/bin/sh
load=`aticonfig --odgc | grep load | cut -c 30-33 | tr -d \ | tr -d %`
expr 1 + $load

```

This is still quite annoying because *only* '1 + $load' works.  '1 * $load' does not   I'm trying other variations.

---


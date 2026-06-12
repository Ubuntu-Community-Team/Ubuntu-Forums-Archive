---
title: "Convert these bat commands?"
date: 2010-03-10
forum: General Help
---

### Post by Bluesplayer on 2010-03-10
Hi

Is it possible to convert these bat file commands to run under ubuntu?  What would the complete file look like?

```
START "" "<--url--->"
ping 1.1.1.1 -n 3 -w 2000 > null
START "" "<--url--->"
ping 1.1.1.1 -n 3 -w 2000 > null
```I think it would need to run off ubuntu desktop as the bat file opens the default browser when running.

Regards

---

### Post by geirha on 2010-03-10
The ping commands appear to be used as a sleep, to sleep for 4-6 seconds. The START commands ... I'm guessing those just open an url in the default browser (I'm assuming "<--url--->" is cencored url..?), so if my guesses are correct, an equivalent script for ubuntu would be:

```
#!/bin/bash
xdg-open "<--url--->"
sleep 5
xdg-open "<--url--->"
sleep 5

```

---

### Post by psusi on 2010-03-10
It also creates a file named "null" which is a bit silly.  On windows it is NUL not null.

---

### Post by Bluesplayer on 2010-03-11
> **geirha said:**
> The ping commands appear to be used as a sleep, to sleep for 4-6 seconds. The START commands ... I'm guessing those just open an url in the default browser (I'm assuming "<--url--->" is cencored url..?), so if my guesses are correct, an equivalent script for ubuntu would be:

```
#!/bin/bash
xdg-open "<--url--->"
sleep 5
xdg-open "<--url--->"
sleep 5

```

That looks like it will do the job!

Thanks

---


---
title: "Infinite /usr/bin/X11 directories?"
date: 2009-09-18
forum: General Help
---

### Post by bostonaholic on 2009-09-18
I was doing some cd'ing and noticed that within the directory
```
/usr/bin/
```
There is a pointer
```
X11 -> .
```
This will cause an infinite number of directories when cd'ing
```
cd /usr/bin/[TAB]
```
```
cd /usr/bin/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11
```

Is there a reason for this or is this a bug?  Could this cause security or memory issues?

---

### Post by bostonaholic on 2009-09-18
Created a quick bash script which will effectively be infinite until out of memory.  I haven't let it run for more than 10 seconds so I'm not sure how long it'd take for OOM to happen...

```
#!/bin/bash

pushd /usr/bin/ > /dev/null

while ls X11 > /dev/null ; do
	pushd X11 > /dev/null
done
```

EDIT: Now that I've run it, I see that nothing gets written to the file /dev/null so maybe OOM won't occur.  But conky is reporting insanely high CPU usage while the script is running.

---


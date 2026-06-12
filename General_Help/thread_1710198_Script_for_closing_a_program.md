---
title: "Script for closing a program"
date: 2011-03-19
forum: General Help
---

### Post by Ghost_Mazal on 2011-03-19
Lo guys , I have a very simple backup script like so:

```
#!/bin/bash
tar -cvf /media/Media_Drive/tarball/homemazal.tar /home/mazal
tar -cvf /media/Media_Drive/tarball/werkstok.tar /media/4D84-E758
```

What I want to know is what can I add to the top to automatically close Evolution before the tar's starts.
I'm worried that with Evolution open that some files might not be correctly backed up.

Thanx

---

### Post by WorMzy on 2011-03-19
```
killall evolution
sleep 3
```

Will send SIGTERM to any evolution process running, then wait for the process(es) to comply with the request.

Use

```
killall -9 evolution
```

if you'd prefer to send SIGKILL and force the process to terminate (may cause loss of data)

---

### Post by Ghost_Mazal on 2011-03-19
Thank you , works perfectly ;)

---


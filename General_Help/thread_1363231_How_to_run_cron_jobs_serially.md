---
title: "How to run cron jobs serially?"
date: 2009-12-24
forum: General Help
---

### Post by EnlistedSquire on 2009-12-24
Hi,

I have several scripts that backup various directories to a remote server. I want to put each one in /etc/cron.daily but I want to make sure the scripts don't run simultaneously.

What's the best way of going about this? Would it simply be to write another script that calls each backup script in turn and put that one script in cron.daily?

E.g.

```
#!/bin/bash
sh script1 && sh script2 && sh script3
```

Slightly more advanced, any ideas how could I write this script so that I don't have to manually add and remove specific backup scripts if I change them? I.e. run all scripts called *_backup one after the other.

Thanks in advance.

---

### Post by lloyd_b on 2009-12-24
> **EnlistedSquire said:**
> Hi,

I have several scripts that backup various directories to a remote server. I want to put each one in /etc/cron.daily but I want to make sure the scripts don't run simultaneously.

What's the best way of going about this? Would it simply be to write another script that calls each backup script in turn and put that one script in cron.daily?

E.g.

```
#!/bin/bash
sh script1 && sh script2 && sh script3
```

Slightly more advanced, any ideas how could I write this script so that I don't have to manually add and remove specific backup scripts if I change them? I.e. run all scripts called *_backup one after the other.

Thanks in advance.

For the first question, yes, have another script that is called from cron that runs the scripts one at a time is the easiest way to go.

For the second question, here's a simple script:```
#!/bin/bash

cd other

for SCRIPT in *; do
    "./$SCRIPT"
done
```This changes into a directory named other, gets a list of all files in that directory, and then executes them one at a time.  You should be able to expand on this to create a "backups" directory with all your backup scripts, and add/remove scripts to be run just by adding/deleting them from that directory.

Lloyd B.

---

### Post by EnlistedSquire on 2009-12-24
Great stuff, thanks. I'll give it a try.

---


---
title: "lpr prints more than one copy randomly"
date: 2012-02-13
forum: General Help
---

### Post by CrusaderAD on 2012-02-13
I'm using this command:

```
lpr -P "Dell" /home/user/invoices/*.pdf
```

and for some reason I get random duplicate prints. Usually with large batches. Any ideas? I added:

```
-# 1
``` to the options in hopes that it will fix this issue. Any ideas?

---

### Post by wyliecoyoteuk on 2012-02-13
Probably a spooling error, the PC struggles to keep up with the printer, and eventually you get a timeout, the job has printed, but the PC resends.
You could use a script with a wait command in it to ensure that each job is complete before another one starts.

---

### Post by CrusaderAD on 2012-02-13
> **wyliecoyoteuk said:**
> Probably a spooling error, the PC struggles to keep up with the printer, and eventually you get a timeout, the job has printed, but the PC resends.
You could use a script with a wait command in it to ensure that each job is complete before another one starts.

I thought about that, but I can't do a sleep (wait) command unless I'm looping all the files and printing them without a wildcard, right?

---

### Post by wyliecoyoteuk on 2012-02-13
You could use ls and loop it, something like this might work

```
cd ~/user/invoices
for i in `ls *.pdf`;do
lpr -P "Dell" $i 
wait
done
```

Of course, if there are spaces in the file names, it might fail, and you might have to add a double ampersand to make sure that the lpr command finishes.

---

### Post by wyliecoyoteuk on 2012-02-13
Actually, this would work better:
```

#!/bin/bash

cd ~/user/invoices
for i in *.pdf;do
lpr -P "Dell" $i &&
wait
done

```

---

### Post by CrusaderAD on 2012-03-22
> **wyliecoyoteuk said:**
> Actually, this would work better:
```

#!/bin/bash

cd ~/user/invoices
for i in *.pdf;do
lpr -P "Dell" $i &&
wait
done

```

Thanks for the suggestion! I'll give that a shot and post back.

---

### Post by CrusaderAD on 2012-05-09
The loop worked, thanks!

---

### Post by wyliecoyoteuk on 2012-05-10
Glad to help :)

---


---
title: "Defining multiple files in the command line."
date: 2012-09-05
forum: General Help
---

### Post by Wellywilly on 2012-09-05
I have been doing some file recovery with photorec. Before you can do anyhting with the recovered files you have to take ownership of them using- sudo chown -R username recup_dir.* . I have recovered multiple files and was wondering how to define batches of them in the above command? Or maybe there is another command for that?

---

### Post by Habitual on 2012-09-05
```
chown -R username recup_dir.*
``` 
is a "batch mode" type of operation, just rerun it after every recovery operation(s), but before restoration.

username would be your LoginID

---

### Post by Wellywilly on 2012-09-05
Gee whiz, I am such a doofus sometimes. I thought you had you replace the * with the number of the file that you wanted to delete. Got it now. Thanks for the help.

---

### Post by coldcritter64 on 2012-09-05
Please mark your threads as "Solved" using the "Thread Tools" menu at the top of the thread, if all is working OK for you. Thanks, coldcritter64. :)

---

### Post by Wellywilly on 2012-09-05
Sorry. Done now. Thanks again.

---

### Post by Habitual on 2012-09-05
> **Wellywilly said:**
> Gee whiz, I am such a doofus sometimes. I thought you had you replace the * with the number of the file that you wanted to delete. Got it now. Thanks for the help.

Glad it worked out!

---


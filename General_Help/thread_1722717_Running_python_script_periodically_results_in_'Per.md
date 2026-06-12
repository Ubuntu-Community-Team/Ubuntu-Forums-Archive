---
title: "Running python script periodically results in 'Permission denied'"
date: 2011-04-06
forum: General Help
---

### Post by polarise on 2011-04-06
Hi,

**Qualifier: **
Puzzling problem this. 

**Background: **
Here is my list of scripts. Note that some are executable.
```
paulk@node007:meta$ ll *.py
-rwxrwxr-x 1 paulk paulk  446 Apr  4 11:48 check_gene_dupl.py*
-rwxrwxr-x 1 paulk paulk  893 Apr  1 16:47 checkGTF.py*
-rwxrwxr-x 1 paulk paulk 1.2K Feb 26 19:46 convertGTF.py*
-rwxrwxr-x 1 paulk paulk  371 Mar 31 18:23 dec2bin.py*
-rwxrwxr-x 1 paulk paulk 5.0K Apr  6 09:46 expr.py*
-rwxrwxr-x 1 paulk paulk 2.1K Apr  4 10:15 genes.py*
-rwxrwxr-x 1 paulk paulk  268 Feb 19 14:07 in_pairs.py*
-rw-rw-r-- 1 paulk paulk   14 Mar 31 17:25 pickle_test.py
-rwxrwxr-x 1 paulk paulk 1.5K Feb 16 12:58 spliced_prop.py*
-rwxrwxr-x 1 paulk paulk   32 Feb 15 14:58 test_pysam.py*
```

I am connected to the server (node007) via SSH. The server is running Scientific Linux SL release 5.4 (Boron) but I am SSHing using Ubuntu 10.04. Occasionally, I get the following error from bash:
```
paulk@node007:meta$ ./expr.py
-bash: ./expr.py: Permission denied
```

**Temporary solution:**
To resolve this error I have to run some other command before I can run my scripts.

**Question(s):** 
What is causing this? 
How can I permanently solve this? (It's annoying!)

Kindly,
Paul

---


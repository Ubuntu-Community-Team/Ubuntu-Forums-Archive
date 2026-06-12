---
title: "Merge directory trees"
date: 2011-02-17
forum: General Help
---

### Post by mrwall-e on 2011-02-17
I have a couple directories in the following format:

+ Dir 1
----+ Dir A
-------- file1
----+ Dir B
-------- file2
+ Dir 2
----+ Dir A
-------- file3
----+ Dir C
-------- file2
+ Dir 3
----+ Dir B
-------- file2
----+ Dir C
-------- file1

My desired structure is:

+ Dir Final
----+ Dir A
-------- file1
-------- file3
----+ Dir B
-------- file2-1 [or something so that the two files don't overwrite]
-------- file2-2
----+ Dir C
-------- file2
-------- file1

Basically, I would like to combine all the directories that I can, without deleting/overwriting any files. I have looked at Rsync, but I could not find the correct options to do what I wanted.

Thanks

---

### Post by mrwall-e on 2011-02-19
Bump

---

### Post by paulproteus on 2012-06-15
I know it's late, but the tool called "unison" will do this for you very conveniently! You can install it from apt-get or the "software center".

---


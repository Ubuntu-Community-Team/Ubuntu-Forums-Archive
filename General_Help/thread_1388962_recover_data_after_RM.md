---
title: "recover data after RM"
date: 2010-01-23
forum: General Help
---

### Post by jesuisbenjamin on 2010-01-23
Hello there,

i wanted to delete a folder on my desktop using the rm command and ended up deleting my entire desktop content. I lost important documents.
Is there any way i can retrieve these?

Thanks.
B.

---

### Post by dcstar on 2010-01-24
> **jesuisbenjamin said:**
> Hello there,

i wanted to delete a folder on my desktop using the rm command and ended up deleting my entire desktop content. I lost important documents.
Is there any way i can retrieve these?

Thanks.
B.

Boot from a live CD, install the **recover** package and try and use that.

If you have continued to use your PC you have probable lost some of the files permanently, you should not use the command line for functions provided by the GUI unless you know what you are doing.

---

### Post by efflandt on 2010-01-24
You should practice safe rm'g by always doing **ls -al** with the filespec you are going to use, before doing rm (unless just removing specific files by full name).  Otherwise wildcards may match more than you intend (especially a lone * or with that with dot prefix).

I believe Linux file systems try not to overwrite anything right away (which minimizes having to defrag).  But once you reboot, all bets are off, which is why you should boot from CD or different (possibly external) drive to attempt recovery.

---

### Post by jesuisbenjamin on 2010-01-24
OK :( 

Is there any command line which moves files to the dust-bin instead? I would prefer to use that in the future indeed...

Thanks.

---


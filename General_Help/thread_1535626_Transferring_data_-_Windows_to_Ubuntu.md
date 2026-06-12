---
title: "Transferring data - Windows to Ubuntu"
date: 2010-07-21
forum: General Help
---

### Post by philfinn7 on 2010-07-21
Hi - I'm new to Linux/Ubuntu and have recently installed Ubuntu 10.04. Installation seems fine but now I want to get my data from Windows backup. I have transferred all the files (called Backup files 1.zip etc, i.e. all have spaces in the names)  and now I presume I need to unzip multiple files. Have searched and found this suggestion: - 

ls *.zip | xargs -n1 unzip (with space at end of command)

However, no luck - 'backup can't be found, file can't be found etc'

Can this be done under the gui rather than command line? Any help appreciated - so far I'm an Ubuntu convert - if I can just recover my years of data! - Phil

---

### Post by dcstar on 2010-07-21
> **philfinn7 said:**
> Hi - I'm new to Linux/Ubuntu and have recently installed Ubuntu 10.04. Installation seems fine but now I want to get my data from Windows backup. I have transferred all the files (called Backup files 1.zip etc, i.e. all have spaces in the names)  and now I presume I need to unzip multiple files. Have searched and found this suggestion: - 

ls *.zip | xargs -n1 unzip (with space at end of command)

However, no luck - 'backup can't be found, file can't be found etc'

Can this be done under the gui rather than command line? Any help appreciated - so far I'm an Ubuntu convert - if I can just recover my years of data! - Phil

```
unzip *.zip
```

---

### Post by philfinn7 on 2010-07-21
thanks - (duh, sounds too easy) - I'm testing this using only two files, but the message I get is: - 
 
archive: backup files 1.zip
caution: filename not matched: backup files 2.zip
 
and only the two original files are there. So, still something I don't understand.

---

### Post by philfinn7 on 2010-07-21
> **philfinn7 said:**
> thanks - (duh, sounds too easy) - I'm testing this using only two files, but the message I get is: - 
 
archive: backup files 1.zip
caution: filename not matched: backup files 2.zip
 
and only the two original files are there. So, still something I don't understand.
 
After experimenting, I think the answer to my question about unzipping multiple files, **where there are spaces in the name**, is ;-
 
unzip '*'.zip
 
thanks, Phil

---


---
title: "Output of ls command"
date: 2010-07-06
forum: General Help
---

### Post by agamjain on 2010-07-06
I need to write a shell script in BASH in which I need to exectue the ls command and then check whether it returns a NULL output or it lists some files. How will I do that?

---

### Post by dino99 on 2010-07-06
[http://unixhelp.ed.ac.uk/CGI/man-cgi?ls](http://unixhelp.ed.ac.uk/CGI/man-cgi?ls)

---

### Post by agamjain on 2010-07-06
> **dino99 said:**
> [http://unixhelp.ed.ac.uk/CGI/man-cgi?ls](http://unixhelp.ed.ac.uk/CGI/man-cgi?ls)
 I have read the manual for ls command. But it does not tell me how to check whether it generates an output or not. How to do that?

---

### Post by CannibalZerg on 2010-07-06
```

#!/bin/bash
files_ct=`ls -1A /var/tmp | wc -l`
if [ $files_ct -eq 0 ]
then
    echo "EmptyFolder"
else
    echo "NonEmptyFolder"
fi

```

---

### Post by techlive on 2010-07-06
many thanks

---

### Post by agamjain on 2010-07-06
> **CannibalZerg said:**
> ```

#!/bin/bash
files_ct=`ls -1A /var/tmp | wc -l`
if [ $files_ct -eq 0 ]
then
    echo "EmptyFolder"
else
    echo "NonEmptyFolder"
fi

```
Thanks a ton. I will try it and get back to you.

---


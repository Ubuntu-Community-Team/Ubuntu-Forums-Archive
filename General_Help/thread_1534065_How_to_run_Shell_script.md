---
title: "How to run Shell script"
date: 2010-07-19
forum: General Help
---

### Post by srikrishnan on 2010-07-19
Dear Friends,

I have Ubuntu 10.04 version in my Home system.

I want to learn writing shell scripts. So for that purpose I write my first "Hello World" file and saved it in my Documents folder as "sample.sh"

#!/bin/bash
echo "Hello World!"

In Terminal, i get into that folder and typed as below

./sample.sh

immediately I get the following message "Permission denied"

Eventhough I logged into my system through Administrator username and password.

Can anybody help me, what the error I have done or anything I need to enable before going to run shell scripts?

Thanks in Advance,
Srikrishnan

---

### Post by DrDevice on 2010-07-19
You have to make it executable first, by using ```
chmod u+x sample.sh
``` or run it directly by using```
sh sample.sh
```  Either way will work

---

### Post by spillin_dylan on 2010-07-19
You're SO close!  Have you checked the permissions of the file?  I am willing to bet that you forgot to flag the file as 'executable'.

```
$ chmod +x sample.sh
```

And then try again!

---

### Post by srikrishnan on 2010-07-19
Hi,

Thanks a lot for your immediate replies.

I will try 

Initially I run my shell scripts straightaway in my "cygwin" "xwin server" it works perfectly. So that I assumed this is the same procedure in Linux also.

Sorry for my confusion.

Thanks,
Srikrishnan

---


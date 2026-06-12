---
title: "How to install Python 3.1.2"
date: 2010-06-19
forum: General Help
---

### Post by selatoski on 2010-06-19
Ok, it's been a while since I've done command line work in Linux, so I need a refresher.  I have downloaded and extracted Python 3.1.2.  How do I install?  All of the HELP and README files are a little vague for me.  The README file tells me to do the following:

./configure
make 
make test
make install

...but when I type in "./configure" in a terminal session, it says "command not found".  

Anyone help a newbie out here?

Thanks in advance.
Scott L.

---

### Post by Pollox on 2010-06-19
Python should be installed by default.  If you specifically need Python 3.1.2 for some reason, that's in the repos to (just install python3-all or python3-minimal with whatever package manager you like).  Installing from the repos is a better idea than compiling it yourself.  I believe the error you are encountering is that you are running "./configure" when you are not in the directory that the files you downloaded are in.  You would need to use "cd" to make your way to that directory, where there should be a file called "configure".

---

### Post by selatoski on 2010-06-19
Thanks.  Had a brain freeze and couldn't thaw it out.

---


---
title: "Using cd command - message no such file or directory"
date: 2011-11-30
forum: General Help
---

### Post by randj on 2011-11-30
I'm trying to use the cd /   command ( to install a program), but when I try to change to another directory I get the reply "bash ----- no such file or directory", even tho' it is there. It does not matter which directory I choose.

Seems to be to do with "bash", but what is wrong?

Roger

---

### Post by bouncingwilf on 2011-11-30
Two quick points about cd (change directory) that sometimes catch people out if they are unfamiliar with unix type systems.

1. the directory name is case sensitive i.e. cd downloads (from home/user) will produce the error message you received. However cd Downloads will work. ( windows does not care about case).

2. If you precede the directory path with a / ( as appears in your post) then the system will try to change directory FROM the root filesystem /Downloads does not normally exist so you will get the error message you described.

Hope this solves your problem.

Bouncingwilf

---

### Post by raja.genupula on 2011-11-30
> **randj said:**
> I'm trying to use the cd /   command ( to install a program), but when I try to change to another directory I get the reply "bash ----- no such file or directory", even tho' it is there. It does not matter which directory I choose.

Seems to be to do with "bash", but what is wrong?

Roger

just post the output of ls command
  copy the terminal code here regarding what you did

---

### Post by randj on 2011-12-02
Thank you all for your answers.  I was aware of the upper/lower case sensitivity.  
I was not aware that preceding the path with a /  changed the directory from the root file system. I have never seen this mentioned in any guides etc.

Leaving out the first /  solved the problem.

Thank you.

---


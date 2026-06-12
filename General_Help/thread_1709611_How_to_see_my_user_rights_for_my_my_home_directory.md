---
title: "How to see my user rights for my my home directory"
date: 2011-03-18
forum: General Help
---

### Post by tonyps on 2011-03-18
Afternnon,
 
I am having a major brain meltdown, at least what is left of it...I cannot remember how to::confused:
list my user rights at the command prompt
how to change them back to what they should by so I have full rights to my directory and the stuff in it.
I am creating a basic web page for a class and I need to be able to launch it from a web browser pointing to my space.
Thanks for the pointers...
Tony ...

---

### Post by 5149.5 on 2011-03-18
ls-l will show permissions and chmod will change them.

---

### Post by r-senior on 2011-03-18
A start would be:

```

$ ls -ld ~
drwxr-xr-x 92 richard richard 4096 2011-03-18 18:35 /home/richard

```

Do you understand how to read the *drwxr-xr-x* part?

---

### Post by DanneStrat on 2011-03-18
Also have a look here:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Good luck.

---

### Post by tonyps on 2011-03-18
Thanks...so I looked up the chown command and it seems pretty vague on exactly how to do what I want to do, which is change the ownership of my files/folders in the root of my home so that I have control over them...when I type in teh url for the webpage I have, I get a permissions denied error, even though I can login and edit any of the files just fine...?
Again, thanks for the pointers!
Tony

---


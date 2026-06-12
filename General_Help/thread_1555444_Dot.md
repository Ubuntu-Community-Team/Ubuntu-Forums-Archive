---
title: "Dot"
date: 2010-08-18
forum: General Help
---

### Post by shashanksingh on 2010-08-18
What exactly does "." mean?
Does it mean "this" or does it mean "execute" as we use it before some scripts???
Also used as a prefix for hidden folders...

---

### Post by Ginsu543 on 2010-08-18
I suppose it's meaning depends on context. If you use it in the command line, "." means "here" or "in the current directory."

---

### Post by earthpigg on 2010-08-18
> **Ginsu543 said:**
> I suppose it's meaning depends on context. If you use it in the command line, "." means "here" or "in the current directory."

yup.

.. means one directory up.

type this in a terminal to see what i mean:

```
cd ..
```

when we use it before scripts, we aren't telling the system to execute... we are telling it "look ***here*** for this script, not in /usr/bin or /bin".

---

### Post by Ginsu543 on 2010-08-18
The "." is one of my favorite commands to use when I copy or move files. Instead of copying or moving a file **to** a destination I want, I prefer to navigate first to the destination folder and copy or move the file I want there **from** where it was using the "." command. This has two advantages, IMO. First, it gives me instant gratification since the new file will appear in the directory I'm already in when I issue the command. Second, if anything goes wrong, I don't have to go looking for the file all over my directory structure so I can erase it. If something goes wrong using the "." command, it just won't appear in my destination folder.

---

### Post by shashanksingh on 2010-08-22
One more context is when we use . <script to exeute> which I guess means to execute the script in this directory.

---

### Post by J V on 2010-08-22
No, as people have already stated, the . in that case signifies the CWD, if that dot was not there it would look in $PATH for the command, not find it, and throw an error. Which is why you use a . or the complete path before applications outside the $PATH

---


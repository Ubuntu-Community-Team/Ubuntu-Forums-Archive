---
title: "Command line help"
date: 2010-06-12
forum: General Help
---

### Post by Dark006 on 2010-06-12
Ok, I'm having some trouble trying to do an operation in the command line. I'm no stranger to it and use it whenever I can, but this I can't figure out. So what I'm trying to do is this; I have a directory with 5 sub directories with zipped files in them (for example, inside test/ resides test1 through test5, and each test1-5 has something.zip in it). So the command I was trying to run was

```
find . -name "*.zip" -exec unzip '{}' \;
```

This kinda works, except it extracts everything in the current directory (text/) I'm in. Is there a way to extract and them in their respective folders? Sorry if I'm making this sound more confusing than it is, if anyone needs me to clarify better I will.

---

### Post by golanbatrac on 2010-06-12
Use -execdir instead of -exec.

---


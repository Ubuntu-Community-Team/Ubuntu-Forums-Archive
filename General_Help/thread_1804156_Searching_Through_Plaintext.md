---
title: "Searching Through Plaintext"
date: 2011-07-14
forum: General Help
---

### Post by minigilani on 2011-07-14
Hi

I have multiple php files used to render a final webpage, but i can't seem to find where this one line is written. Is there a way to search through all the files automatically and find the right one?

The question, i supposed, boils down to whether or not i can search for a phrase through multiple files and find the right file.

Thanks in advance.

---

### Post by nothingspecial on 2011-07-14
You need grep with the -l flag

```
grep -l "phrase" /path/to/files/*
```

---

### Post by minigilani on 2011-09-04
> **nothingspecial said:**
> You need grep with the -l flag

```
grep -l "phrase" /path/to/files/*
```

Yes, but won't that just show me the line that phrase is present in, and not identify the file?

---

### Post by Doug S on 2011-09-04
The -l option will print the file name of the file for the first match of "phrase", instead of the line of the match itself. see also "man grep".

---


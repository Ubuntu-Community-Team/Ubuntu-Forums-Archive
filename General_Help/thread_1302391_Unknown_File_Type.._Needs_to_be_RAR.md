---
title: "Unknown File Type.. Needs to be RAR"
date: 2009-10-27
forum: General Help
---

### Post by Captain_Falafel on 2009-10-27
I've got a file split into several parts used with HJSplit. 
for example, they are: file.rar.001, file.rar.002, file.rar.003, etc.
Ubuntu recognizes the first file, file.rar.001, as a rar file, and gives it the 'zipped' icon, and in it's properties, the file type is rar. However, for the rest of the files, file.rar.002 and on, the file type is unknown, and when I try to extract the files with Archive Manager, it asks me my password, then goes through file.rar.001 first, extracts everything from file.rar.001 into a folder, then doesn't continue after it hits file.rar.002. 
When it fails, the folder that was created from file.rar.001 is erased.

how can I extract all the contents or get Ubuntu to recognize the rest of the parts as rar files rather than unknown files.

---

### Post by geirha on 2009-10-27
Sounds like one of the files may be corrupted. Try extracting it from the command-line and see if it gives you a useful error message.
```
unrar x file.rar.001
```

---

### Post by Captain_Falafel on 2009-10-27
> **geirha said:**
> Sounds like one of the files may be corrupted. Try extracting it from the command-line and see if it gives you a useful error message.
```
unrar x file.rar.001
```

Thanks for the quick response.. I don't think they're corrupt because other people have been able to extract the files and test them.

your trick allowed me to extract everything but about 15 MB from the first archive and keep those extracted files. However, it didn't finish the last 15 MB of the first rar file, and didn't even go into the second one saying it isn't a rar archive.

---

### Post by dcstar on 2009-10-27
> **Captain_Falafel said:**
> **I've got a file split into several parts used with HJSplit. **
for example, they are: file.rar.001, file.rar.002, file.rar.003, etc.
Ubuntu recognizes the first file, file.rar.001, as a rar file, and gives it the 'zipped' icon, and in it's properties, the file type is rar. However, for the rest of the files, file.rar.002 and on, the file type is unknown, and when I try to extract the files with Archive Manager, it asks me my password, then goes through file.rar.001 first, extracts everything from file.rar.001 into a folder, then doesn't continue after it hits file.rar.002. 
When it fails, the folder that was created from file.rar.001 is erased.

how can I extract all the contents or get Ubuntu to recognize the rest of the parts as rar files rather than unknown files.

Then **join** them before you extract them.

---

### Post by Captain_Falafel on 2009-10-27
> **dcstar said:**
> Then **join** them before you extract them.

How can I do that?

---

### Post by dcstar on 2009-10-27
> **Captain_Falafel said:**
> How can I do that?

```
cat file1 file2 > file1+2
```

---

### Post by Captain_Falafel on 2009-10-27
> **dcstar said:**
> ```
cat file1 file2 > file1+2
```

Did the trick! thank you soo much! :KS

---

### Post by guriinii on 2009-10-28
thank you, very helpful thread.

---


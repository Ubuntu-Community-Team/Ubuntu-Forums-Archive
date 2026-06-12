---
title: "How do you make a patch?"
date: 2006-06-09
forum: General Help
---

### Post by jsmidt on 2006-06-09
I have a file call it file A.  I canged one line in file A to create a new file, file B.  How do I make a patch that turns file A into file B.  Is there a package you use to make patches?

I tried to make a text file patch by hand but it won't work.  How do you make patches?

---

### Post by ape on 2006-06-10
So to patch text files, the easiest method is to use the 'diff' tool.  Here's how:

1. Create file1.
2. Create file2 with the modifications to it.
3. run the command `diff -u file1 file2 > file.patch`
4. you will end up with  a patch file that looks something like this:

```
--- file1       2006-06-10 00:12:29.000000000 -0700
+++ file2       2006-06-10 00:12:51.000000000 -0700
@@ -1,5 +1,3 @@
 This is a new
 Line and this is
-an Old line
 New
-Old

```

This shows you that two lines will be removed from file1 to create file2.

On subsequent runs (on different machines or whatever) you would run the command:

   ```
`patch -p0 < file.patch`
```

You should now see that file1 now looks like the file2 you originally created.

Good luck!

--Ape--

---


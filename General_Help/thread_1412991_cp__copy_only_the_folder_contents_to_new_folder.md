---
title: "cp ? copy only the folder contents to new folder"
date: 2010-02-21
forum: General Help
---

### Post by d3v1150m471c on 2010-02-21
I should know this but I figured I'd ask before I screw something up. What is the command to cp just and only the contents of a folder, not the folder itself, into a new folder?

```

cp -R /path/to/folder/ /to/new/folder/

```

Is this right?

---

### Post by raktarok on 2010-02-21
Please see the message below..

---

### Post by raktarok on 2010-02-21
Nope, that copies the entire folder. What you would want is something like this:

```
cp /path/to/folder/* /new/folder/
```

The * means match all files inside the folder.

But if you have hidden files (starting with a dot) inside the folder, then you will have to do this to move all files:

```
cp /path/to/folder/.* /path/to/folder/* /new/folder/
```

This does the job but there should be a way to shorten this command...

---

### Post by d3v1150m471c on 2010-02-21
```

d3v11@d3v11m4ch1n3:~/Projects$ cp -R folder1/* ~/Projects/folder2/

```

This ends up putting both the folder and the contents in the folder.

---

### Post by raktarok on 2010-02-21
> **d3v1150m471c said:**
> ```

d3v11@d3v11m4ch1n3:~/Projects$ cp -R folder1/* ~/Projects/folder2/

```

This ends up putting both the folder and the contents in the folder.

Remove the -R switch. It should work...

Or you can do this too:

cd /path/to/folder/
cp * /path/to/new/folder

---

### Post by d3v1150m471c on 2010-02-21
Score. That got it. Thanks :-)

---

### Post by raktarok on 2010-02-21
Yep, glad you got it! 

If you get confused about any other command in future, use man. Here, you could have done this:

```
man cp 
```

Press q to exit the manual.

---


---
title: "Adding Lines to File from Terminal"
date: 2009-08-04
forum: General Help
---

### Post by iEthan on 2009-08-04
Is there a command that will add a line of text to a file? I remember seeing something like this somewhere, but I don't remember.

---

### Post by BslBryan on 2009-08-04
```
gksudo gedit /path/to/file
```
or
```
sudo nano /path/to/file
```
or
```
vi /path/to/file
```

To name a few. ;-)

---

### Post by iEthan on 2009-08-04
> **BslBryan said:**
> ```
gksudo gedit /path/to/file
```
or
```
sudo nano /path/to/file
```
or
```
vi /path/to/file
```

To name a few. ;-)

I meant something like:
```

[cmd] [line] [file]
```

Without going into an editor.

---

### Post by doas777 on 2009-08-04
```

echo line > file1
cat file0 file1 > file2
cp file2 file0
rm file1 file2

```where file0 is the file you want to append to, and line is the string you want to append.
so you would concatenate (cat) your file, and the string of your line (in file1), and redirect the output of the command to file2. then copy file2 over file0, and delete the others.

well darn. why isn't cat taking a string? always used to (I think). this is messier than it need be...

---

### Post by Glyndwr on 2009-08-04
to add a line to the end of a file (if thats what you want):

echo "some text" >> filename.txt

A single '>' will overwrite the file so be careful :)

---

### Post by iEthan on 2009-08-04
Thanks! That was exactly what I was looking for!

---

### Post by drs305 on 2009-08-04
If it's a system file and you need sudo, you can add it like this:
```

echo "Enter a line of text" | sudo tee -a /path/filename

```

Don't forget the "-a" switch or it will overwrite rather than append.

---


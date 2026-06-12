---
title: "Rename a file with oriental character"
date: 2011-09-11
forum: General Help
---

### Post by Davebuntu11.04 on 2011-09-11
Hi, I have a problem with two files that both have an "oriental" character in the name of the file, I can not rename, delete or copy the files - please help!
One of the files has somehow managed to copy itself into the trash (probably through my various attempts to delete) and when I click empty trash the system hangs for a while then deletes everything in the trash folder except the file with the strange character in.
If anyone can tell me how to rename the files as its very frustrating

---

### Post by hakermania on 2011-09-11
oriental character?
Can you post it here?

---

### Post by Habitual on 2011-09-11
```
ls -i 
```
in directory that has this oriental character file.
Note the numerical value for the file(s).

Post them here.

---

### Post by gmargo on 2011-09-11
You'll need to go to the command line.  This is where wildcards come in handy.

Suppose your bad file is named "fooXXbar.txt" where XX is the weird character(s).

Using a shell wildcard you can refer to this file as "foo*bar.txt".  So, to list and rename that file from the command line:
```

ls -l foo*bar.txt
mv foo*bar.txt newname.txt

```

---

### Post by Habitual on 2011-09-11
Terminal> 
```
ls -i 
```
and note the inum value for the file(s) in the directory that has them/it.
```
find . -inum <inum value> -exec mv {} new-file-name \;
```

---

### Post by Davebuntu11.04 on 2011-09-12
It didn't work in Terminal, got the same error: Input/output error
The two file names are:
Eve&#31992;ts 
Ho&#31993;se
Maybe its important to mention that they are on an external drive with NTFS format (sorry I forgot to write that earlier :( )

---


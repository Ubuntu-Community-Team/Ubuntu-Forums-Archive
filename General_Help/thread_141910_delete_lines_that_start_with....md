---
title: "delete lines that start with..."
date: 2006-03-09
forum: General Help
---

### Post by yanik on 2006-03-09
Hi everyone,

I have this huge text file which contains the output of "ls -lR" of the /data directory on my server.  I'd like to have only the listing of the directories and permissions, but not individual files.  Is there a quick way of doing that?

I thought I might need a command that delete the lines that starts with "-" or "-rwx"

Anyone could help me out?  The text file is over 300 pages long....

Thanks

Yanik

---

### Post by ComplexNumber on 2006-03-09
there are command such as tail and head. what format is the file (ie what columns are there? eg filename, directory, filesize,etc)?

---

### Post by yanik on 2006-03-09
here's a few lines:

```
./Archives/2001/BHG Info/Fonts:
total 172
-rwxrwx---  1 fsadmin gestion 35384 Oct 19 11:33 bnkgothl.TTF
-rwxrwx---  1 fsadmin gestion 35908 Oct 19 11:33 bnkgothm.TTF
-rwxrwx---  1 fsadmin gestion 84068 Oct 19 11:33 nevisncn.TTF
```

I did ls -lR >> textfile while in /data

---

### Post by ComplexNumber on 2006-03-09
theres a command called grep and awk(a bit complex, though) that will enable you to do exactly what you want. i think head may do the trick too. i can't say any more than that because i'm not on linux at the moment.

don't bother deleting the lines that you don'w want because thats not necessary. just use grep or whatever to pick out the lines that you do want and then pipe that into another text file.

---

### Post by yanik on 2006-03-09
ok, 

```
grep -e -rwx textfile.txt
```

list exactly the lines I want to delete.  Now how would I pipe it to delete them?

Thanks again

---

### Post by lamego on 2006-03-09
Using ls for such purpose is not the best option.
You should use:
```
find /data -type d -exec ls -ld {} \;
```
This will find for all directories (type d) and execute ls -ld on them (to show you their permissions).

---

### Post by engla on 2006-03-09
[QUOTE=yanik]ok, 

```
grep -e -rwx textfile.txt
```

list exactly the lines I want to delete.  Now how would I pipe it to delete them?

Thanks again[/QUOTE]
grep -v will do a reverse match, listing the lines not matching, so

grep -ve -rwx textfile.txt > filtered_file.txt

should work

---

### Post by ComplexNumber on 2006-03-09
i thought that you were wanting to extract from one (large) text file only :confused:

---

### Post by yanik on 2006-03-09
thanks to all of you :)

---


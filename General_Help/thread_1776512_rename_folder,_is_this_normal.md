---
title: "rename folder, is this normal?"
date: 2011-06-06
forum: General Help
---

### Post by digbysellers on 2011-06-06
I thought I'd drawn a mental blank!? In the terminal, I typical rename folders using the mv commend eg; "$mv ExamRevision/ examRevision"
 - but I get this:

woz@woz-mint10 /media/StoreGo$ mv ExamRevision/ examRevision
mv: cannot move `ExamRevision/' to a subdirectory of itself, `examRevision/ExamRevision'

I wouldn't have guessed mv was not case-sensitive, but I had to substitute a different folder name before I could rename to the desired folder name. 
Computers are wasting our lives, 
that will teach me to study for an exam=)
Oh well.

---

### Post by pqwoerituytrueiwoq on 2011-06-06
linux file systems are case sensitive
since mv deal with file pats it is case sensitive

mv ./MYFILE ./myfile
the slah is the problem
mv ExamRevision/ examRevision
do this
mv ExamRevision examRevision
or
mv ./ExamRevision ./examRevision

---

### Post by Telengard C64 on 2011-06-06
I'm pretty sure it isn't the *filesystem* that is case sensitive. Various parts of the OS most definitely are case sensitive by default, but sometimes this can be changed.

```

foo$ ls
Alex  apples
foo$ ls a*
apples
foo$ shopt -s nocaseglob
foo$ ls a*
Alex  apples
foo$

```

---


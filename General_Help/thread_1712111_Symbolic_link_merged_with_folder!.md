---
title: "Symbolic link merged with folder!"
date: 2011-03-22
forum: General Help
---

### Post by wavygravy on 2011-03-22
I have done something very studpid I think and was wondering if there's any chance to recovery a folder.
I, for some stupid reason, merged a symbolic link with the actual folder, Thought I was doing something else.
Now the directory does not seem to exist and when I click on it there is an error saying 'The link '/directory/' is broken'
Any help thanks

---

### Post by TeoBigusGeekus on 2011-03-22
Was it an important directory?

---

### Post by wavygravy on 2011-03-22
yeah there were some work docs in it

---

### Post by TeoBigusGeekus on 2011-03-22
What was the exact command you used?

---

### Post by wavygravy on 2011-03-22
it was using the gui, I dragged the linked folder from the desktop to the dir that the original folder was in, when a message came up saying this named folder already exists do u want to merge, I clicked merge, after that the folder icon change to a text doc icon with an X in the corner. I can't change dir to it either using a terminal

---

### Post by TeoBigusGeekus on 2011-03-22
```
file nameofmergedfile
du -h nameofmergedfile
ls -l nameofmergedfile
```
Can you post us the output of these commands?

---

### Post by wavygravy on 2011-03-22
:~$ file /home/stephen/Documents/work/psychology\ bsc/3rd\ year 
/home/stephen/Documents/work/psychology bsc/3rd year: symbolic link in a loop
:~$ du -h /home/stephen/Documents/work/psychology\ bsc/3rd\ year 
4.0K    /home/stephen/Documents/work/psychology bsc/3rd year
:~$ ls -l /home/stephen/Documents/work/psychology\ bsc/3rd\ year 
lrwxrwxrwx 1 stephen stephen 52 2011-03-22 10:50 /home/stephen/Documents/work/psychology bsc/3rd year -> /home/stephen/Documents/work/psychology bsc/3rd year

---

### Post by TeoBigusGeekus on 2011-03-22
The only thing I can propose is to copy the entire thing to your desktop, for example, as a backup and then try to unlink it:
```
unlink /home/stephen/Documents/work/psychology\ bsc/3rd\ year
```

---

### Post by wavygravy on 2011-03-22
ok thanks I will try that

---

### Post by wavygravy on 2011-03-22
the whole thing disappeared, so looks like that folder is doomed, here's where my backups come in handy!
Thanks tho

---

### Post by TeoBigusGeekus on 2011-03-22
I'm sorry to hear that...
Watch out in the future.

---


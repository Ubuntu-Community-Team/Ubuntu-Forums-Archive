---
title: "Start My own program"
date: 2009-09-12
forum: General Help
---

### Post by coffeecake on 2009-09-12
How can i start my own C program by editing the passwd file?

---

### Post by shae on 2009-09-12
I am sorry, but what do you mean?  Are you trying to start a program you wrote or want to start writing a program?

---

### Post by coffeecake on 2009-09-12
i wanna start my compiled C program

---

### Post by bear24rw on 2009-09-12
```

gcc main.c -o main
./main

```?
need some more details on what you're trying to do

---

### Post by coffeecake on 2009-09-12
i mean i wanna run my compiled C program after a user logs in.

How do i do that?


How to add startup entry to /etc/passwd file?

---

### Post by coffeecake on 2009-09-12
my program name is a.out

---

### Post by yabbadabbadont on 2009-09-12
You don't run anything from /etc/passwd.  You would call your program from /etc/profile or /etc/bash.bashrc instead.

---

### Post by rob-ward on 2009-09-12
If you create a file called .bash_login in you home directory any commands you place in it should run when your user logs in.

Is that what you need?

---


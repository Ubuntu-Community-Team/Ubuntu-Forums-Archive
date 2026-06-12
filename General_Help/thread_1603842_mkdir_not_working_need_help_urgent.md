---
title: "mkdir not working need help urgent"
date: 2010-10-23
forum: General Help
---

### Post by programming on 2010-10-23
pid=fork();
            if(pid==0)
            {
                cout<<"Child has pid="<<pid<<endl;
            execlp("/bin/mkdir","mkdir -v myfirst",NULL);
            }
it gives error mkdir:opernads missing
Please tell me what m doing wrong m a beginner,programming in linux for the first time and have to submit this assignment in an hour :(

---

### Post by WorMzy on 2010-10-23
We can't do your projects for you. I suggest you read the mkdir man page. (Open a terminal and run 'man mkdir')

Next time, don't leave your projects to the last minute. ;)

---

### Post by programming on 2010-10-23
thanks for being so helpful dude
and thanks for being so judgemental.
I have been working on this project from the very first day and its just a part of it. using linux for the first time and its nt as easy as it might seem to you.anyways watever

---

### Post by geirha on 2010-10-23
Why do you want to replace your program with mkdir(1)? Why not just use the mkdir(2) system call?

The reason your exec is failing is because exec doesn't invoke a shell to parse it. You need to pass each argument as a separate argument. It won't split on whitespace.

See how bash does it:
```

cd /tmp
strace -e trace=process bash -c 'mkdir -v test'

```

---

### Post by programming on 2010-10-23
ok got it, thanks a lot dude :)

---

### Post by matt_symes on 2010-10-23
Hi 

try this

execlp("/bin/mkdir", "mkdir", "-v", "myfirst", NULL);

Might have duplicated your post geirha. Teach me to go for a coffee mid post

Kind regards

---

### Post by programming on 2010-10-23
problem solved by writing
execlp("\bin\mkdir","mkdir","myfirst",NULL)
Thank you all for saving me :)

---

### Post by Rocket2DMn on 2010-10-23
For the record, these forums do not provide homework support. Please see the [forum policy]("http://ubuntuforums.org/index.php?page=policy") that you agreed to when you registered here. Thread closed.

---


---
title: "Weird filesystem behavior, please help."
date: 2010-04-19
forum: General Help
---

### Post by mvorlov on 2010-04-19
I am trying to figure out a totally odd behavior of the ext3 filesystem mounted in Ubuntu 9.10

There is a Korn Shell script, part of which does the following in the loop:

while ((1)); do

mv dir1/file dir2;
if [[ ! -r dir2/file ]]; then
    echo "ERROR"
    ls -l dir1/* dir2/*
    exit 1
else
    echo "OK"
fi

done


Given that dir2/file always exists and that I do not move it asynchronously with "&", my script should never hit the "ERROR" statement. The odd thing is that it does, and quite randomly (no pattern at all). However when it does hit the ERROR case, ls -l prints that file is in dir2 and it is readable! I tried using "-e" instead of "-r" test - no luck.

I never seen anything like this in 10 years of my programming experience. Same script worked fine on Fedora 11, and yet it wouldn't work on Ubuntu.

Any ideas how to solve this would be greatly appreciated.

---

### Post by cjhabs on 2010-04-19
The only thing I noticed was that you are using an "elif" with no check rather than "else". Maybe the Ubuntu bash shell doesn't care for that?

---

### Post by mvorlov on 2010-04-19
> **cjhabs said:**
> The only thing I noticed was that you are using an "elif" with no check rather than "else". Maybe the Ubuntu bash shell doesn't care for that?

You are right, it is else, not elif - a silly typo. I am using ksh, not bash.

Apparently the filesystem schedules the "mv" and occasionally the if-test kicks in before the i/o write is committed. 

Although I could use sleep 1 or something like this, I'd still like to get to the core of the problem.

---

### Post by cjhabs on 2010-04-19
> **mvorlov said:**
> You are right, it is else, not elif - a silly typo. I am using ksh, not bash.

Apparently the filesystem schedules the "mv" and occasionally the if-test kicks in before the i/o write is committed. 

Although I could use sleep 1 or something like this, I'd still like to get to the core of the problem.

I am interested in how did you came to that conclusion - the only time I have ever seen this was under Unix a long time ago where there was a bug in the disk drive firmware. This just doesn't seem right - it is a very basic operation - I would expect lots of things to fail sporadically if this were the case.

---


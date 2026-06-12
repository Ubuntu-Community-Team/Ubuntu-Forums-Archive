---
title: "quick stupid question....readlink and xargs"
date: 2009-07-25
forum: General Help
---

### Post by ooobooontooo on 2009-07-25
Why does this not work:
```
readlink [-n] Examples | xargs cd
```
Where "Examples" is a symbolic link to /usr/share/example-content/
If I do this it works though...:
```
a=`readlink [-n] Examples`
cd $a
```

By [-n], I mean either with or without.
Thanks in advance.

---

### Post by DaithiF on 2009-07-27
Hello,
when you use a pipe, the process at the far end of the pipe is a child process, and a child process can't affect the current directory of its parent.

so you have to use the second form, where the cd command is the parent, and you pass it an argument that you can construct however you want.

cheers
d

---

### Post by ooobooontooo on 2009-07-27
Makes sense. Thanks, but how come the error I get is:
```
xargs: cd: No such file or directory
```
I would expect that it would change directory within the subshell and exit silently, with of course the end result being that the current directory did not change.

---

### Post by DaithiF on 2009-07-27
yea, good question, i wondered about that myself too at first.  I believe the answer is that  cd is a builtin command, ie. its part of the shell itself.  xargs constructs a command and runs it, but not via the shell, and so the 'cd' command is not found -- leading to the error.  If you had xargs explicitly run a shell and have that shell run the cd command, you wouldn't get the error  (but of course you still won't affect the current directory of the parent process, so its all a bit of a moot point :) )

echo "one" | xargs sh -c "echo $0"
one
echo "one" | xargs sh -c "cd $0"
... exits silently

---

### Post by ooobooontooo on 2009-07-27
I think you're right.

I just ran a test in which I run a python script in the background which is in an infinite loop. And I try to "fg" it:
```
ps -u <user> | grep <pid> | fg
```
Same error as the cd thing:
```
xargs: fg: No such file or directory
```
So I'm guessing that the no such "file" or "directory" refers to the bin of "cd" or "fg"

A similar test with "echo" confirms this:
```
readlink Examples | xargs echo
/usr/share/example-content/
```
It didn't give the no such file error because although echo is a shell built-in, it still has a bin in the system (/bin/echo)

Thanks for your help.

---


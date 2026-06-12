---
title: "dir problem"
date: 2011-04-28
forum: General Help
---

### Post by ubu@ on 2011-04-28
hello world,

I think I have a problem. If my current directory (when using the shell) is* /home/* and I like to lunch a file *a.out*  that is in the* /home/folder1/ *,  I was able to lunch it like that:
```

ubu@ubuntu:/home$  /folder1/a.out
 
```
now I can't. I need to remove the first slash, and then it works:
 ```

ubu@ubuntu:/home$  folder1/a.out
 
```
Although the first is more convenience, how do I get the oldest one?

thanks, 
ubu@

---

### Post by hwttdz on 2011-04-28
The oldest one likely never worked.  Any address beginning with a / is treated as absolute, i.e. given in reference to / (which is sort of the base of the filesystem tree).  An address that omits the leading slash is treated as relative, so "cat Downloads/mystuff.txt" will work if I'm in my home (also referenced as ~, and generally living at /home/username/).  But won't work if I'm currently in Downloads (as then it will look for ~/Downloads/Downloads/mystuff.txt, which won't exist).  

There's the added complications of paths.  Any program in your path will run because the shell will find it.  So when I type "ls" it runs, not because there's an "ls" in the current directory, but because there's on in my path, which is really a set of directories to search for a command.  And if there's an ls in my current directory and I want to use that over the one living at /bin/ls, I have to either give the full path, as in /home/username/ls or I have to give a path relative where I stand (which is referenced as dot) ./ls (which says, the ls in the place where I am now).

so /folder1/a.out, will only work if the program actually lives in /folder1, i.e. it will not work if it lives in /home/username/folder1.

---

### Post by cipherboy_loc on 2011-04-28
On the first one, did you mean:

```

$ ./folder1/a.out

```with the leading '.'?

If you were in /home, and you launched /folder1/a.out, without the leading '.', that would imply you were launching a program that resides in /folder1/ (Where /folder1 resides in the Linux equivalent of C:\), not /home/folder1.


CIpherboy

---

### Post by ubu@ on 2011-04-28
> **cipherboy_loc said:**
> did you mean with the leading '.'?
CIpherboy
No.
> **hwttdz said:**
> The oldest one likely never worked.
hwttdz
Ok. Thanks. Apparently I was wrong. 

Half wrong. All the path examples I had, are starting from root. I think that this is make more sense. isnt?

---


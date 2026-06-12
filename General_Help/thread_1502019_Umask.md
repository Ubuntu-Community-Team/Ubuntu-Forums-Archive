---
title: "Umask"
date: 2010-06-05
forum: General Help
---

### Post by 2603Munna on 2010-06-05
Can anyone explain me the working of umask in the ubuntu terminal.........,I have learnt bt in the practice got tierd with that.......

What all I know is when anything is passd as an argument to umask it just subtracts its default value or the most recent set value from that and gives the resulting file permissions


I tries with this logic and found that it is not working properly

Is there any new it works?:P

---

### Post by BoneKracker on 2010-06-05
The umask command is one thing.  What a umask does is another.

The umask command will set or get the current umask value (the current default file creation mode mask).  That's all the actual 'umask' command itself does.

Now, what happens later as a result of the umask being set to a particular value is the "logic" you are probably talking about.  In general, when you see the term "mask" it means the thing functions to create sort of a shadow (like when you use a stencil (or "mask") to paint block letters on a sign).  In this case, the numbers in this mask (our "umask") are subtracted from the numbers meaning "full permissions" for either a directory or a file.  A mask of 022 does this:```

Full   Mask   Mode
777  - 022  = 755
666  - 022  = 644
```


Umask gives us a way of killing two birds with one stone -- setting both directory and file permissions to a default at once.  Instead of saying "755" and "644", we can just say "umask 022".

It works because the permissions for directories and files are related in such a way that this makes sense.  Look at the example above. By masking '2' for group, we are saying two things that tend to go together:

a) people belonging to the right group can list the contents of and enter this directory, but they can't change its contents (create, delete or rename files in it).
b) people belonging to the right group can read this file, but they can't change it (i.e., edit it, write to it), and they can't execute it.

Those two things tend to go together -- why would you let someone create new files in a directory but not let them edit them?  There are always exceptions, but umask is for setting broad defaults (e.g. for a user, for a program, for a directory).

As you can see, the higher the numbers in a umask, the more permissions get taken away (masked out) from any files and directories later created.  (Higher umask numbers results in lower permissions numbers because the umask numbers are subtracted away from the "full permissions" numbers.)

So you can't test the "logic" of what a umask does by using the umask command.  The umask command just sets or reads what the umask is.  To test what a umask does, you need to set it, create some files, and see what permissions they get.  I'll walk you through doing that:
```
~ $ umask
0022
```
I see that my umask is currently set to 0022 (you may have a different umask).
```
~ $ touch test
~ $ ls -l test
-rw-r--r-- 1 munna munna 0 Jun  5 01:06 test
```
I make a new file named "test", and then I look at it.  It's got 0644 permissions (rw-r--r--), which are what it should have with a umask of 0022.
```
~ $ umask 0077
~ $ umask
0077
```
I change my umask to a more paranoid 0077, and I check it to see that it actually got set.
```
~ $ touch test2
~ $ ls -l test2
-rw------- 1 munna munna 0 Jun  5 01:06 test2
```
I create another new file, look at it, and see that it's got 0600 permissions (rw-------), which is what it ought to have if created under a umask of 0077.
```
~ $ mkdir testdir
~ $ ls -l |grep testdir
drwx------  2 munna munna 4096 Jun  5 01:07 testdir
```
I create a new directory, look at it, and see that it has 0700 permissions, which is what it ought to have if created under a umask of 0077.

See, under umask 0077, a new file got mode 0600 and new directory got 0700.  That's what's supposed to happen.
```
~ $ umask 0022
~ $ mkdir testdir2
~ $ ls -l |grep testdir2
drwxr-xr-x  2 munna munna 4096 Jun  5 01:07 testdir2
```
I change the umask back to what it originally was, create another new directory, look at it, and see that it was created with mode 0755, which is what it should have if created under umask 0022.

See, under umask 0022, a new file got mode 0644 and new directory got 0755.  That's what's supposed to happen.

Note that the permissions are set according to the current umask at the time the file is created, and they do not change retroactively simply because you've changed the umask later.  Even though I changed the umask and then changed it back, both files I created, and both directories I created still have the permissions that were set at the time they were created:```

~ $ ls -ld test*
-rw-r--r-- 1 munna munna    0 Jun  5 01:06 test
-rw------- 1 munna munna    0 Jun  5 01:06 test2
drwx------ 2 munna munna 4096 Jun  5 01:07 testdir
drwxr-xr-x 2 munna munna 4096 Jun  5 01:07 testdir2
```

I hope that clears it up some for you. :)

---

### Post by Lucky. on 2010-06-05
Nice post BoneKracker!

---

### Post by BoneKracker on 2010-06-05
> **Lucky. said:**
> Nice post BoneKracker!
Thanks.  I remember trying to make sense of that when I first used linux.

---


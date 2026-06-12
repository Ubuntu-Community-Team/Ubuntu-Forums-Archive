---
title: "How to prevent opening a text file ?"
date: 2012-03-25
forum: General Help
---

### Post by Swiss_Knight on 2012-03-25
Hi everybody,

I just wanted to know if there is any way to prevent a text file to be opened (with any text editor) without any peculiar restriction for its _execution_. It's a script file I don't want users to edit the content by mistakes.
And I have an other file I don't want users to see what's in it, but they could run it.

Thanks.

---

### Post by idoitprone on 2012-03-25
> **Swiss_Knight said:**
> Hi everybody,

I just wanted to know if there is any way to prevent a text file to be opened (with any text editor) without any peculiar restriction for its _execution_. It's a script file I don't want users to edit the content by mistakes.
And I have an other file I don't want users to see what's in it, but they could run it.

Thanks.

only give it read and excute permissions?

do you want to restrict urself and others or groups?


everone can read and execute but nobody can write 
```
chmod 555 file 
```everyone can execute but nobody can read or write
```

chmod 111 file
```only owner can everything while everyone else can read
```
chmod 755 file
```only owner can do everything while rest can execute
```
chmod 711 file
```is this what you need?

but i dont think allowing other users unable to read it while being able to excute as a script will work
since scripts need read permissions, because it is the nature of scripts; they are interpreted
[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)

---

### Post by Swiss_Knight on 2012-03-26
Hello and thanks for your answer...

In fact I have several other questions :

1. I have given a try to a small script file I use in a program. It was "chmoded" to 111.
    It has not been executed within the program ! It apparently needs the "write" access to be executed and not only the "execute" access. Do you know why ?

2. If I, as root, give the "111" access to a file, what would happen if someone take this 
    file on an other machine ? Would it be "copyable" if access are set to 111 ? 
If yes, I presume that, after that, as root, the new user may be able to reset the access to 777...or whatever else. Or not ?

3. If such a file is meant to be set on several machine with a known root passwrd and 
    username by users, is there any other way to restrict access even to root on these machines ?


Thanks a lot ;)

---

### Post by TeoBigusGeekus on 2012-03-26
...or just
```
chmod -r /path/filename
```

---

### Post by idoitprone on 2012-03-26
> **Swiss_Knight said:**
> Hello and thanks for your answer...

In fact I have several other questions :

1. I have given a try to a small script file I use in a program. It was "chmoded" to 111.
    It has not been executed within the program ! It apparently needs the "write" access to be executed and not only the "execute" access. Do you know why ?

2. If I, as root, give the "111" access to a file, what would happen if someone take this 
    file on an other machine ? Would it be "copyable" if access are set to 111 ? 
If yes, I presume that, after that, as root, the new user may be able to reset the access to 777...or whatever else. Or not ?

3. If such a file is meant to be set on several machine with a known root passwrd and 
    username by users, is there any other way to restrict access even to root on these machines ?


Thanks a lot ;)

the script does not need write access to execute but both read and execute.
Scripts needs to be read before you execute

I will suggest of managing groups so everyone of excute and read the file but cannot edit it.

[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)

One question? Are you good at binary math?


If no then I will give a heads up on chmod command

In binary 
numbers are set up as
421 with the left as the power of 2 of the last one and you add all the slots to get your number
001 = 1
100 = 4
010 = 2
to get five
101 = 4+ 1 =5
110 = 4+2 =6

binary is simple
for permission and chmod 

there are three type of users to a file

owner,group,other

if you type ls -l you get the point
permission size? ownername groupname file name

i using the shorthand of chmod
4 for read 2 for write and 1 for execute
_100_ that read
010 to write
001 to execute

to add both read and write just must the proper position
110 read and write
in math 110 = 6
while
111 = 7 which is read write and execute

in the command ls -l
the permission is position which is the owner, group and other 
ugo

-rw-r--r-- that file owner has read and write while group and other only has read

```
chmod u+x file
``` your givin the owner execute permission
```
chmod g-x file
```your removing excute group permission of the file

---

### Post by Pand5461 on 2012-03-26
> **Swiss_Knight said:**
> Hello and thanks for your answer...

In fact I have several other questions :

1. I have given a try to a small script file I use in a program. It was "chmoded" to 111.
    It has not been executed within the program ! It apparently needs the "write" access to be executed and not only the "execute" access. Do you know why ?

2. If I, as root, give the "111" access to a file, what would happen if someone take this 
    file on an other machine ? Would it be "copyable" if access are set to 111 ? 
If yes, I presume that, after that, as root, the new user may be able to reset the access to 777...or whatever else. Or not ?

3. If such a file is meant to be set on several machine with a known root passwrd and 
    username by users, is there any other way to restrict access even to root on these machines ?


Thanks a lot ;)

1. As mentioned above, it does need "read" permission at least to be executed as it's executed by reading it line by line by the interpreter.

2. If a file cannot be read, it cannot be copied, that's simple. But the owner can change the permissions of their file to whatever they want. Root can do _everything_, whenever he has formal rights or not. His rights simply aren't checked.

3. You can't restrict root access. You can however encrypt your personal files if you don't want them to be read by anybody except yourself.

---

### Post by redmk2 on 2012-03-26
> **Swiss_Knight said:**
> Hello and thanks for your answer...

In fact I have several other questions :

1. I have given a try to a small script file I use in a program. It was "chmoded" to 111.
    It has not been executed within the program ! It apparently needs the "write" access to be executed and not only the "execute" access. Do you know why ?
Without seeing the script, one can only guess.  My guess is that the script sets variables (writes to itself).  The user that invokes the script is who sets the rights to the script.> 

2. If I, as root, give the "111" access to a file, what would happen if someone take this 
    file on an other machine ? Would it be "copyable" if access are set to 111 ? 
If yes, I presume that, after that, as root, the new user may be able to reset the access to 777...or whatever else. Or not ?
Of course it can be copied.  In addition the rights to the file do not follow the script when it is moved from machine to machine.  The rights are set on a per machine basis.  In fact the UID/GID numbers are what are used, not the user and group names.  If you are not the same UID on both machines it would appear to be owned bay a different name.> 

3. If such a file is meant to be set on several machine with a known root passwrd and 
    username by users, is there any other way to restrict access even to root on these machines ?
Thanks a lot ;)
Root always has access to the file.  On the other hand if you use a compiled language like C or C++ then the app becomes a binary blob.  Philosophically, this is frowned upon in the Debian/Ubuntu community.  Compiled applications without source code is the antithesis of Open Source (code) computing.

---


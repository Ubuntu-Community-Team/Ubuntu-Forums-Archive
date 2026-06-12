---
title: "Can't run a program I compiled"
date: 2012-08-28
forum: General Help
---

### Post by checoimg on 2012-08-28
I compiled a small program with the GCC and now I can't run it inside the terminal with "./hello" 
Says "bash: ./hello: Permission denied"

---

### Post by sam1948 on 2012-08-28
- did you compiled under root privileges? 
run:
```
ls -l ./your_file
```

and post the output

---

### Post by checoimg on 2012-08-28
> **sam1948 said:**
> - did you compiled under root privileges? 
run:
```
ls -l ./your_file
```

and post the output

-rw------- 1 user user 8405 Aug 28 09:12 ./hello2

---

### Post by checoimg on 2012-08-28
I'm using a 64bit Ubuntu maybe I'm compiling in 32bits

---

### Post by Lars Noodén on 2012-08-28
You need to [change the file permissions](https://help.ubuntu.com/community/FilePermissions) to make the file executable first,

```

chmod +x ./hello2

```

Then it will run.

```

./hello2

```

---

### Post by sam1948 on 2012-08-28
you don't have any permissions.
might be you used 
"sudo gcc" to compile or ran "su" before trying to compile.

where is your source code (which directory)?
might be you should move to your home dir (cd ~)
and work there.

if you have to run that file where it is , run:
```
chmod +x file_name
```
(of course replace file_name)

[for more info read some here]("http://www.zzee.com/solutions/linux-permissions.shtml")

---

### Post by checoimg on 2012-08-28
Is not working shall I use "sudo" with the command "chmod" ?

Thank you for your help.

---

### Post by gandaran on 2012-08-28
> **checoimg said:**
> Is not working shall I use "sudo" with the command "chmod" ?

Thank you for your help.
do it the easier way, right click file » properties » permissions tab » mark box allow execute file, then you can run the file.

---

### Post by checoimg on 2012-08-28
> **sam1948 said:**
> you don't have any permissions.
might be you used 
"sudo gcc" to compile or ran "su" before trying to compile.

where is your source code (which directory)?
might be you should move to your home dir (cd ~)
and work there.

if you have to run that file where it is , run:
```
chmod +x file_name
```
(of course replace file_name)

[for more info read some here]("http://www.zzee.com/solutions/linux-permissions.shtml")

I compiled in my home directory ( as you suggested ) and I was able to run it from there.

Thank you very much!

---

### Post by Lars Noodén on 2012-08-28
If you are the owner of the file, that is you created it, then you can use [chmod](http://manpages.ubuntu.com/manpages/precise/en/man1/chmod.1posix.html) yourself without using sudo.  If the file is owned by someone other than your own account, then you will have to precede it with sudo, but I think that is not the case.

---

### Post by checoimg on 2012-08-28
> **gandaran said:**
> do it the easier way, right click file » properties » permissions tab » mark box allow execute file, then you can run the file.

It un-checks after I check it.

---

### Post by checoimg on 2012-08-28
Now it runs but with an additional message.

"user@pc:~$ ./hello2
Hola a todos
Segmentation fault (core dumped)"

---

### Post by gandaran on 2012-08-28
> **checoimg said:**
> It un-checks after I check it.
the file was in your home directory or on some non linux file system?
shouldn't have this problem on home directory.

---

### Post by checoimg on 2012-08-28
> **gandaran said:**
> the file was in your home directory or on some non linux file system?
shouldn't have this problem on home directory.

Yes. It was on a external hard drive.

---

### Post by sam1948 on 2012-09-20
> **checoimg said:**
> Now it runs but with an additional message.

"user@pc:~$ ./hello2
Hola a todos
Segmentation fault (core dumped)"

hi,
mostly this means somewhere in your code there is an access to memory address which is not yours or that was released and later used.
it is a coding issue.

if it is not a long program you can upload it here.
in addition it is possible that you ignoring some warning during compile.

---

### Post by checoimg on 2012-09-22
> **sam1948 said:**
> hi,
mostly this means somewhere in your code there is an access to memory address which is not yours or that was released and later used.
it is a coding issue.

if it is not a long program you can upload it here.
in addition it is possible that you ignoring some warning during compile.

Here is the code:

-----------------------------------------------------------------
#include <stdio.h>

int main()

{
       printf("Hello world\n");
       end(0);
}
-----------------------------------------------------------------

---

### Post by MG&amp;TL on 2012-09-22
> **checoimg said:**
> Here is the code:

-----------------------------------------------------------------
#include <stdio.h>

int main()

{
       printf("Hello world\n");
       end(0);
}
-----------------------------------------------------------------

Why end()? I have no idea what that does...

```
return 0;
```

will work fine.

---

### Post by checoimg on 2012-09-22
> **MG&TL said:**
> Why end()? I have no idea what that does...

```
return 0;
```

will work fine.

That code was instructed in a PDF book I compiled the program with your option and it ran OK. :) Thank you for your help!

---


---
title: "Console programming"
date: 2010-05-24
forum: General Help
---

### Post by charkear on 2010-05-24
After upgrading to Lucid I can compile but not run binaries from the console.  

I have build-essentials installed.  

When I try to run a compiled program I get this error:
> bash: .: ./main: cannot execute binary file

---

### Post by charkear on 2010-05-25
Bump, this is royally annoying.  I feel that I am missing something simple.  I installed x64 first.  To try another clean install I put x32 Lucid on an old machine.  I encounter the same problem.

---

### Post by Miyavix3 on 2010-05-25
Have you tried this?
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

Navigate to the folder, then
./configure
make
make install

---

### Post by charkear on 2010-05-25
Thanks that is a good writeup on how to use make.

The problem happens even when trying to run a simple hello world program.  

compile
> 
gcc hello.c -o hello


execute
> 
$ . ./hello
bash: .: ./main: cannot execute binary file




```

#include <stdio.h>

int main(int argc, char **argv)
{
        printf("hello world\n");
        return 0;
}

```

---

### Post by charkear on 2010-05-25
Ok so I can run the binaries when I use sudo.

> 
$ sudo ./hello


This is frustrating because I am the owner of the file and the permissions are set at 755 or rwx r-x r-x.  So there should be no problem running it as a regular user.

---

### Post by charkear on 2010-05-25
I have a solution.
When I run a program like this:
> $ ./hello

There are no problems.

When I run a program like this:
> $ . ./hello

I get the error.

---


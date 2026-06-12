---
title: "stdio.h"
date: 2006-05-12
forum: General Help
---

### Post by bfarris on 2006-05-12
I am trying to compile the following simple program:

#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}


and I get this error:
hello.c:1:20: error:  stdio.h: No such file or directory
hello.c:3: error: ‘::main’ must return ‘int’
hello.c: In function ‘int main()’:
hello.c:5: error: ‘printf’ was not declared in this scope


I know you are probably thinking "he needs to apt-get install build-essential", but I have already done this, and it still does not work.

Any ideas?

---

### Post by jazzgossen on 2006-05-12
Try cstdio.h instead of stdio.h

Also, there seems to be a space between < and the file name. 

Try
#include <cstdio.h>

And, as the compiler says, main should return an int. So it's:
int main()
{
printf("\nHello World\n");
return 0;
}

---

### Post by bfarris on 2006-05-12
thanks, I'll try that when I get home.

I hope you are right and its something so simple.  If so, thats pretty lame on the part of the online tutorial I cut and pasted the code from.

---

### Post by jazzgossen on 2006-05-12
Actually, stdio.h should work, if you are using a plain C compiler. If you are using C++, then the name is cstdio.h instead. Which compiler are you using? Is it gcc?

---

### Post by bfarris on 2006-05-12
I am using gcc.

I haven't gotten home yet to try it, but I'm pretty sure you were right and the problem is simply the syntax of the program itself.  A little embarassed to have posted in a forum for help writing hello world.  

I tried to compile it the way it was written and got the same errors using gcc on my computer here at work, and it worked fine after making the changes.  As you said, stdio.h worked.

thanks again.

---

### Post by Slim Odds on 2006-05-12
[QUOTE=bfarris]A little embarassed to have posted in a forum for help writing hello world.[/QUOTE]

Thanks to the way the WWW works, you will **always** be the guy who had trouble compiling "hello world" :p 

The problem is definitely the <space> after the < and before the stdio.h

---

### Post by steve.horsley on 2006-05-12
I had that same problem yesterday. It turned out that I needed to install the **build-essential** package in addition to the gcc package. That fixed it. Hope it's that easy for you.

---

### Post by Slim Odds on 2006-05-12
[QUOTE=steve.horsley]I had that same problem yesterday. It turned out that I needed to install the **build-essential** package in addition to the gcc package. That fixed it. Hope it's that easy for you.[/QUOTE]

I guess you didn't read his entire post. He did install build-essential

The problem it that you can't have spaces between the < and the filename for includes.

---


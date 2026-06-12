---
title: "how to signal end of file in C"
date: 2011-08-16
forum: General Help
---

### Post by pb910 on 2011-08-16
I've read in multiple places that to signal the end of file in the bash command shell is Ctrl-d, but this does nothing at all for me.

here is my code:

```
#include <stdio.h>

main() {

    int c, i, nwhite, nother;
    int ndigit[10];

    nwhite = nother = 0;

    for (i=0; i<10; ++i)

    while ((c=getchar()) != EOF)
    if (c >= '0' && c <= '9')
        ++ndigit[c-'0'];
    else if (c == ' ' || c == '\n' || c == '\t')
        ++nwhite;
    else
        ++nother;

    printf("digits =");
    for (i=0; i<10; i++);
        printf(" %d,", ndigit[i]);
    printf("white space = %d, other = %d", nwhite, nother);

}

```

the IDE I am using is Code::Blocks, and here are my environment settings:

Shell to run commands in: /bin/bash -c
Terminal to launch console programs: xterm -T $TITLE -e

Does anyone have any idea what's wrong?

---

### Post by decoherence on 2011-08-16
I thought I knew what you were talking about but then you mentioned you were using an IDE so now I'm not sure.

Anyway, if you're writing to a file using bash, you need to hit enter before you hit Ctrl D. eg

```
cat > myfile.c
#include<stdio.h>

main()
{
    printf("Hello World");


}
^D
```

See I hit enter after that last curly brace. Ctrl D won't work otherwise. I'm not sure that's what you're getting at, though.

---

### Post by Jeff250 on 2011-08-16
You have nested loops.  Replace:
```
    for (i=0; i<10; ++i)

    while ((c=getchar()) != EOF)
```

with:

```

    for (i=0; i<10 && (c=getchar()) != EOF; ++i)
```

Note that you still have bugs, and this probably still isn't exactly what you want, but the program should at least terminate now.

---


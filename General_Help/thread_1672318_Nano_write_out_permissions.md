---
title: "Nano write out permissions"
date: 2011-01-20
forum: General Help
---

### Post by qazmonk on 2011-01-20
Im runnign Ubuntu 10.10 on a virtual box on my Mac running OS X 10.6.4. I'm new to ubuntu (and linux in general); I actually downloaded it today. While familiarizing myself I decided to try to write a simple C program (Hello World). I googled and found nano, opened it and wrote
```

#include <stdio.h>

int main()
{
[INDENT]printf("Hello World");[/INDENT]
[INDENT]return 0;[/INDENT]
}

```

I tried to write out my program but i got the error, Error writing helloWorld.c Permission denied.

I have no idea whats wrong

---

### Post by Foxheadz on 2011-01-20
try running ```
sudo nano
``` you might also want to just try getid

---

### Post by qazmonk on 2011-01-20
Oh sorry I just realized that I was in some strange directory, this whole non-visual file maneuvering is taking some getting used to

---


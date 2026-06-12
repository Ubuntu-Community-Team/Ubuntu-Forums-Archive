---
title: "Terminal Pause Command"
date: 2010-09-09
forum: General Help
---

### Post by diego_pmc on 2010-09-09
I can't seem to find the Unix command that pauses execution until the user presses a key (i.e. the equivalent of "pause" in DOS). 

Obviously, I need this for programming. I know about all the performance and security issues of system calls, so please don't recommend I used ncurses or some other library instead.

I only plan to use it in small programs that I write to test various algorithms and where perfection isn't needed.

---

### Post by slakkie on 2010-09-09
read :)



```

#!/usr/bin/env bash

echo "Press the [enter] key to continue"
read

echo "Thanks for pressing a key"

```

---

### Post by diego_pmc on 2010-09-09
[FONT=Arial Narrow]As in [/FONT][FONT=Arial Narrow][FONT=Lucida Console]system("read")[/FONT]? It doesn't work for me. When I use that command the Terminal prints "[/FONT][FONT=Arial Narrow][FONT=Lucida Console]read; 1; arg count[/FONT]"[/FONT] and doesn't do anything else. Here's the C++ code:
```
#include <iostream>
#include <cstdlib>
using namespace std;

int main()
{
    cout << "whatever" << endl;
    system("read");
}
```

---

### Post by slakkie on 2010-09-10
[http://www.google.nl/search?q=C%2B%2B+pause](http://www.google.nl/search?q=C%2B%2B+pause)

Best of luck.

---


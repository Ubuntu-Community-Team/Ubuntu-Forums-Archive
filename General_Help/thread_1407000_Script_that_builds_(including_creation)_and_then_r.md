---
title: "Script that builds (including creation) and then runs an executable"
date: 2010-02-14
forum: General Help
---

### Post by Abscissa on 2010-02-14
I'm trying to make a trivial shell script (as portable as possible) to build an executable and then run it. Basically something like this:

```

#!/bin/sh
# Assume that foo is a natively-compiled program,
# not a script or anything, and gets placed in './bin'
make foo
./bin/foo

```

But, when I try to run that, it complains that './bin/foo' doesn't exist and exits *before* it ever actually invokes 'make foo' which is exactly what *creates* './bin/foo' in the first place.

---

### Post by sandyd on 2010-02-14
> **Abscissa said:**
> I'm trying to make a trivial shell script (as portable as possible) to build an executable and then run it. Basically something like this:

```

#!/bin/sh
# Assume that foo is a natively-compiled program,
# not a script or anything, and gets placed in './bin'
**make**
./bin/foo

```

But, when I try to run that, it complains that './bin/foo' doesn't exist and exits *before* it ever actually invokes 'make foo' which is exactly what *creates* './bin/foo' in the first place.

fixed.

if that doesnt fix it, what exactly are you trying to build?

---

### Post by Abscissa on 2010-02-15
Ah forget it, the first command was erroring out before displaying anything. Tip: Avoid posting and shell-scripting when you haven't eaten anything!

---

### Post by rnerwein on 2010-02-15
> **Abscissa said:**
> I'm trying to make a trivial shell script (as portable as possible) to build an executable and then run it. Basically something like this:

```

#!/bin/sh
# Assume that foo is a natively-compiled program,
# not a script or anything, and gets placed in './bin'
make foo
./bin/foo

```But, when I try to run that, it complains that './bin/foo' doesn't exist and exits *before* it ever actually invokes 'make foo' which is exactly what *creates* './bin/foo' in the first place.

hi - just for fun
do you look for some thing like this

#include <stdio.h>
#include <stdlib.h>

#ifdef bla
#undef bla
#endif

#ifdef bla
# c compiler [COLOR=Blue]do not[/COLOR] see your coding
# put your shell script inside here
# [COLOR=Red]run: sh fun.c[/COLOR]
gcc fun.c -o fun
echo "your program is ready to run"
./fun
exit 0
#endif
main(int ac, char **av)
{
    fprintf(stderr,"here i am - have fun\n");
exit(0);
}

#ifdef " :-) "
#endif
ciao

---


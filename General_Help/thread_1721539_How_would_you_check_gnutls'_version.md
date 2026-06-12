---
title: "How would you check gnutls' version?"
date: 2011-04-04
forum: General Help
---

### Post by Rodayo on 2011-04-04
There's a function inside gnutls.h called "gnutls_check_version" so I wrote this script to check it:

```
#include <stdio.h>
#include "/usr/include/gnutls/gnutls.h"

int main()
{
    const char * version = gnutls_check_version(NULL);
    printf("Version: %s \n", version);
    return 0;
}
```

But I get a linking error("undefined reference to gnutls_check_version") during compile.

What do?

---


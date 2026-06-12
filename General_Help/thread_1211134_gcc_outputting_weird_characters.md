---
title: "gcc outputting weird characters"
date: 2009-07-12
forum: General Help
---

### Post by mike770780 on 2009-07-12
On a fresh install of the latest Ubuntu, gcc is giving me weird characters in the error messages. These are in place of where quotes would normally go.

For example

```

file test.c

int main() {
   not_a_function();
   return 0;
}

```

```

$gcc -Wall test.c
test.c: In function â&#8364;&#732;mainâ&#8364;&#732;:
test.c:4: warning: implicit declaration of function â&#8364;&#732;not_a_functionâ&#8364;&#732;
/tmp/ccevONb0.o: In function â&#8364;&#732;mainâ&#8364;&#732;:
test.c:(.text+0x12): undefined reference to â&#8364;&#732;not_a_functionâ&#8364;&#732;
collect2: ld returned 1 exit status


```

Notice around "main" and "not_a_function" ... how can I get rid of this?


Thanks

---


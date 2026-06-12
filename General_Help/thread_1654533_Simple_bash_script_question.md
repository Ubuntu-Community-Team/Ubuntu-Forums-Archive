---
title: "Simple bash script question"
date: 2010-12-28
forum: General Help
---

### Post by geo909 on 2010-12-28
Hello all,

When I execute the script below
```
#!/bin/bash

for i in {1..4}; do echo $i; done

```

I get the output:
```
{1..4}
```

However, if I execute the exact same line from the command line, I get the following:
```

jorge@flamingo:~/Scripts$ for i in {1..4}; do echo $i; done
1
2
3
4

```

Could somebody please explain to me why there is this difference? It's exactly the same line..

Many thanks in advance

---

### Post by geo909 on 2010-12-28
Ah, the man page for bash under "bracket expansion" is clear:

```
Brace expansion introduces a slight incompatibility with historical versions of
       sh.  sh does not treat opening or closing braces specially when they appear  as
       part  of  a  word,  and preserves them in the output.  Bash removes braces from
       words as a consequence of brace expansion.  For example, a word entered  to  sh
       as  file{1,2}  appears  identically  in the output.  The same word is output as
       file1 file2 after expansion by  bash.   If  strict  compatibility  with  sh  is
       desired,  start  bash with the +B option or disable brace expansion with the +B
       option to the set command (see SHELL BUILTIN COMMANDS below).
```

So, I guess this is solved..

---


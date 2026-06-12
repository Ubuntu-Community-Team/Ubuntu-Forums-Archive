---
title: "Bash case and goto?"
date: 2009-07-08
forum: General Help
---

### Post by Hawk__0 on 2009-07-08
Is it at all possible to make a menu that uses case, but when that is done, it goes back to the menu again? EG:

1. say hello!
2. say bye!

if the user enters 1, the script will use case to echo "hello!", but it needs to bring me back to the meu and allow me to entere a choice again.

Is this possible?

---

### Post by t4thfavor on 2009-07-10
Never use the word goto again 

[http://xkcd.com/292/](http://xkcd.com/292/)

[http://tldp.org/LDP/abs/html/testbranch.html](http://tldp.org/LDP/abs/html/testbranch.html)

case "$variable" in

 "$condition1" )
 command...
 ;;

 "$condition2" )
 command...
 ;;

---

### Post by geirha on 2009-07-10
You use an infinite loop for that.
```

#!/bin/bash
while true; do  # infinite loop
    echo "[1] hello"
    echo "[2] bye"
    echo "[q] quit"
    read -n1 -p "What will it be? " answer
    echo
    case $answer in
        1) echo "Hello!" ;;
        2) echo "Bye!" ;;
        q) break ;;         # Break out of the loop
        *) echo "Uh, what?" ;;
    esac
done

```

The builtin select command is also useful for making menus. Type ```
help select
``` to read about it.

---


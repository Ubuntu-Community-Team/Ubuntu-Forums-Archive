---
title: "Returning to a menu in bash script"
date: 2011-02-06
forum: General Help
---

### Post by whatthefunk on 2011-02-06
Another random bash question...

Im constructing a menu for a program using case.  I have all my normal input options mapped out but i want to have a * ) option so that if something else is inputed, it displays "Incorrect input" and then resumes the normal menu function.  How do I do this?  Ideally, I'd like it to display "Incorrect Input" and then accept more input for the menu.
Thanks

---

### Post by sisco311 on 2011-02-07
Put the case statement in an infinite loop. Something like:
```
#!/usr/bin/env bash

function1 ()
{
  whatever
}

function2 ()
{
  whatever
}

while true; do
  echo "Menu

  1 function1
  2 function2
  3 quit
"

  read -r c
  case $c in
    1)  function1;;
    2)  function2;;
    3)  exit 0;;
    *)  echo "err";;
  esac
done
```

---

### Post by whatthefunk on 2011-02-08
Cool.  Thats much easier than I thought.  Thanks!

---


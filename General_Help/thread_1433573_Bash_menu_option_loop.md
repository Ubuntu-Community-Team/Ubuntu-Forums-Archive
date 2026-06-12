---
title: "Bash menu option loop"
date: 2010-03-19
forum: General Help
---

### Post by dragos2 on 2010-03-19
Hi,

I am trying to make a bash menu that loops with options but it does not work as I want:
```

#!/bin/bash

clear # Clear the screen.

echo "           Menu List"
echo "          -----------"
echo "Choose one of the following options:" 
echo
echo "1) Action"
echo "2) Another option"
echo "3) Quit"
echo

while [ 1 ]
do
read option

case "$option" in

  "1" )
  echo
  echo "Doing things"
  ;;

  "2" )
  echo
  echo "Doing some stuff"
  ;;

  "3" )
  echo
  exit 0
  ;;

* )

   echo
   echo "Wrong selection."
  ;;

esac
done
#echo

#exit 0

```

Some help please :)

I want to make it read an option and do the action then return to menu.

---

### Post by cjhabs on 2010-03-19
I would place the menu code in a function and call that function whenever you need it.

function menu {
    menu code
}

# Call menu
menu

---

### Post by dragos2 on 2010-03-19
> **cjhabs said:**
> I would place the menu code in a function and call that function whenever you need it.

function menu {
    menu code
}

# Call menu
menu

Thanks :)

---


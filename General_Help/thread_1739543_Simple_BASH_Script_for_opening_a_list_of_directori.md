---
title: "Simple BASH Script for opening a list of directories"
date: 2011-04-26
forum: General Help
---

### Post by tg3793 on 2011-04-26
Would someone have a basic script that does the following already. I'm sure I can edit it on my own (even though I'm quite the beginner).

When I run the script I want it to give me a choice of several directories (which I will list) to choose from. It will then open them in Nautilus. Something like this:

Please choose from the following directories to open:
1) New Project
2) Old Projects
3) Client Archives
4) Tech Support

I already know how to open a directory in Nautilus. For example.
nautilus ~/my stuff/New Project

But it's the whole interactive thing I don't know how to do yet.

---

### Post by DaithiF on 2011-04-26
Hi, using **dialog**, something like:
```
#!/bin/bash
menu=( '1' 'New Projects'
        '2' 'Old Projects' 
        '3' 'etc...')
response=$(dialog --stdout --menu 'Choose a Directory:' 20 70 15 "${menu[@]}")
if [[ -n "$response" ]]; then
    item_index=$(( $response * 2 - 1 ))
    echo "You chose directory ${menu[$item_index]}"
fi

```

---

### Post by Crusty Old Fart on 2011-04-26
Using cases, it could be done like this:
```

#!/bin/bash
set -e

f_cases()
{
 clear
 echo "
 Please choose from the following directories to open:
 (or enter 0 to exit this script)

  0. Exit
  1. New Project
  2. Old Projects
  3. Client Archives
  4. Tech Support
"
  read -p " Enter selection [0-4] > " 

  case $REPLY in
    0) echo "  Program terminated."
       exit 0
       ;;  

    1) echo "  Opening New Project directory"
       nautilus ~/"my stuff/New Project"
       f_cases
       ;;  

    2) echo "  Opening Old Projects directory"
       nautilus ~/"my stuff/Old Projects"
       f_cases
       ;;  

    3) echo "  Opening Client Archives directory"
       nautilus ~/"my stuff/Client Archives"
       f_cases
       ;;  

    4) echo "  Opening Tech Support directory"
       nautilus ~/"my stuff/Tech Support"
       f_cases
       ;;  

    *) echo "  Invalid selection."
       read -p " Press Enter to continue."
       f_cases
       ;;  
esac
}
f_cases

```

---

### Post by tg3793 on 2011-04-29
DaithiF and Crusty thanks to both of you. 

@DaithiF ... That menu looks 'very' nice; but I don't know enough to edit it; don't know where to put the directories I want and I'm working on some Wordpress stuff and so don't have time to figure it out at the moment (but maybe later).

@Crusty ... Went ahead and used yours because it was easy enough to plug in the information I needed.

But again @DaithiF; that menu looks really nice. And if I knew what to do with it I would probably use that one.

Thanks to you both.

---


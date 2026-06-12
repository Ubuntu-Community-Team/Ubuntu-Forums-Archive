---
title: "How to create script that takes a variable"
date: 2010-08-05
forum: General Help
---

### Post by kainalu on 2010-08-05
Hey All,

Im trying to make a script that will take a variable from the command line, like so:

script -argument

where argument could be one of five different words, and the different words will lead to sections of script that execute different code. It is to switch out /etc/hosts files quickly.

for instance:

./hostfile -basic
would copy my day-to-day hostfile
./hostfile -kids
would copy my safe-browsing file
./hostfile -orig
would copy my original factory one back into place

and ./hostfile -oorig, ./hostfile -h or just ./hostfile, or any other non-listed variable would lead to a section of code explaining how to use the file.

This is the way i do it now,, but I prefer this argument method, as it works like a standard Terminal program.

```
#!/bin/bash

# Bash script to quickly choose my hosts file. Must execute switch with root priv.
# due to hosts being in /etc/
set -e # Stops on error
clear # Clear the screen.

echo "Please choose from the following host files"
echo 
echo "The main difference is how many and what type"
echo "of web sites are filtered."
echo "This file should be aliased in bashrc to the command"
echo "hostfile"
echo
echo "The more you filter, the slower the web gets"
echo
echo "[L]ight, for minimal filtering"
echo "[N]ormal, for moderate filtering"
echo "[C]razy, for the paranoid. (makes web not so fun...)"
echo "[P]orn, Like Crazy, but gets adult sites too (max protection)"
echo "[O]riginal, from factory. rarely needs using."
echo
echo "Please choose host file, you will be asked for your password"
read host
echo

case "$host" in
# Note variable is quoted.

  "L" | "l" )
  # Accept upper or lowercase input.
  echo "Copying LIGHT host file"
  sudo cp /etc/hosts.lght /etc/hosts
  ;;
# Note double semicolon to terminate each option.

  "N" | "n" )
  echo "Copying NORMAL host file"
  sudo cp /etc/hosts.nrml /etc/hosts
  ;;

  "C" | "c" )
  echo "Copying CRAZY host file"
  sudo cp /etc/hosts.crzy /etc/hosts
  ;;

  "P" | "p" )
  echo "Copying PORN host file"
  sudo cp /etc/hosts.porn /etc/hosts
  ;;

  "O" | "o" )
  echo "Copying ORIGINAL host file"
  sudo cp /etc/hosts.orig /etc/hosts
  ;;

esac

echo
echo
echo "Copying complete, as long as no errors reported"
sleep 3s

clear

exit 0
```

THANK YOU!!

---

### Post by kainalu on 2010-09-20
For anyone that actually cares, this works well for me.


```

case $@ in

variable1)
codecodecode

variable2)
codecodecode

esac

```
I solved my own thread! YAY!

---

